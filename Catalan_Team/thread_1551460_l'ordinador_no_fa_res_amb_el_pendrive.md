---
title: "l'ordinador no fa res amb el pendrive"
date: 2010-08-12
forum: Catalan Team
---

### Post by marmotona on 2010-08-12
Sense haver fet jo cap canvi voluntari, l'ordinador ha deixat d'interaccionar amb les memòries USB d'emmagatzament. L'opció d'esborrar-ne el contingut o d'enviar els fitxers a la paperera estan en gris i no es poden accionar. Tampoc no puc arrossegar-hi fitxers nous.

Què necessiteu saber per intentar ajudar-me a resoldre-ho?.

---

### Post by kimet on 2010-08-12
Hauries de mirar la carpeta on es munta el pendrive i mirar els permisos que te. Si el teu usuari no tingues permisos d'escriptura i/o execucio, canviar-los per ex. amb:
```
sudo chmod 755 /carpeta/on_es_l'usb
```

Abans li fas una ullada a ```
man chmod
``` i ```
man ls
```

També podria ser que no en fossis el propietari: ```
man chown
```

Salut

---

### Post by marmotona on 2010-08-12
> **kimet said:**
> Hauries de mirar la carpeta on es munta el pendrive i mirar els permisos que te. Si el teu usuari no tingues permisos d'escriptura i/o execucio, canviar-los per ex. amb:
```
sudo chmod 755 /carpeta/on_es_l'usb
```Abans li fas una ullada a ```
man chmod
``` i ```
man ls
```També podria ser que no en fossis el propietari: ```
man chown
```Salut

El veig a /media/usb0 però, quan faig 

```
sudo chmod 755 /media/usb0
```no em diu res. En el man chmod no hi entenc res.

Les propietats de la carpeta em diuen que el propietari té tots els drets i que és *root*, però jo no hi he fet cap canvi i sempre havia pogut fer tot el que volia amb els pendrives.

---

### Post by lpargemi on 2010-08-13
Hola,

El problema és aquest: que el propietari és root, i per tant ningú que no tingui privilegis de root pot accedir-hi. Sobre com has arribat fins aquí sense fer res de forma conscient: ni idea.

Per solucionar-ho: canvia'n el propietari i el grup.

Si fos jo (que el meu usuari es diu lluis) hauria de fer:
```
sudo chown lluis /media/usb0
``` per canviar el propietari i
```
sudo chgrp lluis /media/usb0
``` per canviar el grup.

No sé si així et quedarà de forma permanent, o si et caldrà fer alguna altra cosa.

Salut

Lluís

---

### Post by marmotona on 2010-08-13
Sembla que sí, que el camí que m'has indicat deu ser el correcte, però alguna cosa va malament en el meu ordinador perquè el terminal em respon:

> chown: s&#8217;està canviant el propietari de «/media/usb0»: Operation not permitted

i la mateixa resposta per a l'altra ordre.

T'ho agraeixo però potser hauré de reinstal·lar el SO quan aprengui com crear una partició comuna amb windows on guardar tots els fitxers.

---

