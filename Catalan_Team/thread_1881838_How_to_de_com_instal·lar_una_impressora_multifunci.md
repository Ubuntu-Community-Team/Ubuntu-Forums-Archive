---
title: "How to de com instal·lar una impressora multifunció de Brother en Ubuntu 64 bits"
date: 2011-11-16
forum: Catalan Team
---

### Post by akyra on 2011-11-16
Hola a tothom, he volgut fer un petit **"How to"** per poder instal·lar una impressora multifunció de Brother en Ubuntu 11.10 64 bits, ja que aquesta vegada m'ha portat uns quants problemes.

Jo tinc una impressora multifunció Brother MFC-820CW, la qual utilitza els drivers de la MFC-210C, però he intentat que valgui per qualsevol altre impressora.
Al utilitzar Ubuntu de 64 bits té uns passos i requeriments addicionals que són una mica embolicats de trobar i seguir en la pàgina de Brother.
El que he fet ha estat crear dos scripts, un per la part d&#8217;impressora i l&#8217;altre per la part d&#8217;Scanner, el fax no el faig servir i per això no l&#8217;he provat.
El que necessitem per utilitzar aquests scripts és baixar-nos els drivers corresponents per la nostra màquina i que trobarem a:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html")


Instal·lar part d'impressora, pasos a seguir:
[INDENT]1.- Descarregar el script &#8220;Instal_Impresora&#8221;  i donar permisos d&#8217;execució (botó dret->Propietats-> Permisos i marcar la casella de permetre executar l'arxiu com un programa).[/INDENT]

[INDENT]2.- Buscar i baixar els drivers d&#8217;Impressora del tipus &#8220;cupswrapper driver&#8221;. En el nostre cas seleccionem el paquet &#8220;.deb&#8221;.[/INDENT]
[INDENT]3.- Obri el terminal i fer : &#8220;sudo su&#8221;[/INDENT]
[INDENT]4.- A continuació anar a la carpeta de l&#8217;script de la impressora i executar-lo mitjançant:
 [INDENT]./Instal_impresora[/INDENT][/INDENT]
[INDENT]5.- Ens demanarà que introduïm la ruta complerta de la ubicació del fitxer del driver de la impressora.[/INDENT]
[INDENT]6.- Començarà la instal·lació.
Si no teniu instal·lats els paquets &#8220;csh&#8221; i i la llibreria &#8220;ia32-libs&#8221; demanarà si els volem instal·lar. Diem que sí i això es tot.[/INDENT]
[INDENT]7.- Una vegada acabada la instal·lació només haurem d&#8217;anar a &#8220;Impressió&#8221; i afegir una de nova, i posar les següents opcions:
[INDENT]Descripció: Brother MFC-820CW (o el que volgueu)
Location: Casa (o el que volgueu)
URI del dispositiu: lpd://la_Ip_de_la_impressora/BINARY_P1
Finalment només queda seleccionar el tamany de paper per defecte i si voleu canviar alguna altre opció.[/INDENT][/INDENT]


Scanner, passos a seguir  per instal·lar models que pertanyin a BRSCAN, BRSCAN2 o BRSCAN3 en xarxa (el BRSCAN4 tenen unes instruccions més especifiques i depen de models concrets, però si algú li interesa o podria fer):
[INDENT]1.- Descarregar el script &#8220;Instal_Scanner&#8221;  i donar permisos d&#8217;execució.[/INDENT]
[INDENT]2.- Buscar i baixar els drivers de l&#8217;Scanner . En el nostre cas seleccionem el paquet &#8220;.deb&#8221;.[/INDENT]
[INDENT]3.- Obri el terminal i fer : &#8220;sudo su&#8221;[/INDENT]
[INDENT]4.- A continuació anar a la carpeta de l&#8217;script del Scanner i executar-lo mitjançant:
 [INDENT]./Instal_Scanner[/INDENT][/INDENT]
[INDENT]5.- Ens demanarà el següent:
[INDENT]Que introduïm la ruta complerta de la ubicació del fitxer del driver del Scanner.
Entrar el nom que li volem donar a l'Scanner (per exemple: MFC820CW)
Entrar el nom del model de l'Scanner (per exemple : MFC-820CW)
Entrar l'adreça IP de l'Scanner
Entra el numero del tipus de brscan a que pertany (1 per brscan, 2 per brscan2 o 3 per brscan3).[/INDENT][/INDENT]
[INDENT]6.- Començarà la instal·lació i una vegada finalitzada ja es podria scanejar.[/INDENT]

Bé, espero que a algú li vagi bé, i si té algun problema ja m'ho farà saber.

Salutacions

---

### Post by Joan Marc on 2011-11-25
Gracies per l'aportació!
Personalment no tinc cap Brother, però sempre va bé tenir una guía per la gent que té problemes.

---

### Post by akyra on 2011-11-27
De res, a veure si a algú li serveix.

Adeu

---

