---
title: "Actualització a 9.10. no arrenca"
date: 2009-11-01
forum: Catalan Team
---

### Post by pesolnegre on 2009-11-01
Hola a tothom.

Ahir vaig actualitzar a 9.10. en un principi sense problemes aparents. L'únic que al baixar la tapa (és un portàtil) la hibernació va fallar i no va tornar a arrencar.

Avui, fent una baixada de paquets des de synaptic, l'ordinador s'ha tornat a penjar, igual que ahir, quedant la pantalla congelada.

Al reiniciar l'ordinador m'ha aparegut la pantalla inicial per a seleccionar els usuaris (estava desactivada, només hi ha un únic usuari) on he d'introduir la contrassenya, me l'accepta i em retorna a la mateixa pantalla. La contrassenya és la correcta, doncs amb altres contrassenyes erronies em retorna a la mateixa pantalla però amb un missatge d'error.

He provat d'arrencar amb el recovery mode i em fa exactament el mateix.

He provat aquests tres comandaments:

usuari@nomordinador:~$ cat$HOME/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM trough im-switch for locale=ca_AD
Start IM trough /etc/X11/xinit/xinput.d/all_ALL linked to/etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open/ home/usuari/.profile

usuari@nomordinador:~$ df -h
S. fitxers             Mida    En ús  Lliure  %Ús   Muntat a 
/dev/sdal             36G     9,9G   24G   30%   /
udev                   497M    264K   497M  1%   /dev
none                   497M       0     497M  0%   /dev/shm
none                   497M    76K     497M  1%   /var/run
none                   497M       0     497M  0%   /var/lock
none                   497M       0     497M  0%   /lib/init/rw

usuari@nomordinador:~$ ls  -l  .ICEauthority

-rw-------1 usuari usuari 22275 2009-11-01 08:48 .ICEauthority

Faig servir un IBM R51

Algú sap com es pot arreglar això?? Merci a tots.

---

