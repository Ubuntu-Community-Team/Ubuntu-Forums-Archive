---
title: "Resolució Pantalla"
date: 2007-06-11
forum: Catalan Team
---

### Post by Curial on 2007-06-11
Vaig comprar una pantalla LG flatron de 19" model L194wt. La resolució recomanada és de 1440x900 a 60Hz. La que tinc a l'ubuntu és de 1280x1024 a 76Hz.
Tinc un Compaq-HP D310 sense cap targeta gràfica, és a dir, la que du la placa base.

La limitació la tinc amb el hardware o se li pot donar més incrementant la resolució al software?

El més molest en el text algunes línies es retallen parcialment per sota i m'estic quedant guerxo!

Gràcies.
Salut a tots.
Curial.

---

### Post by patrickfromspain on 2007-06-11
sudo dpkg-reconfigure xserver-xorg i alla vas seguint.. salut!

---

### Post by AlexMuntada on 2007-06-12
Aquest problema amb un monitor diferent però de la mateixa resolució va sorgir fa poc a la llista:
[http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5193](http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5193)
[http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5197](http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5197)

Hauràs de cercar les especificacions del teu monitor per estar segur de què els valors són adequats, però la solució és la mateixa.

---

### Post by Curial on 2007-06-26
> **AlexMuntada said:**
> Aquest problema amb un monitor diferent però de la mateixa resolució va sorgir fa poc a la llista:
[http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5193](http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5193)
[http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5197](http://article.gmane.org/gmane.linux.ubuntu.user.catalan/5197)

Hauràs de cercar les especificacions del teu monitor per estar segur de què els valors són adequats, però la solució és la mateixa.

No me'n surto, he instal·lat el read-edid i he fet:
root@joan-desktop:/home/joan# get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x11110 "Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "L194WT"
        VendorName "GSM"
        ModelName "L194WT"
        # Block type: 2:0 3:fd
        HorizSync 28-83
        VertRefresh 56-75
        # Max dot clock (video bandwidth) 140 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1440x900"      # vfreq 59.887Hz, hfreq 55.935kHz
                DotClock        106.500000
                HTimings        1440 1520 1672 1904
                VTimings        900 903 909 934
                Flags   "+HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fc
EndSection

Si s'ha de configurar l'arxiu xorg.conf no se com fer-ho.
Es possible que el hardware no estigui preparat per una resolució de 1440x900 60hz?
Gràcies.

---

