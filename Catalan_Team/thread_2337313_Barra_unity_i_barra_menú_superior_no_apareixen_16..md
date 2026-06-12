---
title: "Barra unity i barra menú superior no apareixen 16.04 LTS"
date: 2016-09-16
forum: Catalan Team
---

### Post by jinglada on 2016-09-16
Avui a l'engegar, la barra unity i el menú superior no apareixen en el 16.04 LTS.
Què faig?
Gràcies a la bestreta.

---

### Post by amarti-m on 2016-09-17
Bona nit!

Introdueix ```
Ctrl + Alt + F1
``` per anar a la tty1. Allà inicia sessió i executa:

```
sudo service lightdm restart
```

Reïnicia la màquina:

```
sudo reboot
```

Si amb això no s'arregla torna a la tty1 i fes:
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop 
sudo apt-get install unity

```

Salut!

---

### Post by jinglada on 2016-09-18
Bon dia i gràcies amarti-m:
"sudo service lightdm restart" no ha resolt el tema; he fet la resta i al final m'ha demanat que fes "sudo apt autoremove" i ho he fet però segueix tot igual.

PS: des del terminal he engegat el navegador per a contestar-te.

---

### Post by jinglada on 2016-09-18
Bon dia i gràcies amarti-m:
"sudo service lightdm restart" m'ha presentat la pantalla d'identificació d'ubuntu, he posat la contrasenya però no ha resolt el tema; he tornat a obrir el terminal i he fet "sudo reboot" i tot seguia igual; he fet la resta i al final m'ha demanat que fes "sudo apt autoremove" i ho he fet però segueix tot igual.

edito per copiar el terminal:
joan@joan-Aspire-E1-572:~$ sudo apt-get update
[sudo] contrasenya per a joan: 
Obj:1 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial InRelease
Obj:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Obj:3 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Obj:4 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-backports InRelease
S'està llegint la llista de paquets&#8230; Fet
joan@joan-Aspire-E1-572:~$ sudo apt-get install --reinstall ubuntu-desktop
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
0 actualitzats, 0 nous a insta&#320;lar, 1 reinsta&#320;lats, 0 a suprimir i 0 no actualitzats.
S'ha d'obtenir 0 B/3616 B d'arxius.
Després d'aquesta operació s'empraran 0 B d'espai en disc addicional.
(S'està llegint la base de dades&#8230; hi ha 404264 fitxers i directoris instal·lats actualment.)
S'està preparant per a desempaquetar &#8230;/ubuntu-desktop_1.361_amd64.deb&#8230;
S'està desempaquetant ubuntu-desktop (1.361) sobre (1.361)&#8230;
S'està configurant ubuntu-desktop (1.361)&#8230;
joan@joan-Aspire-E1-572:~$ sudo apt-get install unity
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
unity ya está en su versión más reciente (7.4.0+16.04.20160906-0ubuntu1).
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
joan@joan-Aspire-E1-572:~$ 

PS: des del terminal he engegat el navegador per a contestar-te.

---

### Post by amarti-m on 2016-09-18
[SIZE=2][FONT=arial]Bon dia!

Imagino que ets el mateix que ha enviat un correu-e per les llistes. Prova amb aquestes comandes:

```

sudo dconf reset -f /org/compiz
sudo setsid unity

```

I si no funcionen:

```
[SIZE=2][FONT=arial]sudo rm -rf ~/.config/compiz-l/compizconfig/*[/FONT][/SIZE]
```
[/FONT][/SIZE]
Després reinicia la màquina.

---

### Post by jinglada on 2016-09-18
He fet el següent, queda el terminal bloquejat, reinicio i tot igual; faig el següent i reinicio:

joan@joan-Aspire-E1-572:~$ sudo dconf reset -f /org/compiz
[sudo] contrasenya per a joan: 
joan@joan-Aspire-E1-572:~$ sudo setsid unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity

(process:10233): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but ECHILD was received by waitpid(). Most likely the process is ignoring SIGCHLD, or some other thread is invoking waitpid() with a nonpositive first argument; either behavior can break applications that use g_spawn_sync either directly or indirectly.

(process:10233): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=446c0440fb1efe1e036af61e539217a0 --binary-syntax --close-stderr': Child process killed by signal 63

(process:10233): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=446c0440fb1efe1e036af61e539217a0 --binary-syntax --close-stderr': Child process killed by signal 63

---

### Post by jinglada on 2016-09-18
Segueix tot igual :-(

---

### Post by jinglada on 2016-09-18
Veig que és un tema recurrent i recent.
Aquí: [https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444)
i ahir mateix també a: [https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444/comments/45](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444/comments/45)

Suposo que algú hi posarà remei.

Gràcies pels teus intents d'ajuda amarti-m

---

### Post by amarti-m on 2016-09-18
Perdona! Ara estava mirant i veig que m'he colat amb una comanda...

Prova aquesta:
```
sudo rm -rf ~/.config/compiz-1/compizconfig[SIZE=2][FONT=arial][/FONT][/SIZE]
```

Aniol

---

### Post by jinglada on 2016-09-18
> **amarti-m said:**
> Perdona! Ara estava mirant i veig que m'he colat amb una comanda...

Prova aquesta:
```
sudo rm -rf ~/.config/compiz-1/compizconfig[SIZE=2][FONT=arial][/FONT][/SIZE]
```

Aniol

No vols pas dir: sudo rm -rf ~/.config/compiz-1/compizconfig/* o sense /*?

---

### Post by jinglada on 2016-09-18
> **jinglada said:**
> No vols pas dir: sudo rm -rf ~/.config/compiz-1/compizconfig/* o sense /*?

He provat de les dues maneres i tot segueix igual.

Gràcies, Aniol, de totes maneres,
Joan

---

### Post by amarti-m on 2016-09-19
Al tenir l'opció -r és el mateix ja que és recursiu. Pensa que has de fer-ho des del tty1 i després reiniciar.

Aniol

---

### Post by wgarcia on 2016-09-19
Una altra cosa que pots fer és mirar quina targeta gràfica tens i quin controladors estàs usant. Per mirar quina targeta gràfica tens:

```
lspci | grep -i vga
```

des d'una terminal.

---

### Post by jinglada on 2016-09-19
> **wgarcia said:**
> Una altra cosa que pots fer és mirar quina targeta gràfica tens i quin controladors estàs usant. Per mirar quina targeta gràfica tens:

```
lspci | grep -i vga
```

des d'una terminal.

Gràcies wgarcia. Tinc:

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

Per saber els controladors com es pot fer des de la terminal? En no tenir ni unity no se m'acut com fer "Paràmetres del sistema" -> "Programari i actualitzacions" -> "Controladors addicionals".

---

### Post by jinglada on 2016-09-19
> **amarti-m said:**
> Al tenir l'opció -r és el mateix ja que és recursiu. Pensa que has de fer-ho des del tty1 i després reiniciar.

Aniol

Gràcies, Aniol.
Per si de cas ho he tornat a fer: 
Ctrl+Alt+F1
identificació
sudo rm -rf ~/.config/compiz-1/compizconfig
sudo reboot

... i segueix tot igual.

Joan

---

### Post by wgarcia on 2016-09-19
Amb la gràfica que tens hauria de funcionar sense problema. Pots entrar a Unity com a usuari "visitant" (guest)?

---

### Post by jinglada on 2016-09-19
> **wgarcia said:**
> Amb la gràfica que tens hauria de funcionar sense problema. Pots entrar a Unity com a usuari "visitant" (guest)?

Si, i tot funciona correcte!

---

### Post by wgarcia on 2016-09-19
Doncs es tracta d'alguna cosa que està malament en la teva carpeta d'inici. Pots provar de reiniciar unity, perdràs alguna personalització que hagis fet, però hauria de regenerar els fitxers de configuració i resoldre el problema. A veure si donant aquestes ordres (una darrera de l'altra) a la terminal ho arregla:

```

sudo apt-get install dconf-tools    
dconf reset -f /org/compiz/       
unity-reset
setsid unity

```
com em sembla ja et va recomanar l'amarti-m, i surt de la sessió i tornar a entrar amb 

```

sudo service lightdm restart

```

---

### Post by jinglada on 2016-09-19
Gràcies, wgarcia, el que em va dir amarti-m ja ho vaig fer i no va funcionar. 

Aquest migdia he fet el que m'ha dit en Pere (a la llista d'ubuntu surt com "Gmail t.collons a gmail.com "), que consisteix en reanomenar alguns subdirectoris ocults del home començant per .config, .gnome, .gnome2, .gnome_private2, .gconf, .gvfs, .local i en segona instància el .cache. Ho he fet i a la segona m'ha quasi funcionat; s'han perdut els historials dels navegadors, (excepte el del firefox) i de la barra llançadora.
He tornat el seu nom als 7 primers i la cosa funciona.

---

### Post by jinglada on 2016-09-19
Aquí [https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444/comments/48](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444/comments/48) ([https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444)) també els funciona.

Poso solved?

---

### Post by wgarcia on 2016-09-20
Sí, sisplau, seria útil que posis solved ja que has pogut solucionar el teu problema.

---

