---
title: "Netbooting Yaboot"
date: 2010-05-12
forum: Apple Hardware Users
---

### Post by Mardok45 on 2010-05-12
I am running a DHCP / TFTP server and am trying to get my Macintosh's to load Yaboot via Netboot.

It as able to download the kernel and initrd when I hit enter, but it's not showing the menu (before I thought it was just freezing up).  All I get is a blank screen with the Netboot logo.

Does anyone know how to get Yaboot to flood the screen with black and display the menu like it normally does when you boot on your hard drive?

All I really did was copy the Yaboot binary onto the server and edited a new configuration, rather than running Ybin.  Is that a big no-no?

EDIT: Just to clarify, downloading and booting the kernel / initrd works fine, it's just that the menu doesn't show.  I want to be able to put in multiple options, so it would be nice to see what I'm doing.

Also, if I hold down the N key while the Mac boots, the menu doesn't show, but if I boot into yaboot on the disk and tell it to Netboot, it is able to show the menu screen and everything.

---

### Post by linuxopjemac on 2010-05-12
I never did it myself. I found a guide on the net which I copied in case it gets lost:
[http://mac.linux.be/content/booting-open-firmware#TFTP](http://mac.linux.be/content/booting-open-firmware#TFTP)

---

### Post by Mardok45 on 2010-05-13
That guide pretty much sums up what I did, but says nothing about the menu screen :(

I took a look around and I think ofboot is the program that actually floods the screen with black and displays all the options and stuff.  Do I set the server to send the ofboot file and find a way to get ofboot to grab yaboot off the server?  Would that work?

---

