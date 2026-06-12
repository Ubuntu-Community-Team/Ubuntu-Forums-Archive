---
title: "escaner epson stylus Photo px810fw"
date: 2010-11-21
forum: Catalan Team
---

### Post by Brunilda on 2010-11-21
Salut ubuntaires,

Tinc una impressora epson stylus photo px810fw i no aconsegueixo que SANE em trobi l'escàner per poder-hi treballar.

Tal com he llegit en d'altres fòrums, he modificat el dll.conf i l'epson.conf afegint el dispositiu que mostra "sane-find-scanner":

> # epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
usb 0x4b8 0x0853
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0


> # /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# Backends can also be enabled by configuration snippets under
# /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory, named after the package.
#

# The next line enables the network backend; comment it out if you don't need
# to use a remote SANE scanner over the network - see sane-net(5) and saned(8)
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
canon_dr
#canon_pp
cardscan
coolscan
#coolscan2
coolscan3
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epkowa
epson
epson2
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
kodak
kvs1025
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
#p5
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
rts8891
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l
xerox_mfp

>   # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0853) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


Però no aconsegueix que el detecti.

Ja sé que SANE no dona suport a aquest escàner, però el que em té mosca és que quan vaig actualitzar a la versió 10.10 (maverick) l'Xsane ho va fer a la versió 0.997 i vaig poder treballar uns dies fins que una actualització de paquets (probablement) em va deixar sense l'escàner.

Perdoneu-me si no faig servir els termes adients però és que no en sé més.

Gràcies per endavant.

---

### Post by Brunilda on 2010-11-21
Tota la tarda amb aquest tema, he avançat.

Després d'instal·lar el controlador [iscan]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do") he aconseguit poder treballar amb l'escàner, això si, he d'obrir l'Xsane amb l'ordre sudo Xsane perquè si no apareix el següent missatge d'error:

"No s'ha pogut obrir el dispositiu 'epkowa:usb:001:002'. S'ha denegat l'accés al recurs.

Algú sap que s'ha de fer a partir d'aquí?

---

### Post by kimet on 2010-11-21
Prova afegint el teu usuari al grup scanner, 
```
sudo adduser usuari scanner
```

Salut

---

### Post by Brunilda on 2010-11-21
gràcies kimet,

> Prova afegint el teu usuari al grup scanner

No ha funcionat. El grup no estava creat. L'he creat i m'hi he donat d'alta però segueix tornant el mateix error.

---

### Post by Brunilda on 2010-11-21
Una tarda ben entretinguda... però ja està arreglat.

sudo aduser <usuari> lp (ho he trobat en un forum de l'opensuse)

de moment no ha funcionat, però he sortit de la sessió he tornat ha entrar i ha ja he tornat a escanejar com sempre.

Salut!

---

