---
title: "ati rage 128"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by unseenbeing on 2007-01-22
i have this card plugged into my pc

specs
933mhz p3
256mb ram
ubuntu edgy 6.10


i plug in this card and the boot up will show
then it doesnt show when it gets finished booting

i plugged in my monitor to the onboard video and it shows a very big grid of color

do i need drivers for my ati card to get it to work right
and if so where do i get them

---

### Post by wpshooter on 2007-01-22
Unseenbeing:

I take it that you are trying to install from the DESKTOP (live) CD version of Ubuntu.

Did you burn your CD at 4X or less ?

Have you checked the integrity of your Ubuntu CD by running the verification function found on the initial Ubuntu boot screen menu ?

Have you ran the memtest found on that same menu ?

Have you tried starting the Ubuntu CD with the safe video mode parameter ?

If this does not help you should try downloading and installing from the ALTERNATE (test based) version of Ubuntu.

Personally, with that machine I think you might be better off with either Dapper or maybe even Xubuntu.

Try the above and if you can get the O/S installed, write back and someone will tell you how to install "fglrx" video drivers and then edit your /etc/X11/xorg.conf file.

Good luck.

---

### Post by unseenbeing on 2007-01-22
ubuntu is already installed

the integrated video is eating the ram

i may try installing dapper cause i have a disk made from 2 months ago

what i need to know is how to install the fglrx video drivers and edit  /etc/x11/xorg.conf

---

### Post by ardchoille42 on 2007-01-22
This page should help you install the ATI drivers, edit xorg.conf and restart X:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by az on 2007-01-22
> **unseenbeing said:**
> 
do i need drivers for my ati card to get it to work right
and if so where do i get them

You switched video cards?

For older ATI cards, you do not need the proprietary flglx drivers - they don't work.  The native linux drivers work perfectly, though.

Just boot into recovery mode (from grub) and run

dpkg-reconfigure -phigh xserver-xorg

and then

init 2


The OS currently cannot reconfigure a video card without you telling it to do so.  This will be changed soon, in a more recent release.

---

### Post by unseenbeing on 2007-01-22
well now i have to reinstall ubuntu

i keep getting x server error screen
even after doing what you said

---

### Post by unseenbeing on 2007-01-22
i think i know why they called it the rage

cause the more you try to make it work 
the more the rage in you builds up until you finaly break the thing

---

