---
title: "Dual Boot Question-simple, maybe maybe not"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by reality_hunter on 2007-04-10
Hi, and thanks for all the people who are so knowledgeable about all of the help / howto / stff:

My computer has 2 hard disks: 
~230GB - SATA - master/main
~40GB - IDE - as slave

on my 40gb HD I have windows XP installed and it works fine - no problem -
on my 230gb HD - I had recently installed UBUNTU 6.10 (edgy i guess), anyways This was a clean install meaning that I had choosen the option to install UBUNTU without touching XP and had choose the option to use the entire HD for UBUNTU OS.  Which should be ok since the XP was on my other HD.  

_QUESTION:_ my question is this that when I boot my computer and in BIOS the priority for booting is CD, MASTER, SLAVE in this order.  This does not work and error comes up saying that no OS was found....(why is that? , I did install the UBUNTU on that master HD and yet it didn't find it :()
anyways, if I BOOT from the slave - I see a boot menu screen which let me choose from:
UBUNTU
UBUNTU - recovery 
---------------------------------
Windows
and soon

and both OS are working. OK, so far so good...i am happy with this configuration.  BUT my CONCERN is this:

what if I want to be able to boot from the master drive and I have my reasons like for eg.      ----that 40gb hd is kinna like few years old and I want to recycle it and throw in a different hd in the PC OR OR ----if that 40gb HD fails since its old or whatever reason.

I don't want to lose my current UBUNTU OS just because for some reason the setup have put the booting loader (i dont know the correct term) or boot menu into the windows(40gb) hd.
like i mean what the heck.?](*,) 
How can I get boot menu to load from the sata/230gb hd that has UBUNTU installed onto it? OR better yet how can I get that master hd to recoganize that there is an UBUNTU OS on it.

thanks again for taking the time to read this and for the help provided

PS: I donot want to loose anything on UBUNTU containg hd because I have spent good days working and configuring it (but loosing windows one is OK)

---

### Post by justleen on 2007-04-10
apperently, you have booted of your slave disk when installing windows/ubuntu.

It has installed GRUB on the slave. if you want to change it to boot of your primary master, you should boot off the live CD and install GRUB by hand on the primary master...

---

### Post by reality_hunter on 2007-04-10
> **justleen said:**
> apperently, you have booted of your slave disk when installing windows/ubuntu.

It has installed GRUB on the slave. if you want to change it to boot of your primary master, you should boot off the live CD and install GRUB by hand on the primary master...

hi and thanks for the reply,
you are right, I had installed windows on the slave HD and and I guess I had to boot from the slave drive in order to use windows and when Installing UBUNTU...I didn't know that that is where it will install the GRUB (boot loader)

you said to do this
_you should boot off the live CD and install GRUB by hand on the primary master..._

just to clarify, do i do:
1) insert cd and reboot and from the cd start UBUNTU (is this what you mean by live cd / session)
2) [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)  
is this what you are refering to?
thanks again

---

### Post by justleen on 2007-04-10
yep, thats describes how-to manually add grub to a HD.

but.. Its working right? It just reads the MBR of the other drive at the moment.. doenst matter that much IMHO (i have a similair setup - for different reasons)

---

### Post by reality_hunter on 2007-04-10
> **justleen said:**
> yep, thats describes how-to manually add grub to a HD.

but.. Its working right? It just reads the MBR of the other drive at the moment.. doenst matter that much IMHO (i have a similair setup - for different reasons)

cool man, thanks
i just thought that I wont be able to boot into UBUNTU without reinstalling it incase the slave fails....I didn't you could just live session and install GRUB and not harm any data........sweet
thanks again

---

### Post by justleen on 2007-04-10
erm.. no, you cant boot into ubuntu if your slave HD fails..

but then.. if you install GRUB on the master and the HD fails you have pretty much the same effect :)

---

### Post by ubuntukid on 2007-04-10
Surely if he already is able to boot into ubuntu he can simply do so and then run grub-install from there?

---

### Post by justleen on 2007-04-10
> **ubuntukid said:**
> Surely if he already is able to boot into ubuntu he can simply do so and then run grub-install from there?

ehm.. yea, he can...

Absoluty right.. slipped my mind, thanks for the pointer!

---

### Post by reality_hunter on 2007-04-10
> **justleen said:**
> ehm.. yea, he can...

Absoluty right.. slipped my mind, thanks for the pointer!

hey justleen, I tried that method described above and grub say unable to mount hd0
by using the search command, i found out that it is (hd1,0) and running that its the same inf file.

what I want is to simply boot from the same hard drive where my UBUNTU is installed on and not from the other drive where the windows is.  Can you help?????

thanks

---

