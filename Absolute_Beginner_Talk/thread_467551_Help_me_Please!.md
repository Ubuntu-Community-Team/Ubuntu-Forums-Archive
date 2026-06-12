---
title: "Help me Please!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-07
After some research, I've decided to drop Beryl and try E16 or E17. But I don't have internet yet, so here are the problems:

1. How am I supposed to install the driver for my card ([driver found here]("http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel")), without internet? Can I just put all the files in a USB drive and use Sypantic to install them? 

2. Where can I download E16 to a USB drive and then install it in Ubuntu? A step by step guide would be excellent! :)


Please help out this complete Linux n00b! :(

---

### Post by pbw on 2007-06-07
1, yeah, but use dpkg.

2. same thing, it's in universe.

---

### Post by shamushand on 2007-06-07
Using the little knowledge I have, I managed to download the tarball, put it on a USB drive, save to the Ubuntu PC, and untar it. But what do I do with the driver now? :(

---

### Post by pbw on 2007-06-07
Download the .deb file, not the tarball. Slap it on the usb as is. When you go onto your ubuntu, cd to where you've placed the deb file, and issue sudo dpkg -i nameofdeb

---

### Post by shamushand on 2007-06-07
I can't find the .deb file, are you sure that it's there?

---

### Post by shamushand on 2007-06-07
I researched it, ad turns out the .deb package for i810 driver is no longer maintained because of a glitch (?)...

How do I install the tarball...

---

### Post by pbw on 2007-06-07
i'm using the i810 driver right now, and i just downloaded the .deb.

wget [http://ftp.ale.org/pub/mirrors/ubuntu/pool/main/x/xserver-xorg-video-i810/xserver-xorg-video-i810_1.7.4-0ubuntu1_i386.deb](http://ftp.ale.org/pub/mirrors/ubuntu/pool/main/x/xserver-xorg-video-i810/xserver-xorg-video-i810_1.7.4-0ubuntu1_i386.deb)

---

### Post by shamushand on 2007-06-07
I don't have internet, so I just download that manually, what are the dependencies needed? Because when I open the package, i say's "Error: Dependency is not satisfiable: libc6" :(

Using "sudo dpkg -i <package>" only get me "Errors where encoutered while processing: xserver-xorg-video-i810"

What am I doing wrong???

---

### Post by pbw on 2007-06-07
First, the driver should be included on the install cd. not sure why it didnt apply itself during install. But you should be able to pop the cd in your offline computer, add it to your sources.list and apt-get install it

But in answer to your question, here's the dependencies:

> 
$ apt-cache showpkg xserver-xorg-video-i810
Package: xserver-xorg-video-i810
Versions:
2:1.7.4-0ubuntu1 (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language:
                 File: /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
                  MD5: bbbe823a22691cff70c9323f8fa03bf3


Reverse Depends:
  xserver-xorg-video-intel,xserver-xorg-video-i810 2:1.9.91-1
  xserver-xorg-video-intel,xserver-xorg-video-i810 2:1.9.91-1
  xserver-xorg-video-all,xserver-xorg-video-i810
Dependencies:
2:1.7.4-0ubuntu1 - libc6 (2 2.5-0ubuntu1) xserver-xorg-core (2 2:1.1.1-11) xserver-xorg-driver-i810 (0 (null)) xserver-xorg (3 6.8.2-35) xserver-xorg-driver-i810 (0 (null))
Provides:
2:1.7.4-0ubuntu1 - xserver-xorg-video-1.0
Reverse Provides:


Question though, how did you get beryl working without the correct driver or direct rendering?

---

### Post by shamushand on 2007-06-07
Never got beryl working, I was planning on it though. But since this is a very old machine (533Mhz CPU, 256MB RAM, integrated i810 Card), I decided enlightenment would be.. well... lighter. :p The faster, the better!

By the way... Could you tell me the exact command to add it to sources.list and "Apt-get install" it? I'm not really good at writing the commands yet.

---

### Post by pbw on 2007-06-07
when the cd is in your drive enter 
sudo apt-cdrom
then
sudo apt-get update && sudo apt-get install xserver-xorg-video-i810

---

### Post by shamushand on 2007-06-07
It typed in "sudo apt-get -f" and it asked if I wanted to install the driver, I pressed "y"  and it said it was successful. Is that it or is there more to be done still?

---

### Post by pbw on 2007-06-07
enter 
cat /etc/X11/xorg.conf | grep Driver

If it returns 
Driver          "i810"
Then you're good to go, just reboot.

If it doesnt then you'll have to enter

sudo dpkg-reconfigure xserver-xorg

And select the correct driver and settings you'd like. then reboot and you're good.

---

### Post by shamushand on 2007-06-07
I think I hosed my system... When I bootup all I get is a flashing screen with a distorted Ubuntu logo. What now? I mean, besides probably reinstalling...

---

### Post by pbw on 2007-06-07
ctrl + alt + f2

sudo dpkg-reconfigure xerver-xorg

---

### Post by shamushand on 2007-06-07
It's asking me to select a video card... i810 is not one of them...

---

### Post by pbw on 2007-06-07
No clue then that doesnt make sense, sorry. Go with vesa though if you want. It'll still work, just no dri.

---

### Post by shamushand on 2007-06-08
Rebooting right now... let's see!

---

### Post by shamushand on 2007-06-08
Darn... screen flashes for about 15 seconds, the shows Ubuntu logo with progress bar near full, with a line cutting through it horizontally. Any insight?

---

### Post by shamushand on 2007-06-08
I'm going to that command again. This time I'll pick a different chipset. Also, how much memory should I set for the card?

---

### Post by shamushand on 2007-06-08
I'm gonna try a little longer. If nothing works, I'll reinstall tomorrow and try again. Either way, thank you guys, especially pbw, you've been very helpful to me! :D

---

### Post by shamushand on 2007-06-08
In the event that I fail again tomorrow, does E16 or E17 require a video card? :roll:

---

