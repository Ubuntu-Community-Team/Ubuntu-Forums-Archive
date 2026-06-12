---
title: "Installing Ubuntu on 2ND harddrive?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Ghot on 2007-11-18
ok...currently I run Windows XP Pro SP2 installed on my primary HD a WD raptor 36GB
I also have a secondary HD Seagate I think...80GB

Here's the questions:
1.  Previously I have installed Ubuntu 6.xx on my Primary HD and had ONLY one problem...
     a.  Every time the grub loader updated itself, it wud ADD another entry to the OS choices menu.
          HAS THIS BEEN FIXED in the 7.10 version?  I do NOT want an OS choices menu with my winodws
          install and then 2,3,4,5 etc  grub loaders listed.
2.  Now for the hard question...IF I were to install 7.10 on my secondary HD, would I then be forced to 
     go into the BIOS everytime I wanted to switch back and forth between OS's?

Primarily I game on Windows XP Pro..I'd like to be able to "game" on Ubuntu.  However, after reading the forums for hours on end, I still see 100's of issues concerning gaming/multimedia.

My main desire is to be able to say: Hasta la vista to Windows entirely, and of course I also want to be able to do everything on an Ubuntu OS that I can on Windows XP Pro.

For example: 
1.  I want to be able to go to the store and buy a game and install it and play...without having to deal
     with command lines, binaries, etc  Is this possible on Ubuntu...yet?   If not, is there any Linux 
     distro that does this?
2.  I guess what I'm really saying is:  I want Windows XP Pro system w/o the Microsoft..as they are
     getting way out of hand.
3.  I have Verizon DSL at the moment   soon to be Verizon FIOS......will my Verizon WEBMAIL work on 
     Ubuntu?  I use NO email clients, I dont trust them, and they are very insecure.

Linux is on the verge of blowing Windows (any version) out of the water...entire countries are switching to Linux.  I WANT to switch to Linux but I want the ease and compatibility of Windows XP Pro...is this possible at this time??????


MY SYSTEM at this time:

Motherboard:
ASUS A7N8X Deluxe rev. 2

Processor:
AMD Athlon XP 2800+ Barton Core .13um

Memory:
Corsair XMS TWINX2048 PC4000PT

Video Card # 1:
BFG Nvidia GeForce 6800GT (factory OC'd)

Hard Drive # 1:
WD 36GB 10,000rpm Raptor SATA

Hard Drive # 2:
Seagate 80GB 7200rpm SATA

Optical Drive # 1:
Lite-On LTR-52246S CD/RW

Optical Drive # 2:
Lite-On LH-18A1P CD/DVD Burner

Power Supply:
PC Power & Cooling Silencer 750 Quad (Black) EPS12V 750W Continuous @ 40°C (825W Peak) Power Supply

Case:
Full Tower (Gerneric)

Sound Card:
none

Monitor:
ViewSonic G90FB Black 19" CRT Monitor

---

### Post by meierfra on 2007-11-18
I can answer your first two questions:
> 
1)  Every time the grub loader updated itself, it wud ADD another entry to the OS choices menu. HAS THIS BEEN FIXED in the 7.10 version? 

You can (and always could) choose how many Ubuntu kernel you want to have on the grub menu:

The file "/boot/grub/menu.lst" contains "#howmany=all" . Change it to #howmany=1" and type "sudo update-grub" in a terminal

After that you will just have "Ubuntu" and "Ubuntu, recovery mode" on the Grub menu.
(and  it stays that way after a kernel upgrade) 

> 2. Now for the hard question...IF I were to install 7.10 on my secondary HD, would I then be forced to
go into the BIOS everytime I wanted to switch back and forth between OS's?

No.  It works just the same way as with one hard drive. You can choose the OS from the Grub menu. No need to mess with the bios.

---

### Post by PointyWombat on 2007-11-18
for #1, you can do as meierfra states, or you can just uninstall the old kernels via synaptic.

for #2,  also as per meierfra

for #3, if your webmail works for you today with firefox on windows, then it will most likely work with firefox on ubuntu. Try it with the live CD.

---

### Post by bumanie on 2007-11-18
Regarding games, you can check out this site and see if it meets your needs.
[http://www.tuxgames.com/](http://www.tuxgames.com/)
[http://www.transgaming.com/](http://www.transgaming.com/) (this one costs a small monthly fee, I think)
Also look at [http://www.getdeb.net/](http://www.getdeb.net/) where there a number of pre-compiled packages that should only need a double click to install.

---

