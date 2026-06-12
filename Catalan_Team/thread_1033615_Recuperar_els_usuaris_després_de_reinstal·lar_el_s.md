---
title: "Recuperar els usuaris després de reinstal·lar el sistema"
date: 2009-01-07
forum: Catalan Team
---

### Post by Jpedros2 on 2009-01-07
Aquests dies m'he trobat amb un problema respecte al qual he trobat poca documentació per internet: recuperar els usuaris després de reinstal·lar un sistema operatiu GNU/Linux. La informació que he trobat m'ha estat útil, però era molt fragmentària, per aquesta raó he decidit escriure aquestes notes, on recullc tota la informació més el resultat de les meves proves.
Com que no soc un usuari expert, algunes maneres de fer no seran molt elegants. Però a mi m'han resultat efectives.
Admetré gustós millores en el procediment.


**El punt de partida:**
En una partició els arxius de sistema: "/"
En una altra partició, els arxius d'usuari: "/home". En el meu cas, tenim tres usuaris diferents: "jesus", "usuari2", "usuari3".

Per tal de canviar de versió d'Ubuntu (he tornat a Hardy després d'un temps amb l'Intrèpid), he formatat la partició que conté els arxius de sistema, respectant la partició "home".

**El problema:**
Durant la nova instal·lació, quan em demana nom d'usuari, introdueixc el mateix nom (jesus) i la mateixa contrasenya que tenia abans, així el nou sistema recupera les meves dades d'usuari, però açò només es pot fer per a un usuari, per als altres dos la cosa es complica:
Si una vegada tenim instal·lat el nou sistema anem a "Administració > usuaris i grups" i intentem afegir els usuaris que ens falten, ens trobem amb que no podem, atès que ja existeix al directori "/home" una carpeta amb el mateix nom: Si volem recuperar l'usuari2 afegint-lo, ens diu que no pot ser, atès que ja existeix la carpeta "usuari2" al directori /home.
[B]
La solució:[/B]
Com que els meus coneixements de GNU/Linux són limitats, utilitze de vegades la consola i de vegades solucions gràfiques. No és el més elegant, però em funciona.
Des de la consola:
$ sudo nautilus
per tal d'obrir un nautilus amb privilegis de superusuari. Amb aquest nautilus canvie el nom de les carpetes d'usuari que necessite recuperar: "usuari2" passa a ser "usuari2_". El mateix amb la resta de carpetes d'usuari.
Fet açò ja podem anar a "Sistema > Administració > usuaris i grups" i crear nous usuaris amb el mateix nom que tenien abans: "usuari2", "usuari3"...
novament utilitzem nautilus amb privilegis de superusuari, esborrem les carpetes d'usuari que s'han creat en el directori "/home" al crear els usuaris i tornem a canviar el nom de les originals: Esborrem la carpeta "usuari2" recent creada i després canviem el nom a "usuari2_" (que conté les dades que volem recuperar), perquè es digui "usuari2". D'aquesta manera ja hem creat els mateixos usuaris que teníem, recuperant cadascú les seves dades.

Però encara no hem acabat!
Els arxius de cada usuari han de ser propietat d'ell mateix, i amb les operacions que hem fet amb nautilus hem canviat el propietari i no sé si els permisos.
Si oblidem aquesta darrera part ens trobarem problemes com ara els relacionats amb la impossibilitat del sistema de modificar l'arxiu .dmrc, on es guarden dades relatives a la configuració de cada usuari, així, hem de fer:

a) Canviar el propietari:
Des de la consola, situant-nos al directori /home (normalment serà suficient pujar un nivell en l'estructura de directoris, per exemple amb cd .. o bé fent cd /home)
/home$ sudo chown -R usuari2 /home/usuari2
Així aconseguim que tots els arxius de les carpetes i subcarpetes de l'usuari2 siguen propietat d'ell mateix.

b) Canviar els permisos:
Des de la consola, i també en el directori /home:
/home$ sudo chmod -R 755 /home/usuari2

(c) En algun lloc he llegit que els permisos de l'arxiu .dmrc de cada usuari haurien de ser "644", però a  mi m'ha funcionat perfectament seguint només les passes a) i b) indicades més amunt. 
Si volem canviar els permisos d'aquest arxiu (crec que no és necessari, atès que 755 representa una major capacitat d'accés que 644) haurem de fer:
/home$ sudo chmod 644 /home/usuari2/.dmrc
(així per a cada usuari).

---

### Post by papapep on 2009-01-07
Bona entrada, Jesús, gràcies per la feina.

Només un parell (de fet quatre) de comentaris ;-):


 a) no és aconsellable executar programes gràfics amb sudo des del terminal(és molt llarg d'explicar i si vols més informació ho pots trobar googlejant, i no passa amb tots els programes).
És millor prèmer "Alt+F2" i al diàleg que s'obre posar "gksudo nautilus". De no fer-ho així, es poden tenir problemes posteriors amb els permisos de certs fitxers importants del sistema gràfic.

 b) quan executes una ordre i dónes el camí absolut, p. ex. /home/elteusuari, no cal anar al directori inferior a fer-ho amb "cd". Tampoc fa cap mal, però és feina en va, ja que a la ordre ja li dónes tu el camí :-)

 c) quan fas el "sudo chown -R usuari2 /home/usuari2", o sigui, sempre que canvies un o diversos fitxers o directoris de propietari no està de més especificar també el grup. Si, de fet, no ha de canviar el grup, com a mínim ho comento a fi de que els usuaris menys experts tinguin present que el grup al que pertany el fitxer o directori també pot ser important (a vegades vital).
Per assignar-li també grup, només cal afegir ":elgrup" darrera el nou usuari propietari: 

"sudo chown -R usuari2:usuari2 /home/usuari2"

AFEGITÓ: per cert, el que comentes de que 755 és "millor", és el que dónes a entendre, que 644 per als permisos de .dmrc, no té per que ser així. Els permisos quants menys (sempre que funcioni com cal, clar) millor, i, evidentment, per temes de seguretat ;-) Ergo: si amb 644 funciona, no n'hi donis més (i això és pot aplicar a qualsevol altre supòsit).

---

### Post by Jpedros2 on 2009-01-15
Papapep, moltes gràcies pels teus aclariments.
Salutacions molt cordials-
--
Jesús

---

