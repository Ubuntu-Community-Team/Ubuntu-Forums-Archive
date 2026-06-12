---
title: "No em reconeix la webcam integrada ni el microfon"
date: 2010-07-08
forum: Catalan Team
---

### Post by karto_on on 2010-07-08
Hola a tots, 

soc un novato, però amb ganes d'apendre...
Tinc un VAIO VGN-FZ31E que te la webcam integrada i un micro. El problema és que no me'ls detecta.
Quina informació us hauria de facilitar i com la trec?!
 
Moltes gràcies i endavant!

P.E: Ens veiem el 10 a la mani!! :p

---

### Post by wgarcia on 2010-07-09
Quines proves has fet per veure que no et reconeix la webcam i el micro?

---

### Post by karto_on on 2010-07-09
Hola, 

Tot ha vingut quan he volgut fer una video-conferencia amb el messenger.
Després m'he baixat un programa que es diu Camorama, per veure si era problema del messenger o que, però aquest programa tampoc em reconeixia la camera, deia que no estava conectada.
I pel so, he provat també amb el programa d'enregistrament de so i efectivament, no grava re.

Salut!

---

### Post by wgarcia on 2010-07-09
El camorama té un problema perquè depèn d'unes llibreries que no s'han adaptat el nou sistema de vídeo de linux. 

Prova d'instal·lar una aplicació que es diu "xawtv" i mira si aquesta pot detectar la teva càmara. 

Per instal·lar "xawtv" pots fer servir el Gestor de Paquets Synaptic o des d'una terminal donar la instrucció següent:


sudo apt-get install xawtv

Quant al micròfon fes un clic amb el botó esquerra del ratolí a l'altaveu que surt a la barra de dalt, i clica "preferències de so" i busca "input", mira què surt i si té el volum donat.

---

### Post by karto_on on 2010-07-10
moltes gràcies, 
efectivament ho del micro tenies rao... el volum estava al mínim!
pero el XawTv no se'm carrega, el tinc instal·lat, però quan clicko per arrancar no fa re...com si no hagués clickat en lloc ni fa l'intent de carregar re, ni re de re...
que pot ser?

---

### Post by wgarcia on 2010-07-10
Intenta obrir-lo des de la línea de comandes, a veure què passa. Obre una terminal i entra "xawtv" i prem into.

---

### Post by karto_on on 2010-07-10
em dona aquest error:

kartoon@kartoon-laptop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-23-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

que vol dir?

---

### Post by wgarcia on 2010-07-10
Vol dir que no troba el vídeo. Prova de fer:

ls /dev/video*

a veure si surt alguna cosa.

---

### Post by karto_on on 2010-07-11
Efectivament no existeix aquesta carpeta:

kartoon@kartoon-laptop:~$ ls /dev/video*
ls: no s’ha pogut accedir a /dev/video*: No such file or directory

S'havia d'haver creat al instalat el xawtv? o és una carpeta del sistema?

---

### Post by wgarcia on 2010-07-12
Aquestes no són carpetes normals sinó virtuals que es creen per gestionar els diversos dispositius usb i d'altres tipus connectats al sistema. El fet que no existeixi aquesta carpeta vol dir com tu dius que no s'està detectant correctament la webcam integrada. Per confirmar això reinicia l'ordinador, i de seguida des d'una terminal entra la instrucció següent:

dmesg | grep -i video

i engantxa aquí el que surti.

---

### Post by karto_on on 2010-07-12
Hola, 

kartoon@kartoon-laptop:~$ dmesg | grep -i video
[    0.832622] pci 0000:01:00.0: Boot video device
[   24.857224] Linux video capture interface: v2.00
[   25.172772] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[   25.173098] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   25.173346] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   25.173434] uvcvideo: Failed to initialize the device (-5).
[   25.173587] usbcore: registered new interface driver uvcvideo
[   25.175421] USB Video Class driver (v0.1.0)
kartoon@kartoon-laptop:~$ 

Necesito uns drivers?

---

### Post by wgarcia on 2010-07-12
El problema és que registra el mòdul uvcvideo i es veu que aquest mòdul no li va bé a la teva webcam. Està explicat al següent blog:

[http://www.nosinmiubuntu.com/2010/04/webcam-r5u870-de-vaio-fz21s-en-lucid.html](http://www.nosinmiubuntu.com/2010/04/webcam-r5u870-de-vaio-fz21s-en-lucid.html)

Com veuràs també dóna instruccions precises sobre com arreglar-ho. Potser l'únic que no està documentat és quan diu de descomprimir el fitxer: 
r5u870_k2.6.30_i386.tar.bz2

que és el que et baixes del primer enllaç.

Per descomprimir-ho ves on hagis baixat el fitxer i fes:
tar xvjf r5u870_k2.6.30_i386.tar.bz2


Mira també abans de començar si tens instal·lat :
sudo apt-get install build-essential

Després segueix pas per pas el que t'expliquen i a veure si comença a funcionar la webcam.

---

### Post by karto_on on 2010-07-15
Olé!!! 

Moltissimes gracies wgarcia!!! ja em funciona tot!!! ets un crack!
Hi ha alguna manera de donar-te punts o alguna cosa? perquè t'ho has currat un ou!

Moltes gràcies, de veritat!

---

### Post by karto_on on 2010-07-15
Olé!!! 

Moltissimes gracies wgarcia!!! ja em funciona tot!!! ets un crack!
Hi ha alguna manera de donar-te punts o alguna cosa? perquè t'ho has currat un ou!

Moltes gràcies, de veritat!

P.E. com es tanca el post?

---

### Post by wgarcia on 2010-07-16
M'alegro que ja et funcioni. Per tancar-ho simplement amb el fil obert tens un menú a dalt on pots canviar el tema del fil posant-li "Solved" endavant, com altres fils que veus en aquest fòrum.

---

### Post by Catalanoic on 2010-09-26
a mi també m'ha funcionat amb un ordinador igual, gràcies!

---

### Post by 19preguntes on 2010-10-16
Tenia el mateix problema amb un VAIO PCG-4N2M (que no tinc ni idea si és gaire diferent del del karto_on). He seguit les explicacions de wgarcia i funciona perfecte.

Respecte el micro, però, un detall: en el meu cas no es tractava d'ajustar el volum (que no estava a 0). He hagut de seleccionar "Microphone 2" perquè funcionés (i us asseguro que no tinc dos micros...)

Gràcies wgarcia!!!

Salut!

---

### Post by Lomarc on 2011-03-30
> **wgarcia said:**
> M'alegro que ja et funcioni. Per tancar-ho simplement amb el fil obert tens un menú a dalt on pots canviar el tema del fil posant-li "Solved" endavant, com altres fils que veus en aquest fòrum.

Hola wgacia, tinc un problem semblan al company.
El micro, OK
Però la webcam no hi ha manera (Utilitzo Skype)
He provat de fer això que expliqueu per aquí i el terminal em diu això;
lomarc@lomarcportatil:~/Downloads/r5u870$ sudo make
make -C /lib/modules/2.6.35-28-generic/build M=/home/lomarc/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/lomarc/Downloads/r5u870/usbcam/usbcam_util.o
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_allocbuf&#8217;:
/home/lomarc/Dolomarc@lomarcportatil:~/Downloads/r5u870$ sudo make
make -C /lib/modules/2.6.35-28-generic/build M=/home/lomarc/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/lomarc/Downloads/r5u870/usbcam/usbcam_util.o
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_allocbuf&#8217;:
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c:163: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c:166: warning: assignment makes pointer from integer without a cast
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_freebuf&#8217;:
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c:177: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[3]: *** [/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.o] Error 1
make[2]: *** [/home/lomarc/Downloads/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/lomarc/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2
wnloads/r5u870/usbcam/usbcam_util.c:163: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c:166: warning: assignment makes pointer from integer without a cast
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c: In function &#8216;usbcam_urb_freebuf&#8217;:
/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.c:177: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[3]: *** [/home/lomarc/Downloads/r5u870/usbcam/usbcam_util.o] Error 1
make[2]: *** [/home/lomarc/Downloads/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/lomarc/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2


Crec que aquesta informació també et pot ser útil per saber el que em passa MB L webcam

lomarc@lomarcportatil:~$ dmesg | grep -i video
[    0.272538] pci 0000:00:02.0: Boot video device
[    1.217220] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    1.217274] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.121220] Linux video capture interface: v2.00
[   19.149430] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
[   19.153062] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   19.153996] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   19.154001] uvcvideo: Failed to initialize the device (-5).
[   19.154114] usbcore: registered new interface driver uvcvideo
[   19.154117] USB Video Class driver (v0.1.0)


Em pots ajudar si us plau?
:(:(:(:(:(

---

### Post by wgarcia on 2011-03-30
Convindria que obrissis un nou fil detallant el maquinari que fas servir tot el que puguis i descrivint el problema en detall.

---

