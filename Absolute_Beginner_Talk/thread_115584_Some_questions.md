---
title: "Some questions"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by kenny_c002 on 2006-01-10
Hi, I'm just a newbie in this, so I would like some guidance. :P

I've partitioned my hard drive for a dual boot, and I have a FAT32 partition that would be shared between the two operating systems.  The problem is that the ubuntu side is unable to write in it (but can read it).  Whenn I look at the properties, on the permissions leaflet, I see that the owner of this drive is "root", and that only root can write in it (i.e. other groups cannot).  I was wondering how I can get it so that I can write in this hard disk...

And secondly, I'd like to get Visualboy running along with an SNES emulator, but I have absolutely no idea how I would get there.  I've gotten access to multiverse and universe applications.  I think I installed them through synaptic, but I have no idea where the programs are, and how to access them (or even check if I have them installed or not).

Lastly, I wanted to get this program called "KolMafia", and I know there is a linux version of this program.  If I were to download this onto desktop, is there a way to install from my desktop?

Thanks. :)

---

### Post by jimrz on 2006-01-10
1- Look [**[COLOR="Sienna"]here[/COLOR]**]("http://www.ubuntuguide.org/#automountntfs")
 for instructions on getting your FAT (also ntfs) partions mounted correctly and to where they will auto-mount each time you start up. Be sure to scroll down the page to the section where you edit /etc/fstab, in order to get automount.

2- To locate your programs go to Synaptic, then in the panel on the left sibe (towards the bottom) click on "Status", then on "installed" (above), then find the app your want - right click it and look in properties to find where it is located on your system.

---

### Post by aysiu on 2006-01-10
[QUOTE=kenny_c002]
I've partitioned my hard drive for a dual boot, and I have a FAT32 partition that would be shared between the two operating systems.  The problem is that the ubuntu side is unable to write in it (but can read it).  Whenn I look at the properties, on the permissions leaflet, I see that the owner of this drive is "root", and that only root can write in it (i.e. other groups cannot).  I was wondering how I can get it so that I can write in this hard disk...[/quote] See the fourth link of my sig.

> 
And secondly, I'd like to get Visualboy running along with an SNES emulator, but I have absolutely no idea how I would get there.  I've gotten access to multiverse and universe applications.  I think I installed them through synaptic, but I have no idea where the programs are, and how to access them (or even check if I have them installed or not). zsnes is in Synaptic. You need to get ROMs of the games. Once you have them, right-click on the ROM and select "Open With" and type *zsnes*.

---

### Post by kenny_c002 on 2006-01-11
Thanks guys. :)

But just another question.  I have some GBA Roms and I know I have Visualboy installed.  How would I go by playing the roms?  I noticed the right-clicking did not have Visualboy actually on the program list.

Edit 2: Actually, I don't have ZNES install, I have some other emulator that I found for the snes on the synaptic, and it doesn't show up on the right-click "menu" either.

---

