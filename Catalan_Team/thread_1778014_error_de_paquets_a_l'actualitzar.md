---
title: "error de paquets a l'actualitzar"
date: 2011-06-08
forum: Catalan Team
---

### Post by ladisse on 2011-06-08
Bona tarda, des de que vaig instal·lar la versió 11.04 (Ubuntu Borges Jam) que tinc força problemes per les actualitzacions (encara que hi ha alguns dies que s'actualitza tot sense cap problema; deu dependre dels paquets x actualitzar). El tema està en que després de "llegir" el release, em surt el missatge següent: [IMG]http://file:///home/elena/Documents/Captura-3.png[/IMG] i llavors s'atura tot el procés. 


[ATTACH]194565[/ATTACH]

[ATTACH]194566[/ATTACH]
Per a més informació, puc dir que algun dia he provat de fer un terminal amb l'ordre següent. sudo apt-get update (i tampoc no ha acabat de fer bé la feina). Fa més temps, ja em vaig trobar amb el problema similar però era per un tema de connexió a internet -[vegeu el threat]("http://ubuntuforums.org/showthread.php?t=1756375")-. De moment, tampoc no he fet res més pq no sé trobar on és el problema. Moltes gràcies i salut per tots!

---

### Post by wgarcia on 2011-06-09
Respecte al primer missatge, Ubuntu sempre ho mostra quan es tracta de paquets proveïts externament, com ara els d'Adobe. Si el paquet s'ha baixat del Centre de Programari o del Gestor Synaptics tot i que surti aquest missatge no és perillós instal·lar-lo. 

En quant al segon missatge, sembla que tens habilitat un dipòsit de programari que està oferint un paquet que ja tens instal·lat, o està duplicat. Accedeix a la gestió de dipòsits a Paràmetres de sistema (Al menú de tancar) -> Sistema - Gestor de Paquets Synaptic, i aquí busca la pestanya "Paràmetres" i l'opció Dipòsits. A la pestanya "Altre programari" mira què tens marcat, i si pots desmarcar "Canonical Partners". Tanca el Synaptic, fes a una terminal "sudo apt-get update" i "sudo apt-get upgrade". Això ho hauria d'arreglar. 

Posteriorment pots tornar a habilitar "Canonical Partners" perquè continuï actualitzant els paquets d'aquest dipòsit.

---

### Post by ladisse on 2011-06-14
Gràcies. Després d'aplicar els canvis del Synaptic, al refrescar no em deixa (veure captura 7)[ATTACH]195068[/ATTACH] 

[ATTACH]195069[/ATTACH] 

Poso la seqüència de pantalles desp&#341;es d'haver tret Canonical i refrescar paquets. 
He obert un terminal amb les ordres update i aquests són els fallos que m'han sortit:
[ATTACH]195070[/ATTACH]

[ATTACH]195071[/ATTACH]

[ATTACH]195072[/ATTACH]

---

### Post by wgarcia on 2011-06-14
Pots adjuntar a un missatge el fitxer:

/etc/apt/sources.list

?

---

### Post by ladisse on 2011-06-14
Això és el que em respon la terminal:
[ATTACH]195086[/ATTACH]

---

### Post by Kette on 2011-06-14
> **ladisse said:**
> Això és el que em respon la terminal:

Amb el que has escrit al terminal no obtindràs cap resposta satisfactòria:
l'hi estas passant una ruta sense dir-li que ha de fer.
Per obtenir el contingut del fitxer que et demanen hauries d'escriure:
```
sudo cat /etc/apt/sources.list
```
i enganxar la sortida a un fitxer "txt". Per fer-ho més fàcil escriu al terminal:
```
sudo gedit /etc/apt/sources.list &
```
i s'obrirà en un editor de text gràfic. Ara resta copiar i enganxar.
Compta amb "apt", ho has escrit malament!
Salut

---

### Post by wgarcia on 2011-06-15
Jo el que deia era simplement clicar "Manage attachements" a dalt del tot, navegar fins a la carpeta /etc/apt i adjuntar el fitxer "list", però ara que veig kette té raó, no et deixaria perquè no és una de les extensions de fitxers permeses. 

Per tant és millor el que diu kette, obrir una terminal i entrar:

cat /etc/apt/sources.list > sources.txt

i adjuntar (amb el "Manage attachments") aquest últim fitxer.

---

### Post by ladisse on 2011-06-16
Volíeu dir això? És que últimament tinc la sensació que no entenc res de res.... Gràcies!

[ATTACH]195254[/ATTACH]

---

### Post by wgarcia on 2011-06-16
Sí, és això, es tracta del fitxer on s'estipulen els dipòsits de programari que va actualitzant el sistema, i a través del "Gestor de Paquets Synaptic" o del "Centre de Programari Ubuntu" es va canviant aquest fitxer si afegeixes o elimines un dipòsit.

Sembla que et falten les actualitzacions de seguretat. Jo faria el següent: obrir el "Centre de programari Ubuntu" i al menú "Edita" -> "Fonts de programari", a la pestanya "Programari Ubuntu" (la primera) ho marcaria tot menys "Codi font", l'última opció (si no coincideix algun d'aquest noms perdoneu però estic a un sistema amb els menús en anglès), i a la pestanya "Altre programari" ho desmarcaria tot, si encara tens alguna cosa marcada cosa que no sembla pel teu fitxer sources.list. A la pestanya "Actualitzacions" marcaria "Actualitzacions importants de seguretat" i "Actualitzacions recomanades" (també es convenient marcar el "backports", la quarta opció). També marcar "mirar actualitzacions" i aquí la tercera opció "Sols notifica sobre actualitzacions disponibles". Per tant en aquesta pestanya marcar les opcions 1, 2, 4 i 5 i dins de la 5 la tercera opció.

---

### Post by ladisse on 2011-06-16
ho he fet, i per una estona m'he cregut que funcionava.... :( després, al instal·lar els paquets baixats -que, sigui dit els ha baixat sense problemes, algo hem avançat-, doncs ha resultat que m'ha sortit un missatge dient que fallava la connexió a internet. Jo, innocent, he provat amb el "truco" del ping i resulta que internet i la connexió estan bé (100% dels paquets correctes). Algú em dóna una pista més? Moltes gràcies a tots, altra vegada.

---

### Post by wgarcia on 2011-06-16
Prova de canviar el servidor d'on et baixes les coses, ho pots fer obrint el Centre de programari Ubuntu, mirar el menú Edita -> Fonts de programari, i a la primera pestanya desplega "Baixa de", jo faig servir "ftp.caliu.cat" que és el de l'associació CALIU (Associació d'Usuaris i Usuàries de GNU/Linux en Llengua Catalana, [http://caliu.cat](http://caliu.cat)).

---

### Post by ladisse on 2011-06-16
Gràcies pel consell; ho acabo de fer, esperant que aquesta vegada anés bé... però em surt aquest missatge: "... requereix la instal·lació de paquets de fonts no autenticades..." i s'atura tot el procés. Realment, estic ben a punt de passar-hi el Live.... ànims!

---

### Post by wgarcia on 2011-06-16
Ara el problema que hi ha és que et falta baixar alguna clau. Hi ha un petit programa que et baixa les que et falten i que pots provar. Per fer-lo servir, com no està als dipòsits oficials, has d'entrar les següents instruccions successivament a una terminal (prement INTRO després de cada una d'elles):

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys
sudo launchpad-getkeys

---

### Post by ladisse on 2011-06-17
HOla WGarcia, aquest matí sembla que tampoc no vol funcionar tot i que les ordres que m'has dit semblava que sí que anaven fent.... al final, he anat al gestor d'actualitzacions i també ha fallat. Diu que no els baixa pq són de fonts no autenticades. :confused:

---

### Post by wgarcia on 2011-06-17
Has fet els passos que suggereixo al missatge #13?

---

### Post by ladisse on 2011-06-17
sí, els he seguit al peu de la lletra.

---

### Post by ladisse on 2011-06-17
enganxo l'últim terminal:
[ATTACH]195343[/ATTACH] a veure si hi sabeu trobar quin és el fallo, pq cada vegada me'n surt un o altre que no havia sortit fins ara. Insisteixo: moltes gràcies.

---

### Post by wgarcia on 2011-06-17
El sources.list es veu bé, quins missatges t'han sortit quan has entrat a la terminal les següents instruccions?:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys
sudo launchpad-getkeys 
```

---

### Post by ladisse on 2011-06-17
enganxo el document amb els terminals (la lletra en negre és per ressaltar les ordres, no ho he fet pas, en negreta ni en majúscules).[ATTACH]195380[/ATTACH] No sé si és millor fer-ho així o posar les diferents captures.... ja direu. Moltes gràcies.

---

### Post by wgarcia on 2011-06-18
Per enganxar aquí els resultats de comandes hi ha dues maneres. 

1) Clicar sobre el símbol # a l'editor del fòrum, que creat una etiqueta "CODE" (CODI). Dins de ```
[\CODE] que surt quan es clica es pot enganxar (després de copiar des de la terminal) el resultat de la comanda. 

2) Crear un fitxer amb extensió ".txt", per exemple "captura.txt". Per crear-lo hi ha diverses opcions. Una és córrer la comanda a la terminal, obrir "gedit", enganxar el que es vol capturar (després de copiar des de la terminal) i desar-lo amb el nom de fitxer que es vulgui (per exemple "captura.txt"). Després adjuntar aquest fitxer al fòrum (hi ha una opció per adjuntar quan crees un missatge). Una altra manera és córrer la instrucció a la terminal i dirigir el resultat a un fitxer, per exemple 
[CODE]sudo apt-get update > captura.txt
```

Tornant al teu problema, els captures que adjuntes de les comandes no semblen ser les que han de ser, són totes el fitxer "sources.list", no surt cap altra cosa a la terminal quan les vas donant?

---

### Post by ladisse on 2011-06-18
Crec que sí que hi enganxo tot el que surt. Gràcies per les dreceres de captures, m'aniran molt bé. Si ja et dic jo, que segur que no ho puc fer d'altra manera és pq el trasto no acaba de rutllar... quant no té un all, té una ceba.

---

### Post by ladisse on 2011-06-18
Bé, puc dir que em sembla que s'ha mig solucionat el tema. He anat a Synaptic --> Estat --> NO instal·lat residual i he provat d'eliminar el que hi havia, com que no he pogut, els he tornat a instal-lar. Llavors, he reiniciat i... des del gestor d'actualitzacions he provat d'actualitzar. Oh, sembla que baixa alguns paquets (suposo, per tant que també ha instalat les pertinents actualitzacions), però no ha fet ni cas dels de traducció. 
[ATTACH]195418[/ATTACH]

---

### Post by wgarcia on 2011-06-19
Em sembla que ja quasi ho tens arreglat. Mira si els passos que s'expliquen en aquest missatge:

[http://ubuntuforums.org/showpost.php?p=10826516&postcount=4](http://ubuntuforums.org/showpost.php?p=10826516&postcount=4)

t'ho acaben d'arreglar.

---

### Post by ladisse on 2011-06-19
Sembla que sí que ha funcionat, esperaré un parell o tres de dies per acabar d'assegurar-me que ha funcionat del tot. Realment, la que ha em sembla que ha tingut més èxit, és la última ordre: sudo apt-get dist-upgrade. Insisteixo a donar-te les gràcies.

---

### Post by wgarcia on 2011-06-19
Si realment ha funcionat recorda't de tornar i posar-li "Solved" a aquest intercanvi, pots fer-lo amb "Thread tools" un cop que obres el fil.

També pots tornar a habilitar els dipòsits "Partner" perquè es continuïn actualitzant els paquets associats a aquest dipòsit.

---

### Post by ladisse on 2011-06-19
Sí, ja tinc present lo de marcar el threat amb Solved... gràcies per recordar-m'ho.

---

### Post by ladisse on 2011-06-21
Bé, haig de dir que he pogut actualitzar només alguns paquets. Els que fallen (posi el servidor que posi -he provat de canviar-los per veure si hi havia el mateix error, i el resultat és que sí), són els que comencen per Translation. Penjo captura de pantalla, per si algú en sap treure l'entrellat.
[ATTACH]195671[/ATTACH]
moltes gràcies a tots.

---

### Post by wgarcia on 2011-06-22
Sembla que els paquets d'idioma encara no estan del tot bé instal·lats. Una manera de mirar-ho és la següent. Clica sobre el botó de tancar el sistema (l'última icona a la barra de dalt) i dins del menú que s'obre esculls "Paràmetres de sistema". Dins de la finestra que s'obre a la secció "Sistema" busques "Suport d'idioma" i clicant aquí mira a veure si tot es veu bé, o si et diu alguna cosa així com "El suport d'idioma no està del tot instal·lat", si aquest és el cas et donarà una opció per acabar-ho d'instal·lar.

---

### Post by ladisse on 2011-06-22
En principi tot això està de manera correcte. Em surt que el català/valencià està en primera lloc, i a continuació l'anglès; i la "descripció" de la moneda i de la data, a l'apartat de formats regionals, també és correcte. Potser canviant això puc arreglar els paquets de translation? tu ho creus? He provat en posar-ho a Andorra i Espanya i tinc els mateixos problemes.

---

### Post by ladisse on 2011-06-22
Després de penjar l'últim post, he provat d'actualitzar i semblava que tot anava bé. Quan ha arribat el paquet següent: **language-pack-es-base** i **[COLOR=Black]language-pack-gnome-aa[/COLOR]** ha sortit un missatge dient que la baixada dels paquets havia fallat i no ha continuat fent res més. Qualsevol "pista" sobre el tema, ho agraïré molt i molt, encara ho agraïré més si algú té la solució definitva. Moltes gràcies.

---

### Post by ladisse on 2011-06-22
Bé, estic molt però que molt satisfeta. Ara mateix acabo de poder actualitzar tot el programari!!! Inclòs els paquets de tranlation... encara que no sé quin és el problema que tenia (i que suposo que deu haver quedat per algun racó del pc) us explico com ho he pogut fer.
He anat a Synaptic --> Instal·lat (actualitzable) i he marcat els paquets per grups. S'han baixat la mar de bé; llavors veient que funcionava, he 'provat' si també em baixava i instal·lava sense problemes els de llenguatge. I sí, cal dir que ho ha fet! Ara, m'espero uns dies per saber si "l'apanyo" és per sempre o només m'ha funcionat ara; si realment és per sempre, ja posaré "Solved" al threat; sinó, continuaré demanant consell a tots vosaltres.

---

### Post by ladisse on 2011-06-27
Doncs no, els paquets que comencen per "Translation" (index, -ca, -Es principalment) continuen o bé inactius o no els baixa, o simplement els ignora. Algú em pot ajudar? Començo un altre fil amb un altre tema, que no sé si està relacionat amb tot això o no.

---

### Post by wgarcia on 2011-07-01
Potser fora bo que tornessis a adjuntar el resultat de 

sudo apt-get update

que obtens des d'una terminal, per poder veure com han quedat els dipòsits de programari.

---

### Post by ladisse on 2011-07-01
Poso el document del que surt al terminal; ho he fet així en aquest format, pq si faig el sudo cat /etc/apt/sources.list només enganxa les últimes línies. És molt llarg, però espero qeu hi podreu trobar l'error. Gràcies altra vegada.

[ATTACH]196482[/ATTACH]

---

### Post by wgarcia on 2011-07-01
Has de deshabilitar el dipòsit "PPA" que produeix l'error. Aquests són dipòsits que es poden crear els desenvolupadors per posar a disposició dels usuaris paquets que no estan en els dipòsits oficials, i s'han d'instal·lar amb precaució, perquè en no ser oficials no hi ha garantia del que fan (tot i que si algú/alguna vol fer alguna malifeta se li pot caure el pel). 

Per deshabilitar-ho obre el Centre de Programari Ubuntu, i al menú "Edita" busca "Fons de programari", i aquí la pestanya "Altre programari". A la llista que et surt busca algun dipòsit que comenci amb "ppa" i desmarca'l. També si veus algun altre que diu "translations" desmarca'l. 

Em sembla que això ja ho havies fet en alguna altra part d'aquest intercanvi, però per alguna raó encara els tens habilitats.

---

### Post by ladisse on 2011-07-02
Sí, ja ho he provat. He anat fent canvis d'això, així com d'altres opcions (repositoris, sobretot- entre el servidor principal, el caliu i el d'Espanya) però alhora d'actualitzar els paquets, sempre em dóna error. Crec que fóra millor reinstal·lar l'ubuntu de cap a peus. És que li van sortint cosetes que van fallant i n'estic ben tipa (no agafa dos ports USB, no llegeix disquets, no agafa la webcam.... en fi, que crec que entre avui i demà o poso tot a la bassa i començo de nou, a veure si va tot millor. MOltissimes gràcies, Wgarcia.

---

