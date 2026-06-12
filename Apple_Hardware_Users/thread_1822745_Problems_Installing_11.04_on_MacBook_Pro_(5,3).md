---
title: "Problems Installing 11.04 on MacBook Pro (5,3)"
date: 2011-08-10
forum: Apple Hardware Users
---

### Post by Arctic Shadow on 2011-08-10
Hello there,

I've been trying to install 11.04 on my MacBook Pro for the past couple weeks, and I'm getting pretty frustrated with it.

When I try to boot from a DVD, I either get a blank screen with just a flashing cursor, or it will ask me if I want to try, install, or verify the disc, after which I will get a bunch of different-colored blocks all around the screen.

I have installed past versions of Ubuntu on this computer with no problems, so I'm pretty stumped now on why I'm having this problem. Also, I've tried the Ubuntu Wiki and sticky thread on this forum, but nothing in either seems to help. Additionally, I have installed Mac OS X 10.7 Lion. I don't think it'd effect anything, but I thought it was worth mentioning.

Thanks! =)

---

### Post by Arctic Shadow on 2011-08-12
Last night, I finally managed to get to install Ubuntu after changing an option in the F6 menu for selecting to try or install the system. After installing it, I updated the MBR with rEFIt and tried to boot into Ubuntu, which brought up the same issue I was having with the live CD: just a blank screen with a flashing cursor.

Additionally, the Ubuntu partition on my computer will not mount under Mac OS X (I am using fuse-ext2 for ext support), and it gives me an inaccessible folder icon for that partition when viewing it in Disc Utility. It shows that it is mounted, and when I try to unmount it, it gives me an error.

I'm really hoping I can get this up an running soon, I really want to get to use Ubuntu on my computer... =/

---

### Post by jtaylor7192 on 2011-08-29
Having the same problem.

I'm trying to dual boot Ubuntu 11.04 alongside OS X Lion on a Macbook pro 5,3. The first time I tried to boot from the live CD a menu appeared but it lead to those same colored blocks. Now when I boot from the CD all I get is the black screen with the flashing cursor.

I've been using these pages.

A general guide on installing Ubuntu on a Mac:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Information specific to Macbook pro 5,3 but nothing on how to install Ubuntu.
[https://help.ubuntu.com/community/MacBookPro5-3/Natty](https://help.ubuntu.com/community/MacBookPro5-3/Natty)

Can you post here if you get it working.

---

### Post by feasty on 2011-11-23
I've just got it working on my Mac Mini which had the same problems as your Macbooks were showing. This is with 11.10 but it's probably the same for 11.04. Here's what I did to get it working:

1. Download the 11.10 cd enhanced for Macs from [http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)
2. Reboot the mac and hold C down when the screen goes blank to get it to boot off the CD.
3. When the cd menu comes up press return and select your language.
4. Go down to the 'Install Ubuntu' option and press F6 to bring up the options.
5. Select noapic, acpi=off and nomodeset
6. Boot the 'install ubuntu' option

Note: If anyone else is trying to replicate this on a desktop using the wireless keyboard an mouse I found that mine didn't work for the installer and I had to use a wired keyboard an mouse.

---

### Post by feasty on 2011-11-23
Update: You can get your bluetooth keyboard an mouse by going to system settings and adding the devices once the installer has started using your wired keyboard an mouse.

---

### Post by jfishman on 2012-06-11
> **feasty said:**
> 
5. Select noapic, acpi=off and nomodeset


Thank you!  This worked from the EFI Grub2 on the standard 12.04 LTS 64-bit ISO to load the installer.  Hopefully all else will proceed smoothly...

*Edit*
Only the "nomodeset" option was required.  The others (specifically "acpi=off") disabled the keyboard and mouse, making installation impossible.

---

