---
title: "La webcam no funciona (Skype)"
date: 2011-01-17
forum: Catalan Team
---

### Post by antoniu on 2011-01-17
Bé, estava configurant l'skype i al fer la prova de webcam no he tingut cap problema, però quan he començat una conversa aquesta no s'ha engegat i ara quan intento tornar a fer la prova tampoc funciona.

No sé quin model de webcam és; el meu portàtil és un acer i la té integrada.

P.s.: Acabo de provar d'entrar a una pàgina d'aquestes que té xat amb vídeo i surt com si no tingués webcam.

---

### Post by wgarcia on 2011-01-17
Mira si el suggeriment donat en aquest comentari:

[http://ubuntuforums.org/showpost.php?p=9969459&postcount=3](http://ubuntuforums.org/showpost.php?p=9969459&postcount=3)

et serveix.

---

### Post by antoniu on 2011-01-17
Gràcies, però no em funciona. Sobre l'skype però la càmera continua sense funcionar.

---

### Post by wgarcia on 2011-01-18
Et funciona en altres aplicacions, per exemple amb "cheese"?

---

### Post by antoniu on 2011-01-18
Ho acabo de provar i tampoc. O sigui m'apareix que tinc càmera (Camera (/dev/video0)) però no s'encén.

---

### Post by wgarcia on 2011-01-18
Hauries de dir quina càmera és. Per fer això desendolla-la i torna-la a endollar, i enganxa les 2 o 3 últimes línies que obtens si obres una terminal i escrius

dmesg

---

### Post by antoniu on 2011-01-18
No ho puc fer perquè la càmera està integrada.

---

### Post by wgarcia on 2011-01-18
Sí, perdona, ja ho havies dit. Llavors pots reiniciar l'ordinador, i en quant accedeixes al teu escriptori obres una terminal i entres

dmesg | grep -i video

---

### Post by wgarcia on 2011-01-18
Sí, perdona, ja ho havies dit. Llavors pots reiniciar l'ordinador, i en quant accedeixes al teu escriptori obres una terminal i entres

dmesg | grep -i video

---

### Post by wgarcia on 2011-01-18
Sí, perdona, ja ho havies dit. Llavors pots reiniciar l'ordinador, i en quant accedeixes al teu escriptori obres una terminal i entres

dmesg | grep -i video

(Vaja, el navegador quedava com penjat i ara resulta que ha enviat la mateixa contestació tres cops!)

---

### Post by antoniu on 2011-01-18
Crec que no diu el model..em surt això

[    0.838992] pci 0000:01:00.0: Boot video device
[   18.877294] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input4
[   18.877359] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.099303] Linux video capture interface: v2.00
[   19.124403] gspca: video0 created

---

### Post by kimet on 2011-01-18
Encara que sigui una camara integrada, es frequent que estigui conectada per el bus usb internament, amb lsusb sabràs quina es descartant el lector de targetes i els hub.
També hi han programes per donar informació del hardware, hardinfo,hwinfo...

Salud.

---

### Post by wgarcia on 2011-01-19
No em queda clar si reconeix la càmera. 

Una altra cosa que es pot fer és obrir una terminal i entrar:

gstreamer-properties

A la finestra que s'obre, clicar la pestanya "Vídeo" i a l'entrada dispositiu veure si surt algun dispositiu. Aquí també es poden fer proves de la càmera.

---

### Post by antoniu on 2011-01-19
He fet això que m'heu dit i la càmera és una Logitech, Inc. OrbiCam
Pel què fa a l'altre pas he pogut provar la càmera i m'ha funcionat i de fet he obert l'skype i al fer la prova també ha funcionat.
Ara em falta provar-ho en una conversa, que és quan va deixar de funcionar l'altre cop, a veure si realment funciona o no.

---

