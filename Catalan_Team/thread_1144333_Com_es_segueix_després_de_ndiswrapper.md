---
title: "Com es segueix després de ndiswrapper?"
date: 2009-04-30
forum: Catalan Team
---

### Post by lpargemi on 2009-04-30
Hola

Estic provant amb un wifi per USB *Sitecom WL-608 v1.001* que no suporta Linux. He vist que es pot provar amb ndiswrapper i els drivers de windows. L'he instal.lat i obtinc 
```
lluis@lluis:~$ ndiswrapper -l
rt2870 : driver installed
        device (0DF6:003F) present

```
Molt bé, i ara que més he de fer per tal de configurar i fer servir això? No m'apareix aquesta tarja wifi quan entro a la configuració de la xarxa. Es perquè em deixo alguna cosa, o perquè simplement aquest equip no és compatible ni amb ndiswrapper?

Si miro els ports usb em surt: 
```
lluis@lluis:~$ lsusb
Bus 005 Device 003: ID 0df6:003f Sitecom Europe B.V.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0a81:0203 Chesen Electronics Corp. Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

On el Sitecom aquest és la tarja wifi

Agraït

Lluís

---

### Post by PatrickVogeli on 2009-04-30
sudo modprobe ndiswrapper i torna provar

---

### Post by CarlesOriol on 2009-05-01
i després del que ha dit en Patrick fes un dmesg per veure que no hi ha cap error.

---

### Post by lpargemi on 2009-05-02
Hola. He estat fora uns dies i no he pogut provar res.

Ara que he tornat, amb dmesg em trobo això, així que si que hi ha alguna cosa que falla. 

```
[   49.947461] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   49.947595] ndiswrapper (load_sys_files:210): couldn't prepare driver 'rt2870'
[   49.948056] ndiswrapper (load_wrap_driver:112): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   49.949172] usbcore: registered new interface driver ndiswrapper

```

Miro al registre del sistema el syslog i hi trobo a la mateixa hora:

```
Apr 30 23:15:34 lluis kernel: [ 6636.024983] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 23:15:35 lluis kernel: [ 6636.150038] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Apr 30 23:15:35 lluis kernel: [ 6636.293791] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
Apr 30 23:15:35 lluis kernel: [ 6636.293946] ndiswrapper (load_sys_files:210): couldn't prepare driver 'rt2870'
Apr 30 23:15:35 lluis loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver rt2870 
Apr 30 23:15:35 lluis kernel: [ 6636.374906] ndiswrapper (load_wrap_driver:112): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
Apr 30 23:15:35 lluis kernel: [ 6636.374934] usbcore: registered new interface driver ndiswrapper

```

Suposo que alguna cosa d'aquests drivers per windows deu estar massa malament perquè sigui assumible des de ndiswrapper

Lluís

---

### Post by CarlesOriol on 2009-05-03
Vens dissabte a la festa?

---

### Post by lpargemi on 2009-05-03
> Vens dissabte a la festa? 
Em sembla que no. Amb els saraus de la família és molt difícil que em pugui escapar així un dissabte, i menys en el més de maig, que son festes a Badalona. 
Que us ho passeu bé!

---

