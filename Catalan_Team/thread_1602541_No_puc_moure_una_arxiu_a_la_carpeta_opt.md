---
title: "No puc moure una arxiu a la carpeta /opt"
date: 2010-10-21
forum: Catalan Team
---

### Post by Pelacanyes on 2010-10-21
Bona tarda a tothom:
Estic intentant instal·lar Xampp. Resulta que al baixar el fitxer l'he guardat a la carpeta de baixades, però resulta que per instal·lar-ho l'arxiu hauria d'estar a la carpeta /opt.
La qüestió es que no em deixa moure l'arxiu en aquesta carpeta doncs sembla ser que no sóc "Propietari" del meu propi ordinador.:(
Us ho agrairia molt si em poguéssiu donar un cop de ma.
Gracies per endavant per la vostra ajuda.
Salutacions des de la Tarraco Imperial
Pelacanyes

---

### Post by lluisanunez on 2010-10-21
Ja poses "sudo" davant de la comanda?

---

### Post by Pelacanyes on 2010-10-21
Hola de nou:
El problema es que fins ara no havia hagut de fer res de tot això i sóc novell amb l'ubuntu, pel que no se per on començar.
> Ja poses "sudo" davant de la comanda? 	
Veient això que em dius, veig que no tinc n'idea. Es pot moure i com des del terminal? o s'ha de fer des de l'escriptori?. 
Socoooooooooorrrrrrrrrrrrrrrrrrrrrsssssssss 

Gracies de nou pel vostre ajut
Salutacions des de Tarraco
Pelacanyes

---

### Post by kukat on 2010-10-21
mira, pots fer-ho així

***sudo cp /ruta/carpeta /opt***

o bé:

***sudo nautilus***

i s'obri el "nautilus" que és l'aplicació que administra les carpetes i arxius, i el mous de la forma tradicional. si utilitzes kde on lloc de gnome:
***sudo konqueror***

---

### Post by wgarcia on 2010-10-22
Com bé diu el kukat, amb "sudo" pots fer **tot** al teu ordinador. No és que no siguis propietari, sinó que per precaució els usuaris normals no tenen accés a certes parts que podrien danyar el funcionament del sistema. També podria passar que com a usuari intentessis fer servir un programa tipus virus que pogués danyar el sistema. Per aquesta raó es diu que Linux és un sistema operatiu relativament segur, perquè tot i que ho intentessis, un virus sols danyaria el teu usuari, i no tot el sistema.

Ara bé, amb "sudo" sí que pots danyar tot el sistema. Així que millor saber el que s'està fent, i quant executes una comanda posant-li el "sudo" endavant, sí que tens accés a tot el sistema.

---

### Post by Pelacanyes on 2010-10-22
Moltes gracies a tots. Encara m'esti barallant però crec que m'ensortiré.
Veig que sóc un novell total i tinc molt per apendre. M'he descarregat un tutorial per apendre a fer funcionar ubuntu, el més bàsic. Si en sabeu d'algun tutorial i/o manual per "novatos" us agrairé qualsevol informació.
De nou moltes gracies a tots.
Salutacions des de la Tarraco Imperial
Pelacanyes

---

### Post by kukat on 2010-10-22
Aquí: [http://ubuntuforums.org/showthread.php?t=1597647](http://ubuntuforums.org/showthread.php?t=1597647)

Miquel Ubuntero va penjar una Guia de la darrera versió. 

Al Wiki de l'equip també hi ha molta informació. 

per exemple: [http://ajuda.ubuntu.cat/9.10/index.html](http://ajuda.ubuntu.cat/9.10/index.html)

---

### Post by Pelacanyes on 2010-10-22
Moltes gracies Kukat, de seguides em poso a llegir. No puc continuar així, sense saber ni canviar de directori  :confused: :mad::confused: :mad::confused:
Per altra banda, dir-vos que finalment he pogut instal·lar Xampp. He hagut de fer servir una combinació de Nautilus i Terminal, però finalment està instalat.
Pasos que he seguit:
1.- obrir nautilus
2.- moure l'arxiu comprimit **[B] xampp-linux-1.7.3a**.tar.gz   [/B]de la carpeta "Baixades"  al directori /opt
3.- Extreure l'arxiu dins el directori /opt
4.- Al terminal, entrar com root i executar "sudo /opt/lampp/lampp start"
5.- un cop ha arrencat xampp, comprobar al explorador l'adreça localhost
Be, ara miraré d'instalar el CMS i m'empaparé l'informació referent a l'Ubuntu.

Moltes gracies a tots per la vostra ajuda.

Salutacions des de la Tarraco Imperial

**[SIZE=4][COLOR=DarkGreen]Pelacanyes[/COLOR][/SIZE]**

---

