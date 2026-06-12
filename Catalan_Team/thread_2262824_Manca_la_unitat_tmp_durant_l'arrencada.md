---
title: "Manca la unitat /tmp durant l'arrencada"
date: 2015-01-27
forum: Catalan Team
---

### Post by Lalaith on 2015-01-27
Hola Ubuntaires!

he instal·lat Ubuntu de nou i de tant en quant, durant l'arrencada em surt el següent missatge d'error:

"La unitat de disc /tmp no està preparada o bé no està present".

Si segueixo les instruccions per reparar el problema "automàticament" (és a dir, sense reparació manual), es repara i arrenca Ubuntu normalment. No és un problema greu, però és molest...

Sabeu com el puc solucionar o per on tirar per cercar informació sobre el tema? Normalment cerco la informació del problema en anglès, però en aquest cas, al tenir el missatge d'error en català, no he trobat cap problema similar.

Gràcies!

---

### Post by wgarcia on 2015-01-28
Sembla un problema de tancament incorrecte del disc. Normalment amb una correcció d'errors del disc s'arregla. Prova de fer:
```
sudo touch /forcefsck
```
i reinicia.

Això forçarà una verificació dels discos en arrencar, a veure si ho arregla.

---

### Post by Lalaith on 2015-01-28
Pànic!
He intentat encendre l'ordinador per provar el que em vas escriure, i el grub no ha estat capaç d'arrencar el sistema. 

```

kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

```

He aplicat la solució proposada aquí:
[http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

Muntant el kernel 3.x.0-44-generic.
I he pogut arrencar Ubuntu, però han sortit un munt de problemes! No pot connectar-se al software centre per trobar actualitzacions, i han fallat 3 or 4 coses (una crec que era algo així com /usr/apt-cache i un parell deien algo dins de /usr/share/, però no recordo exactament què). 

Ho he embolicat tot una mica més, oi? :(

**Actualitzo:**
He fet un update-grub, he reiniciat l'ordinador, i ja no em surten errors. Esperaré si em surt un altre cop l'error del /tmp per executar la línia que em vas enviar.

Gràcies de nou.

---

### Post by wgarcia on 2015-01-29
M'alegro que s'hagi arreglat. Mira com ha quedat tot, quins nuclis tens instal·lats, i intenta actualitzar tot. També miraria si hi ha problemes d'espai al disc, per si un cas.

---

### Post by Lalaith on 2015-01-30
Hum, tens raó, la cosa no pinta gaire bé perquè quan intento veure els "Detalls" dins dels paràmetres del sistema (o la pestanya "Quant a aquest ordinador"), la finestra no s'obre. Tampoc puc accedir al Software Centre ni al "Programari i actualitzacions".
Espai al disc en tinc de sobres (recent instal·lat i sense haver desat pràcticament res). I només tinc 2 nuclis instal·lats.
El problema és que no m'entero de res, tampoc no sé per on tirar per buscar el problema i poder trobar-li una solució.

De moment em sembla que tiraré pel dret i m'apuntaré a un MOOC sobre Linux per començar a controlar què passa:
[https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-2#.VMvUgjWLe1E](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-2#.VMvUgjWLe1E)

Però qualsevol altre suggeriment serà molt benvingut :)

---

### Post by wgarcia on 2015-01-31
Obre una terminal, entra les següents línies:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Després de cadascuna d'aquestes línies fes "Intro". Comenta si surt algun missatge extrany.

---

### Post by Lalaith on 2015-02-04
he tornat a instal·lar de nou, i malgrat tot el codi 
```

sudo apt-get update

```

em mostra el següent error:
```

W: S'ha produït un error amb el GPG: http://de.archive.ubuntu.com trusty-updates Release: Les signatures següents són invàlides: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Això de signatures invàlides significa que no és capaç de descarregar-ho tot bé, oi?

Gràcies.

---

### Post by wgarcia on 2015-02-05
Sí, hi ha una signatura que no està ben definida.

Tens definit com a dipòsit de programari el dipòsit d'Alemanya, "de.archive.ubuntu.com". Prova de canviar de dipòsit (Paràmetres del sistema -> Programari i actualitzacions, i a la pestanya "Programari Ubuntu" a "baixa de:" escull per exemple "ftp.caliu.cat" o el que vulguis). Això molt sovint ho arregla, si no s'arregla s'ha de netejar la carpeta de baixades, ho podem provar a continuació si l'error persisteix.

---

### Post by Lalaith on 2015-02-05
ha funcionat!
Podria ser que el repositori alemany no tingués algun fitxer de traducció al català, i alguns altres paquets depenguessin d'aquest fitxer?

Gràcies de nou! :)

---

### Post by wgarcia on 2015-02-05
No, crec que es desincronitza la signatura que tens a l'ordinador i la que proveeix el dipòsit. Això de la signatura és una eina de seguretat perquè no es pugui baixar programari de fonts no autentificades.

---

### Post by Lalaith on 2015-02-08
La cosa no pinta gaire be, ara Unity no arrenca. Nomes veig el fons de pantalla i no s'obre cap finestra (per exemple si intento obrir una terminal amb Ctrl+Alt+T).
I l'arrencada es molt lenta. 
He apres a accedir al tty1, tty2, etc. Puc executar sudo apt-get update i sudo apt-get upgrade des d'alli, o es perillos?

(perdo pels accents, des del live USB nomes puc utilitzar un teclat en angles :()

---

### Post by wgarcia on 2015-02-09
No, no és perillós, i és el primer que pots provar. 

Si no ho arregla, té pinta de ser un problema de configuració gràfica. Des d'allà mateix dóna l'ordre:

```
lspci | grep -i "vga"
```

i amb això es podrà veure el model de targeta gràfica que tens. A partir d'aquí es pot veure si tens els controladors adequats per a aquesta targeta.

---

### Post by Lalaith on 2015-02-16
No vaig poder arribar a executar la línia de codi. no podia arrencar el sistema, es quedava penjat al initramfs, i no vaig poder trobar per internet com solucionar el problema .
Així que he tornat a instal.lar de nou... però em temo que hi ha un problema de base, perquè cada cop que reinstal.lo de zero continuo tenint els mateixos problemes. L'arrencada és molt lenta, el pc va lent i quan l'apago, algo va malament durant el procés d'apagada i em surten errors a l'arrencada.


Tinc una targeta nvidia, i he instal.lat els controladors necessaris per la targeta (els que estaven identificats com "comprovats"). Malgrat tot, quan he suspès l'ordinador no m'ha arrencat bé el Unity. He hagut d'anar al tty1 i trastejar una mica per allí, i he vist que intentava arrencar amb nouveau enlloc dels controladors de nvidia.  A la documentació d'Ubuntu hi ha una pàgina sobre la Nvidia i diu com arreglar aquest problema. Ho tinc pendent de fer.
Però mentre trastejava, m'he trobat les següents línies al syslog:

[drm] Wrong MCH_SSKPD value: 0x16040307
[drm] this can cause pipe underruns and display issues
[drm] Please upgrade your BIOS to fix this

Podria ser que aquest fos l'origen del mal funcionament?
he vist que és un procés delicat. Em recomanaries que el dugués a un professional, o em puc fiar del que trobi a la web del fabricant? 
No m'agrada la idea de dur-lo a una botiga a reparar-lo, perquè visc a Alemanya i tinc el sistema en català.

---

### Post by wgarcia on 2015-02-17
Sembla que sí que s'ha d'actualitzar el BIOS. En aquesta pàgina donen instruccions per a diversos models:

[https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

Suposo que si has reinstal·lat és perquè tens còpia de totes les dades. La veritat és que mai no m'he vist amb necessitat de fer-ho, així que no puc comentar-te gaire sobre això, potser algun altre que llegeixi pot donar alguna experiència.

---

### Post by Lalaith on 2015-02-28
Tot plegat es massa per a mi, el dure a arreglar i espero que li trobin el problema. 
Tanco el fil per no molestar mes.

Gracies de nou!!!

(perdo pels accents, torno a usar un teclat angles)

---

### Post by wgarcia on 2015-03-02
Tingues en compte també que de tant en tant celebrem trobades per instal·lar i arreglar problemes. Segons quines coses és difícil donar suport sense tenir l'ordinador endavant. 

Properament anunciarem la propera trobada, que se celebrarà a finals de maig a Terrassa.

---

