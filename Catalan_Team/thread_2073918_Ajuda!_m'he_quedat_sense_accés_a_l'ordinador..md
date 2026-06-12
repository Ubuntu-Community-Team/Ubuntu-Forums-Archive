---
title: "Ajuda! m'he quedat sense accés a l'ordinador."
date: 2012-10-20
forum: Catalan Team
---

### Post by jinglada on 2012-10-20
Ajuda! m'he quedat sense accés a l'ordinador!

En un portàtil Easy Note TM86 de Packard Bell, Intel Core i3-330M, Intel HD Graphics, 4GB, 15,6" 16:9 HD LED LCD, Windows 7, vaig instal·lar el 12.04 el qual va anul·lar l'accés a windows-7.

Intentant solucionar l'accés a windows m'he quedat sense accés a l'ordinador.

Necessitem el windows i intento reinstal·lar el disc de windows 7 i es queda bloquejat tant si li dic "reparar" com si li dic "instal·lar"

Hi ha alguna utilitat per formatejar i a partir d'aquí començar de nou?

Què és millor instal·lar primer el windows o l'ubuntu?

---

### Post by wgarcia on 2012-10-20
El millor és instal·lar Windows i després Linux, perquè Linux reconeix les particions creades per Windows però Windows, como no podia ser d'una altra manera pel seu caràcter de monopoli, sols es reconeix a sí mateix. Per tant si tens disc i has pagat la llicència per instal·lar Windows, pots intal·lar-lo i després instal·lar la distribució de Linux que vulguis a sobre que et quedarà la doble arrencada. 

Això sempre que no t'importi perdre les dades del disc, o tinguis còpia de seguretat per recuperar-les.

---

### Post by jinglada on 2012-10-20
> **wgarcia said:**
> El millor és instal·lar Windows i després Linux, perquè Linux reconeix les particions creades per Windows però Windows, como no podia ser d'una altra manera pel seu caràcter de monopoli, sols es reconeix a sí mateix. Per tant si tens disc i has pagat la llicència per instal·lar Windows, pots intal·lar-lo i després instal·lar la distribució de Linux que vulguis a sobre que et quedarà la doble arrencada. 

Això sempre que no t'importi perdre les dades del disc, o tinguis còpia de seguretat per recuperar-les.

El problema és que no m'accepta el disc de windows; es queda bloquejat tant si li dic "reparar" com si li dic "instal·lar".

Per això demanava si hi ha una eina a part per a formatejar el disc i llavors provar d'instal·lar windows.

¿Intento instal·lar Ubuntu utilitzant tot el disc i després intento instal·lar windows, encara que s'ho carregui tot, i finalment torno a instal·lar l'ubuntu?

---

### Post by Satboy on 2012-10-20
Hola,
 Has provat d'arreglar-ho amb el Super Grub Disk?

 [www.supergrubdisk.org](www.supergrubdisk.org)

 Dew! ;)

---

### Post by jinglada on 2012-10-20
> **Satboy said:**
> Hola,
 Has provat d'arreglar-ho amb el Super Grub Disk?

 [www.supergrubdisk.org](www.supergrubdisk.org)

 Dew! ;)
Gràcies Satboy!
He descarregat el Rescatux 0.30 i he aplicat el "Rescatux autodetect" i a continuació el "Restore Windows MBR (BETA)" i al rebootar ja m'ha sortit directament el missatge:
> No se puede iniciar windows. Es posible que un cambio de hardware o de sofware reciente sea la causa. para corregir el problema:

1.-inserte el disco de instalacion de windows y reinicie el equipo.
2.-elija la configuracion de idioma y despues haga clic en siguiente
3.-haga clic en reparar equipo

si no tiene este disco, pongase en contacto con el administrador del sistema o con el fabricante del equipo para obtener ayuda:

Estado: 0xc000000e
informacion: Error al seleccionar el arranque, no se puede tener acceso a un dispositivo requerido

He posat el disc de windows i al clicar "reparar equipo" es queda bloquejat. 

Llavors he fet el "Restore Grub" del disc del Rescatux  i al rebootar surt el missatge indicat de windows.

Veig que la segona opció del Rescatux 0.30 és la de "Super Grup2 Disk". Demà la provaré.

---

### Post by jinglada on 2012-10-21
El meu gendre necessitava el portàtil per connectar-se a internet. Se'm va ocòrrer d'instal·lar-li el 10.04 del qual tenia disc.

Em va crear el grub amb el 10.04, el 12.04 i el windows, però nomès em deixa accedir al 10.04

---------------------------------------------------------------
Ara estic passant el Super Grub2 del disc Rescatux, 
1) detecció dels S.O. : Tots 3, amb la curiositat que el w2 el reconeix com a vista.
2) detecció dels Grub2 (grub.cfg): Tots 2. He pogut entrar en el 12.04 només a partir del Grub del 10.04. Si intento entrar al w2 dóna l'error esmentat 0xc000000e
3) detecció dels Grub legacy (menu.lst): no en troba cap
4) detecció d'instal·lacions de Grub (even if mbr is overwriten): Tots 2 (core.img) i si els executo arranquen igual que el punt 2)
-------------------------------------------
Amb aquest següent no sé què fer
-------------------------------------------
5) Enable extra GRUB2 functionality ... amb els submenu de 'supports' següent:
- LVM 
- RAID
- PATA (to work around BIOS bugs/limitations)
- USB *experimental*
- Mount encript volumes (LUKS and geli)
- Enable serial terminal

---

### Post by jinglada on 2012-10-21
He probat **Rescatux 64 bits** i després de moltes línies amb 'Buffer I/O error on device  sr0' s'ha aturat fa més d'una hora amb una línia que diu:

**Kernel panic - not syncing: Attempted to kill init**

Què vol dir això?

---

### Post by jinglada on 2012-10-21
He reinstal · lat Ubuntu 12.04 usant tot el HD. Si la família no s'adapta reinstalaré W7 i provaré l'Ubuntu 10.04 a veure si no es càrrega l'accés al W7 com ha fet el 12.04. En instal · lar Ubuntu 12.04 usant tot el disc no hi ha hagut cap problema d'accés.

Gràcies a tots els que heu intentat ajudar-me.

---

### Post by Satboy on 2012-10-24
Hola,
 Jo ara he instal.lat el [Linux Mint Debian]("http://www.linuxmint.com/download_lmde.php") amb l'escriptori [Mate]("http://mate-desktop.org").
 També hi ha la versió [Linux Mint 13]("http://www.linuxmint.com/download.php") (Maya) amb escriptori **Mate**.
 La peculiaritat d'aquest escriptori és que és una evolució del Gnome 2.x.
 Em penso que l'Ubuntu no té aquest escriptori, però se li pot afegir.

 Dew! ;)

---

### Post by jinglada on 2012-10-24
> **Satboy said:**
> Hola,
 Jo ara he instal.lat el [Linux Mint Debian]("http://www.linuxmint.com/download_lmde.php") amb l'escriptori [Mate]("http://mate-desktop.org").
 També hi ha la versió [Linux Mint 13]("http://www.linuxmint.com/download.php") (Maya) amb escriptori **Mate**.
 La peculiaritat d'aquest escriptori és que és una evolució del Gnome 2.x.
 Em penso que l'Ubuntu no té aquest escriptori, però se li pot afegir.

 Dew! ;)

Gràcies, Satboy! Ho tindré en compte si no me'n surto.

---

### Post by Satboy on 2012-10-24
Hola,
 Te'l recomano de debò, va molt bé!

 Dew! ;)

---

