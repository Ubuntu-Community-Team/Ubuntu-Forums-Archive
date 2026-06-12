---
title: "Mount my hard drive."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by rollerworld on 2008-01-19
I use 4 computers, 2xwinxp - 1x ubuntu 6.06 - 1x dos 6.22 running dos cad pcb design programs.

The spec for the dos machine is,
celeron 400mhz
ram 130MB
2.4 gig HD 2 gig unused space
lan port 10MHZ
2 x USB 1 ports.
O.S. dos 6.22


I want to use this machine to access the internet with firefox via the lan port, I have a cable router, this shoud be ok. I also want to be able to mount the hard drive and copy a 50MB program to a pen drive via USB 1 port

Can I obtain a CD copy of a ubuntu O.S. that can  be installed in the 2GB free space, and give me the ability to mount the dos partition to copy a program to pen drive? And do everything else that I need?

If no, how can I easily achieve this?

Thanks Tony Johns.

---

### Post by amo-ej1 on 2008-01-19
I suggest you do the following.

a) obtain an ubuntu livecd
b) boot it 
c) mount the dos partition under ubuntu (doesn't require any free space)
d) backup the data of your dos partition to pendrive
e) repartition the disk so you can install ubuntu on it and restore the dos partition next to it 

Don't omit the backup part ! 

Once ubuntu is installed you have some options. You can either dual boot between ubuntu and dos. Or you can run dos within ubuntu. Ubuntu has for example several x86 emulators and even dos emulator   (e.g. apt-cache search dosemu )

---

### Post by mips on 2008-01-19
Out of curiosity why don't you run your pcb design stuff in wine or use dos in virtualbox. There might even be linux pcb design stuff out there.

Just wondering as I would get annoyed switching between so many computers.

---

