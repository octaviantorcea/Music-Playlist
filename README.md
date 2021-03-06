# Tema 1 - Structuri de Date

Copyright 2020 Torcea Octavian

## Simularea unui playlist folosind o lista dublu inlantuita

* `playlist.c`: Lista dublu inlantuita va reprezenta playlistul, iar nodurile vor
    avea rolul de a stoca date despre melodiile din playlist.

    * `initList`: Initializeaza lista dublu inlantuita, dupa ce listei i s-a
    alocat memorie in main.

    * `freeList`: Elibereaza memoria tuturor nodurilor, iar la final elibereaza
    memoria alocata listei.

    * `cmdInterpretor`: Functia ia cate o linie din fisier si o imparte in
    comanda si numele melodiei (la comenzile ce necesita numele unei melodii),
    iar apoi concateneaza numele melodiei cu stringul "songs/" pentru a obtine
    calea necesara deschiderii fisierului cu informatii. Apeleaza apoi comanda
    primita anterior printr-o serie de if-uri. Daca se va solicita o alta
    comanda decat cele din cerinte se va afisa eroarea "Comanda gresita!". Daca
    se omite numele melodiei in cazul unei comenzi ce necesita acest lucru, se
    va afisa eroarea "Nu s-a specificat melodia." .

    * `main`: Doar se deschid si se inchid fisierele de input si output, se
    aloca memorie, se initializeaza lista si apoi se elibereza memoria alocata
    listei.


* `addFunctions.c`: Daca se doreste adaugarea unei melodii inexistente in folderul
    songs, se va afisa eroarea: "Nu s-a gasit melodia in folder." .

    * `copyInfo`: Functie care copiaza datele din fisier in nod.
    
    * `addFirst`: Adauga o melodie pe prima pozitie din playlist. Prima data se
    verifica daca playlistul este gol, deoarece este un caz special in care se
    vor modifica atat head-ul listei, cat si tail-ul si cursorul. Daca
    playlistul nu este gol, se verifica daca melodia ce trebuie adaugata exista
    deja in playlist. Daca exista si nu este unica din playlist (daca ar fi
    unica melodie din playlist, adaugand-o iar, practic nu s-ar schimba nimic),
    se va verifica daca pozitia melodiei deja existente in playlist coincide
    cu head-ul sau tail-ul listei, stergandu-se melodia si adaugandu-se apoi pe
    prima pozitie din playlist. Altfel, se verifica daca cursorul se afla pe
    melodie, caz in care cursorul se va muta pe pozitia viitoare (se evita
    mutarea cursorului pe pozitia anterioara, deoarece se verifica anterior
    daca melodia se afla la capatul listei), apoi se va adauga melodia la
    inceputul listei. Daca melodia nu a mai fost gasita in playlist, se va
    adauga la inceputul listei noua melodie si se va actualiza size-ul listei.

    * `addLast`: Aceleasi instructiuni ca la addFirst, cu exceptia ca noua
    melodie se va adauga la coada listei.

    * `addAfter`: Adauga o melodie dupa pozitia cursorului. Daca melodia
    ce se doreste adaugata coincide cu melodia care se afla la adresa
    cursorului, functia nu va efectua nicio schimbare. Se verifica daca melodia
    ce se va adauga exista deja in playlist. Daca exista, aceasta se va sterge.
    Se verifica daca cursorul coincide cu ultima melodie din playlist (caz
    special deoarece se va actualiza tail-ul listei).


* `deleteFunctions.c`: In toate functiile delete se va elibera memoria nodului ce
    se va sterge, astfel incat apelantul functiei sa nu fie nevoit sa elibereze
    el memoria. De asemenea, se ia in considerare la fiecare stergere pozitia
    cursorului, acesta mutandu-se conform cerintei.

    * `delOnlySong`: Functie care sterge melodia din playlist atunci cand
    playlistul are doar o singura melodie. Este un caz special deoarece trebuie
    actualizat la NULL atat head-ul listei, cat si tail-ul si cursorul.

    * `delFirst`: Se verifica prima data daca exista macar o melodie in
    playlist. In caz contrar, se va afisa un mesaj de eroare. Apoi se verifica
    daca pozitia cursorului coincide cu prima pozitie din lista, caz in care se
    va muta cursorul la melodia urmatoare. Se elimina primul nod din lista, se
    elibereaza memoria si se actualizeaza size-ul listei.

    * `delLast`: Aceleasi instructiuni ca la delFirst, doar ca se verifica daca
    pozitia cursorului coincide cu ultima pozitie din lista, caz in care se va
    muta cursorul la melodia anterioara si se va elimina ultimul nod din lista.

    * `delCurr`: Se verifica daca exista macar o melodie in playlist; daca nu,
    se va afisa un mesaj de eroare. Se verifica apoi daca pozitia cursorului
    coincide cu prima/ultima pozitie din playlist, caz in care se vor apela
    functiile delFirst sau delLast. Altfel, se efectueaza stergerea obisnuita,
    mutandu-se cursorul la pozitia urmatoare si actualizandu-se size-ul listei.

    * `delSong`: Daca se apeleaza aceasta functie cand playlistul este gol, se
    va afisa o eroare. Daca se doreste stergerea unei melodii ce nu se gaseste
    in folderul "songs", se va afisa eroarea "Nu s-a gasit melodia in folder" .
    Se verifica daca melodia ce se doreste sa fie stearsa se gaseste in lista.
    Se verifica apoi daca melodia gasita este pe primul sau ultimul loc in
    lista (pentru a se apela functiile delFirst sau delLast). Altfel, se sterge
    pur si simplu melodia din playlist. Daca nu s-a gasit melodia in playlist,
    se va afisa o eroare.


* `moveFunctions.c`: Functii ce efectueaza mutarea cursorului pe pozitia urmatoare
    sau pe cea anterioara. Daca se apeleaza o functie de move cand playlistul
    este gol, se va afisa eroarea "Error: no track playing." .

* `showFunctions.c`: Functiile de afisare.

    * `printInfo`: Afiseaza toate informatiile (titlu, artist, album si an)
    despre o singura melodie (nod) data ca parametru. 
    
