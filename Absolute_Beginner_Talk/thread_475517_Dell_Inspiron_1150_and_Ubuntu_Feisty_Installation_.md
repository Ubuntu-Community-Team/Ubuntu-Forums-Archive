---
title: "Dell Inspiron 1150 and Ubuntu Feisty Installation problem"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by azzkickr on 2007-06-16
Hello there

I've got a Dell Inspiron 1150. Here's technical spec.

Intel(R) Celeron(R) CPU 2.60GHz
Memory Slot 1 [DIMM_A] 256Mb

Network:
Broadcom 440x 10/100 Integrated Controller - Packet Scheduler Miniport [onboard]
RT73 USB Wireless LAN Card - Packet Scheduler Miniport [USB]


DVD/CD-ROM Drives QSI CDRW/DVD SBW242U
Disk Drives IC25N030ATMR04-0 27.94Gb

Display Adapters
Intel(R) 82852/82855 GM/GME Graphics Controller 64Mb
Intel(R) 82852/82855 GM/GME Graphics Controller 64Mb

IDE ATA/ATAPI Controllers Intel(R) 82801DBM Ultra ATA Storage Controller - 24CA
Primary IDE Channel
Secondary IDE Channel

Keyboards Standard 101/102-Key or Microsoft Natural PS/2 Keyboard

Mice and Other Pointing Devices Synaptics PS/2 Port Pointing Device

Monitors Plug and Play Monitor - (Standard monitor types) Plug and Play Monitor - (Standard monitor types)

Sound Devices SigmaTel C-Major Audio

USB Controllers Intel(R) 82801DB/DBM USB Universal Host Controller - 24C2
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C4
Intel(R) 82801DB/DBM USB Universal Host Controller - 24C7
Intel(R) 82801DB/DBM USB 2.0 Enhanced Host Controller - 24CD


I've tried several times to install Ubuntu (I have it running on another laptop and on my box) but it wouldn't even start. It gets to the beige graphical screen with mouse pointer, shows a gnome error (saying that I won't be able to save my sound or screen preferences) and that's about that. I left it running for 13 hours once. Nothing. Keeps reading CD as crazy though.

Tried redownloading the ISO and burning another CD, same problem.

I thought it might be RAM (256 only) so downloaded and burned Xubuntu - but desktop manager doesn't start - I see standard icons - Examples etc. but no taskbars or whatsoever.

Any ideas?

P.S.
I always tried to run it with my USB wifi card in - do You think it's worth trying without? I ask instead of trying as last time it took 13 hours without any success...
__________________

---

### Post by Golyadkin on 2007-06-16
Well, that "beige graphical screen with mouse pointer"; does it show you an icon that says "Install"  ?
Because that is the standard live-cd environment. To install Ubuntu itself you have to start the installation by clicking the "Install" icon.

---

### Post by whizbaby on 2007-06-16
Try with the alternate install CD. This doesnt need any xserver to install (as far as I know), and you can fix problems (if any) later. If X doesnt come up after an installation, hit ctrl-alt-f1, log in, install w3m (sudo apt-get install w3m) and type
w3m [www.ubuntuforums.org](www.ubuntuforums.org)
to still be able to browse the forums.

---

### Post by whizbaby on 2007-06-16
> **Golyadkin said:**
> Well, that "beige graphical screen with mouse pointer"; does it show you an icon that says "Install"  ?
Because that is the standard live-cd environment. To install Ubuntu itself you have to start the installation by clicking the "Install" icon.
I dont believe this as the normal install CDs are all 'live' systems, that means Ubuntu should start. On my 'install' disc theres a whole software bundle including e.g. firefox, system programs (network-admin), terminal and many many more. The only different CD I know is the alternate install CD which doesnt start a live system. :tongue:

---

### Post by Golyadkin on 2007-06-16
Well, he is using xubuntu. I don't know how that look after booting into the live-cd, but it won't show you as much as GNOME would I think. Probably just an almost empty Xfce desktop.

---

### Post by whizbaby on 2007-06-16
> **Golyadkin said:**
>  Probably just an almost empty Xfce desktop.
Exactly. + one menubar at the top (with the programs I speak of) and a process bar at the bottom.
Remeber that the live CDs are made so that people can test the system BEFORE they have to install it. Believe me, theres no such thing as an ubuntu install CD loading a Desktop and then ONLY having an install icon and no programs. (unless you can show me one).

---

### Post by Golyadkin on 2007-06-16
No of course not :) I meant that there would be an install icon in addition to the other stuff. The fact that there would be an install icon would mean he is running a live cd and had not installed Ubuntu yet.

---

### Post by markthecarp on 2007-09-16
I'm running into the same problems with a Dell Inspiron 1150. The Fiesty LiveCd gets to the Gnome start screen, which is being displayed at 640x480, the gnome error message is covered by the gnome start splash. The gnome desktop never fully starts. A Ctl-Alt-F1 gets me to vc1 after a minute or so. A "sudo halt" takes about 5 minutes to complete.

I plan to try the alternate cd later today. We are painting the computer room, aka "The Bat Cave", today. Hopefully I'll have enough of that complete to get my network back online.

-mark

---

