---
title: "Installed..FINALLY!..Now What....?"
date: 2007-03-24
forum: Apple PPC Users
---

### Post by vChrist on 2007-03-24
I had one helluva hard time installing Unbuntu Edgy for my iMac g5 which included erasing my endtire system and having to reinstall Mac OSX. I finally got the dual thing working and when i log into the linux part, it gives me a command promt, tells me to login, when i do,...nothing.

I fool around with the commands, found a list, what do i do to actually use linux? im new to this...

i wanted it for the windows emulator and the cool simplicity... anyone know how to go about getting that?

---

### Post by aysiu on 2007-03-25
I don't know what happened, but this should help you get up and running:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by 3rdalbum on 2007-03-25
Have you installed the Server version, or the normal version? The server version doesn't install a GUI. If you've got the normal Desktop version, then something has gone awry with the monitor detection. The page that aysiu linked to will help in both cases.

Just so you know, WINE (which is the Windows compatibility program) does not run on PowerPC processors. That's because all Windows programs have been compiled for x86 chips. Sorry!

---

### Post by vChrist on 2007-03-25
then whats the point of linux.....?

---

### Post by stokedfish on 2007-03-25
The point of Linux is to use it with Linux applications. 

Wine sucks.

---

### Post by vChrist on 2007-03-25
is there ANY way to get wine on PPC, i was told something about Virtual PC and parallels...

---

### Post by BryannMelvin on 2007-03-26
you can't use paralells on a ppc mac just mactel. or virtual box

You CAN use Bochs to do i86 emulation  bochs is NOT very easy to use,,,and the documentation is lacking clarity

wine is not an emulation it's an api set; it needs an x86 processor([COLOR="Red"] W[/COLOR]ine [COLOR="Red"]I[/COLOR]S [COLOR="Red"]N[/COLOR]ot an[COLOR="Red"] E[/COLOR]mulator)

the only way to use it on a mac would be a mactel mac.

the bset thing to do is use an equivalent software package ....There ARE more software packages built fo linux ppc than OSX...

So WHAT are you trying to so with the machine,?

FWIW ther was a beginning project called "darwine" to do what you want in OSX  but it was never finished Open darwin and darwine have died with the birth of Mactel

Here's ths system requirements fo MS Virtual PC7 for mac  

	



System Requirements for Virtual PC for Mac Version 7

To use Microsoft Virtual PC for Mac Version 7, users need the following:

System Requirements

    * Hardware: A 700 MHz native* PowerPC G3, G4 or G5 processor
    * Operating system: Mac OS X Version 10.2.8; Mac OS X Version 10.3; Mac OS X Version 10.4.1 or later.
    * Free Hard Disk Space: 3 GB
    * RAM: 512 MB
    * Display: 1024 x 768 resolution monitor displaying thousands of colors
    * Storage: CD-ROM drive (or connection to a local area network if installing a network)
    * Peripherals: Mouse or compatible pointing device

* Upgrade cards and accelerators are not supported
I have never used virtual pc....Out of the software you questioned this seems the only possibility unless you want to learn Bochs


and sorry   this is for OSX not linux.....I suggest you do the economical thing and research alternative applicatiions....if the computer is not for production you have thousands of things to play with

---

### Post by aantn on 2007-07-03
You know that you didn't have to erase your entire hard drive to partition...

---

### Post by stmiller on 2007-07-03
Qemu works, but is slow. You have a G5 machine, so it may work okay for you. I've only used win98 in qemu just to be able to execute some .exe files every now and then.


******
EDIT: Woops, looks like Xen is x86 only. ? Anyone know?
*****

The ultimate solution (perhaps)  is Xen:

[http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen)

**
EDIT no. 2: I did find this link: [http://wiki.xensource.com/xenwiki/XenPPC](http://wiki.xensource.com/xenwiki/XenPPC)

---

