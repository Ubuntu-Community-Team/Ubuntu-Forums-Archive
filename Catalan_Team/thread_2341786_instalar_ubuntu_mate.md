---
title: "instalar ubuntu mate"
date: 2016-10-31
forum: Catalan Team
---

### Post by josep-maria on 2016-10-31
He volgut instalar l'ubuntu mate a un pc que té el windows 7. Amb un disc que té gravat l'ubuntu mate 5.10.
Faig que la bios vagi a llegir el disc dvd. Surt una finestra que diu: provar o instalar. Faig clic a instalar.

Demana 6,5 GB d'espai i accés a internet. 
Diu: no hi ha cap sistema operatiu a aquest pc. Què voleu fer? esborrar-ho tot, o alguna altra cosa.
(no és veritat que no hi hagi cap sistema oeratiu)
faig clic a "alguna altra cosa"

Surt una finestra de títol "tipus d'instalació".
Surt una finestreta per triar entre:
sda1(fat32)
sda2(unknown)
sda3(ntfs)
espai lliure

I una altra finestreta que diu: dispositiu on instalar el carregador, a triar entre:
dev/sda
dev/sda1
dev/sda3

Triant l'opció /dev/sda3 ntfs s'obre una finestra que diu: edita la partició (as superuser) i surten moltes opcions a triar. Trio la de àrea d'intercanvi (per no esborrar el windows 7).
Quan faig click a instalar surt una finestra que diu: No s'ha definit el sistema de fitxers arrel. Corretgiu això al des del menú de partició.

[ATTACH=CONFIG]271895[/ATTACH][ATTACH=CONFIG]271896[/ATTACH][ATTACH=CONFIG]271897[/ATTACH]

---

### Post by wgarcia on 2016-11-02
Segons el que mostres a les captures de pantalla, sembla que al disc /dev/sda que deu ser el disc dur intern a l'ordinador, sols hi ha instal·lat el Windows. Hi ha una partició (/dev/sda3) que pràcticament ocupa tot i està formatada a NTFS, el sistema de fitxers del Windows. A les particions /dev/sda1 i /dev/sda2, molt més petites, sembla haver-hi l'arrencada del Windows i la recuperació.

L'Ubuntu Mate està instal·lat a un disc extern?

---

### Post by josep-maria on 2016-11-02
El Mate 15.10 és a un disc dvd.

---

### Post by wgarcia on 2016-11-03
Però encara no tens instal·lat l'Ubuntu Mate a l'ordinador, oi?

Si és així primer hauries de reduir la mida de la partició "/dev/sda3" per fer espai per a instal·lar l'Ubuntu Mate. Per fer això, primer convé desfragmentar un parell de cops des del Windows aquesta partició. Òbviament també s'ha de fer còpia de seguretat i tenir preparat la recuperació del Windows per si alguna cosa va malament. Un cop desfragmentat el disc, l'aplicació "gparted" et permet reduir la mida d'aquesta partició. Iniciant des del dvd on tens l'ubuntu mate una sessió autonòma (és a dir sense intal·lar encara), obres aquest programa "gparted" i et mostrarà les particions (semblant a la primera captura de pantalla). Clicant amb el botó dret veuràs que hi ha una opció per reduir al mida de la partició. Per instal·lar l'Ubuntu Mate s'hauria de deixar almenys uns 50 gigues com per tenir espai suficient per al sistema operatiu i les dades que vulguis tenir. Un cop fet això, a la instal·lació hauries de veure aquest espai i poder escollir instal·lar l'Ubuntu Mate a aquest espai lliure.

---

### Post by josep-maria on 2016-11-05
I com es fa això de desfragmentar?

---

### Post by wgarcia on 2016-11-06
Això es una funció del Windows, ho tinc una mica oxidat, però penso que has d'anar al Control del sistema o com es digui, clicar sobre "Discos" i allà et surt una funció per defragmentar el disc dur.

---

### Post by josep-maria on 2016-11-07
Ja he defragmentat. També he creat una partició de 100 GB. L'ubuntu s'ha instalat, després de moltes peripècies. Però ara cada cop que engego el pc, va directament al windows, sense deixar triar. He mirat al boot menu que surt quan engegues el pc, però no he pogut arreglar-ho.

---

### Post by wgarcia on 2016-11-08
Sembla com si no s'hagués instal·lat correctament el grub, el sistema d'arrencada que dóna un menú. Entenc que pots entrar a ubuntu, oi, si no pots hauràs d'intentar arreglar-ho des d'un dvd o usb amb versió de prova. 

Per arregla això va bé usar una aplicació que es diu "boot-repair", i veure si ho arregla. Per instal·lar-lo, des d'una terminal fes:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

Després inicia-lo des del menú (suposo que quedarà a "Sistema" o quelcom semblant) i és força intuïtiu com funciona. També ho explica (en anglès) a la pàgina següent:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by josep-maria on 2016-11-08
Quan faig això, surt una finestra que diu:

The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. Açò activa aquesta funció. For example, use a live-USB of Boor-Repair-Disk-64bit ([www.sourceforge.net/q/boor-repair-cd](www.sourceforge.net/q/boor-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode.

No entenc res de res.

---

### Post by wgarcia on 2016-11-09
Diu que et baixis una imatge (iso) de l'enllaç que poses, l'escriguis a un USB o DVD, inicïis l'ordinador des d'aquest USB o DVD, i tornis a provar d'executar el boot-repair des d'aquesta sessió iniciada en "mode de prova".

---

### Post by josep-maria on 2016-11-19
La cosa es complica. Vegem, puc descarregar l'ubuntu-mate des de la web d'ubuntu cap al meu pc, però sense ficar-lo a cap disc tou, sinó ficant-lo directament al meu disc dur? I que quedi ja insta&#320;lat com si l'hagués ficat des d'un disc dvd?

---

### Post by wgarcia on 2016-11-20
No, això no ho pots fer, has de crear un mitjà arrencable (USB o DVD-ROM) i arrencar des d'aquest mitjà per fer la instal·lació.

Hi ha una manera de fer la instal·lació però requereix de coneixements força avançats, jo almenys mai no l'he provada. Consisteix en tenir la imatge arrencable al disc dur i modificar el grub perquè arrenqui des d'aquesta imatge. Ho he vist explicar, però com deia mai no he provat aquesta opció.

A les festes d'instal·lació també tenim una manera d'instal·lar sense USB o DVD, però fa servir un mirall d'instal·lacions que tenim configurat i sols es pot fer a les festes d'instal·lació. Instal·la des d'una xarxa que crea que el mirall.

---

### Post by josep-maria on 2016-11-21
Serà millor tornar a començar. He volgut comprar el disc de l'ubuntu mate a la web ubuntu-mate.org, però em pregunta si vull el de 32 bits o el de 64 bits. Quin cal agafar?

---

### Post by josep-maria on 2016-11-21
El processador és un i3.

---

### Post by wgarcia on 2016-11-22
El de 64 bits va bé, en tot cas no cal que el compris, també el pots gravar des de qualsevol sistema que et funcioni, fins i tot si no és Ubuntu. L'únic que cal és tenir cura que es gravi com a imatge i no com a disc de dades. Cal baixar-se dons el fitxer de la versió que vols instal·la (amb extensió "iso") i gravar-lo com imatge al DVD (o CD si cap).

Els ordinadors des de fa uns anys són capaços de córrer la versió de 64 bits, i ja s'ha convertit en la versió per defecte des de fa un parell d'anys.

---

### Post by josep-maria on 2016-12-26
Per fi, ja he pogut insta&#320;lar l'ubuntu mate 16.04, esborrant el mate 15.10 que hi havia ficat. Moltes gràcies.

---

