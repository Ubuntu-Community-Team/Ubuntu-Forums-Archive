---
title: "actualiztar Flash Player 10 al firefox"
date: 2009-10-19
forum: Catalan Team
---

### Post by diablessamariken on 2009-10-19
Hola a tots

fa estona que em barallo amb el terminal i l'arxiu d'instal·lació del Flash Player 10.0.32.18 que necessito per poder visualitzar algunes pàgines web.

Segons el tutorial d'instal·lació de la web de l'Adobe el procés a seguir és el següent: 

1- Descarregar l'arxiu, en aquest cas la versió en format tar.gz
2- Seguir les instruccions que us copio aquí sota.
[I][B]
Linux (x86)[/B]

Instrucciones de instalación para tar.gz

       1. Haga clic en el enlace de descarga de .tar.gz. Aparecerá un cuadro de diálogo en el que se solicita la ubicación en la que desea guardar el archivo.
       2. Guarde el archivo .tar.gz en el escritorio y espere a que el archivo se descargue por completo.
       3. Descomprima el archivo. Se creará un directorio con el nombre install_flash_player_10_linux.
       4. En el terminal, examine el directorio e introduzca ./flashplayer-installer para ejecutar el programa de instalación. Haga clic en Intro. El programa de instalación solicitará que se cierre el explorador.
       5. Cuando la instalación finalice, el plug-in se habrá instalado en el explorador Mozilla. Para realizar una comprobación, inicie Mozilla y consulte la información relativa a plug-ins en el menú Ayuda del explorador[/I].

Com podeu veure, el punt 3 diu que en descomprimir l'arxiu es crearà un directori. Però jo no em trobo amb això sinó que en descomprimir l'arxiu m'apareix directament l'arxiu següent:

libflashplayer.so

Què faig amb això? En cap moment em demana instal·lar res i el flashplayer no funciona... És ben estrany.

Alguna idea?

Moltes gràcies!

---

### Post by papapep on 2009-10-19
Fes a un terminal:

```
sudo mv libflashplayer.so /usr/lib/flashplugin-nonfree/
```

Això considerant que el directori per a la teva versió sigui aquest. Pensa que a l'ordinador que sóc ara té una 8.04.

Probablement et surti més a compte fer primer un:

```
sudo locate libflashplayer.so
```

i adaptar la primera ordre al directori que t'indiqui la segona.  ;)

---

### Post by diablessamariken on 2009-10-19
Fantàstic!

El directori era el que suggeries, Papapep perquè jo també sóc en un 8.04. I després d'introduir l'altra comanda i reiniciar el Firefox, ha reconegut la nova versió del Flash Player.

Gràcies doncs!!

---

