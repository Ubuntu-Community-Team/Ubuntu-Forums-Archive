---
title: "problems on 12&quot; iBookG4 with suspend and keyboard"
date: 2010-01-09
forum: Apple Hardware Users
---

### Post by Wintergedaerm on 2010-01-09
Hello,
i have just installed xubuntu on my old 12" iBook G4 and have run into some problems.

First of all, when i go into suspend mode my iBook wont wake up anymore. wether i do it manually or i just close the lid doesnt matter.


Secondproblem i have run into is that i cant find the (at) symbol and the binary or symbol. I have tried various keyboard layout settings. Right now i have unchecked the () use system defaults. And have selected Macintosh and German- Macintosh as Keyboard layout. 

One third problem is that the ctrl key just works as a modifier for right click only on the xfce panel. But it doesn in the filebrowser nor in firefox etc.

Thnx in advance for anyone who could help, and sorry if i have overlooked something when googling etc.that wouldve solve one /more of my problems.

---

### Post by linuxopjemac on 2010-01-10
If you'd have installed Debian Lenny, you would have a working sleep/suspend laptop due to pbbuttonsd. I run it on a Pismo G3/400 and it works fine (except the fact that I have to restart the wireless kernel module). I guess you have to compile it yourself as it is not in the repository. I am not sure whether you can install the debian ppc version.

[http://pbbuttons.berlios.de/](http://pbbuttons.berlios.de/)
[http://packages.debian.org/squeeze/powerpc/pbbuttonsd/download](http://packages.debian.org/squeeze/powerpc/pbbuttonsd/download)

it seems like it's going to be back in Lucid Lynx
[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001103.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001103.html)

---

### Post by Wintergedaerm on 2010-01-10
is there any ohter package i should remove before installing pbuttonsd besides xfce4-power-manager ?

---

### Post by Wintergedaerm on 2010-01-12
So does anyone have any other clues on how to get suspend running on my ibook without having to install debian?

I have now uninstalled xcfe-power-manager and installed pbbuttonsd and powerprefs to configure it, but still my computer wont get back from sleep mode once i close the lid.

---

### Post by linuxopjemac on 2010-01-12
I don't know how pbbuttonsd works, but it needs the following packages:

    *

      dep: hdparm
          tune hard disk parameters for high performance 

    *

      dep: libasound2 (>> 1.0.12)
          ALSA library 

    *

      dep: libc6 (>= 2.3.5-1)
          GNU C Library: Shared libraries
          also a virtual package provided by libc6-udeb 

    *

      dep: libgcc1 (>= 1:4.1.1-12)
          GCC support library 

    *

      dep: libglib2.0-0 (>= 2.12.0)
          The GLib library of C routines 

    *

      dep: libstdc++6 (>= 4.1.1-12)
          The GNU Standard C++ Library v3 

    *

      dep: lsb-base
          Linux Standard Base 3.2 init script functionality 

    *

      dep: makedev (>= 2.3.1-78)
          creates device files in /dev 
      or udev
          /dev/ and hotplug management daemon 

    *

      rec: laptop-mode-tools
          Scripts to spin down hard drive and save power 

see [here]("http://packages.debian.org/lenny/pbbuttonsd")

---

### Post by linuxopjemac on 2010-01-12
I think it boils down to the fact that Karmic does not use Hal anymore, that's probably the reason you won't get it to work...I might be wrong, but that's my guess...

---

### Post by luvgirl12345 on 2010-01-13
I have ubuntu with the same problem did you find a way to use suspend? It's like the only thing. that doesn't work on ibook g4....

---

### Post by linuxopjemac on 2010-01-13
What happens if you remove the b43 or b43legacy module before sleep ?

```
rmmod b43
```
or
```
rmmod -f b43
```

---

### Post by linuxopjemac on 2010-01-13
[https://wiki.ubuntu.com/PowerPCKnownIssues#Wont%20suspend%20when%20you%20close%20the%20lid](https://wiki.ubuntu.com/PowerPCKnownIssues#Wont%20suspend%20when%20you%20close%20the%20lid)

---

### Post by Wintergedaerm on 2010-01-13
Thank you for the tipps i will try them out when i get home and post the results!

---

### Post by llamabr on 2010-01-13
I had that, and other problems.  Backup your home dir, and install debian lenny.  On my ibook, it all just works, and the net install takes 15 minutes.

Ubuntu no longer supports the ppc architecture, so it's going to get worse, I'm afraid.

---

### Post by linuxopjemac on 2010-01-14
> Ubuntu no longer supports the ppc architecture, so it's going to get worse, I'm afraid. 

I agree

---

### Post by luvgirl12345 on 2010-01-14
I installed debian but I can't connect to the internet anymore... I need the eth0 options... can't find it... would be happy if someone tests the fix... I only need the computer for school but it would be better if I could close it...

---

### Post by llamabr on 2010-01-14
> **luvgirl12345 said:**
> I installed debian but I can't connect to the internet anymore... I need the eth0 options... can't find it... would be happy if someone tests the fix... I only need the computer for school but it would be better if I could close it...

Hi.  Probably best to start your own thread.  A question like this, buried on page two of someone else's is unlikely to receive an answer.

---

### Post by linuxopjemac on 2010-01-19
debian uses HAL, pmud and pbbuttonsd. I have no idea if that will work on Ubuntu, you have to read bout power management on Ubuntu. You want to disable gnome-powermanager.

---

### Post by linuxopjemac on 2010-01-19
>  keyboard backlight

modify /etc/modules and append i2c-dev

Get the last version of pbbuttonsd and install it

wget [http://prdownloads.sourceforge.net/pbbuttons/pbbuttonsd-0.8.1a.tar.gz?download](http://prdownloads.sourceforge.net/pbbuttons/pbbuttonsd-0.8.1a.tar.gz?download)
tar zxvf pbbuttonsd-0.8.1a.tar.gz
cd pbbuttonsd-0.8.1a
./configure LAPTOP=pb

make
make install

on file pbbuttonsd

/etc/rc.d/init.d/

change the DEAMON

#DAEMON=/usr/bin/pbbuttonsd
DAEMON=/usr/local/bin/pbbuttonsd

restart

 /etc/rc.d/init.d/pbbuttonsd restart

precessor scaling

did you try this?
see [here]("https://wiki.ubuntu.com/PowerPCKnownIssues") You might want to tweak the pbbuttonsd.cnf file, see here:
[http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.cnf.html](http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.cnf.html)

---

### Post by matrav on 2010-01-22
Short press of off/on button works for me, after reopening the lid...

---

