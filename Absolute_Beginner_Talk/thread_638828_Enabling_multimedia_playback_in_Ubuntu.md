---
title: "Enabling multimedia playback in Ubuntu"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by fuse5k on 2007-12-12
Hi, My name is Ian and i've just departed microsoft and all that goes with it.

I suppose i've been a bit stupid really, i got a bit baked and installed ubuntu over windows without meaning to. I was hoping for a dual boot thing, but that hasn't really panned out.

I cant make a single complaint about the installation process, and my internet worked straight off, even via a router.

I however have 2 major issues with my move, sounds & video...

I have no sound at all, and to be honest i havent a clue how to find out.

I have a graphics card, and i've got my TV running through it, however since my first boot i have been viewing stuff in glorious  800*600 and i cant get a picture on the tv at all.

A more minor gripe is that i cant view any of the common video files off the internet (swf/avi)

any help would be greatly appreciated, even if its just pointing me to somewhere i can read a bit about how to do stuff.

I have a windows disk and i dont want to have to use it...

Cheers

Ian

---

### Post by meborc on 2007-12-12
Hi and welcome :)

due to legal issues, the mp3 and video codecs can not be included in the ubuntu cd... BUT they can easily be installed...

First you need to enable the extra repositories
like this [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

EDIT: you might also check to see if all the extra repositories are enabled in the synaptic

And then install the ubuntu-restricted-extras package
type this in the terminal:
**sudo apt-get install ubuntu-restricted-extras**

---

### Post by thelatinist on 2007-12-12
Install the ubuntu-restricted-extras package.  It contains the codecs and such for playing media files which in some jurisdictions can pose legal difficulties.

As for your other problems, you will need to tell us what kind of graphics card and sound card you have.

---

### Post by philinux on 2007-12-12
Click on the multimedia link below and work through it.

As said legal beagel stuff.

---

### Post by aysiu on 2007-12-12
> **meborc said:**
> Hi and welcome :)

due to legal issues, the mp3 and video codecs can not be included in the ubuntu cd... BUT they can easily be installed...

First you need to enable the extra repositories
like this [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

EDIT: you might also check to see if all the extra repositories are enabled in the synaptic

And then install the ubuntu-restricted-extras package
type this in the terminal:
**sudo apt-get install ubuntu-restricted-extras**
Actually, the legal reason is secondary. The main reason is philosophical:
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

If you want a step-by-step (with screenshots) guide of what meborc is talking about, go here:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by The Tronyx on 2007-12-12
> **fuse5k said:**
> 
I have a windows disk and i dont want to have to use it...


Sir, put down the Windows disk!:lolflag:

First of all welcome to Ubuntu.  A lot of the problems you described I have seen addressed multiple places on the forums and from personal experience, the best advice I can give you is to search.  I personally have never had problems with sound so I unfortunately I am of little assistance on that problem but using the search problem and looking for "no sound" or "sound issues" sound turn up quote a few results.  Also looking for what kind of sound card you have and using that as a search term on the forums could prove to be quite useful.

Another tip when using the forums and looking for assistance is providing as much information about your problem and system as possible in the question.

It always helps to have information such as:
Linux version
Hardware information (processor, sound card, video card, etc.)
Any error messages you recieve are a great help too

I already see after previewing this post that others have pointed you in the right direction for playing various media formats in linux so on that note I wish you the best of luck and a sincere welcome to the open source community!

---

### Post by Don1500 on 2007-12-12
1. Since you say you installed Ubuntu over windows, You will have to re-install windows if you ever want to run it. 
2. All your data and pgms that you may have had in windows will also need to be reinstalled.
3. You didn't say what kind of vedio card you have but you may need to install propritary drivers for it (you may have had a pop-up for this in the upper right of your window, follow thise instructions.)
4. Sound.... Check your set up and options, make sure it is turned on then cry, then come back here and search the forum for similar problems.:lolflag:

---

### Post by OffAxis on 2007-12-12
TV out is only available on the proprietary ('restricted') drivers.

Enabling the restricted driver is really easy nowadays; it's probably a checkbox somewhere. I'm not sure where it is in gnome; probably under system setttings --> video.

---

### Post by aysiu on 2007-12-12
> **OffAxis said:**
> TV out is only available on the proprietary ('restricted') drivers.

Enabling the restricted driver is really easy nowadays; it's probably a checkbox somewhere. I'm not sure where it is in gnome; probably under system setttings --> video.
This is how you do it in Gnome:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by fuse5k on 2007-12-12
cheers for the help... 

does anyone know how i can find out what hardware i have?

---

### Post by aysiu on 2007-12-12
> **fuse5k said:**
> cheers for the help... 

does anyone know how i can find out what hardware i have?
I think pasting the command ```
lspci
``` into [the terminal](http://www.psychocats.net/ubuntu/terminal) lists your hardware, which you can then paste back here.

---

### Post by ajgreeny on 2007-12-12
Or if you want a full list of everything on your machine it's ```
sudo lshw
```

---

### Post by fuse5k on 2007-12-12
ian@ian-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


right,  so im guessing that mine is an on board sound card? what do i need to do???

---

### Post by aysiu on 2007-12-12
> **fuse5k said:**
> i feel like such a tool, but how do i get a command line...
Click the link I posted earlier: *the terminal*

---

### Post by fuse5k on 2007-12-12
> **aysiu said:**
> Click the link I posted earlier: *the terminal*

sorry didnt read first time round...

---

