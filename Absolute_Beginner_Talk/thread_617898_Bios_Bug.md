---
title: "Bios Bug"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Kunks on 2007-11-19
Toshiba a-105 S-1014 laptop
Intel Celeron M 1.5 ghz
512mb ram
Realtek High Def Audio
Dual boot Xp hm/Gutsy 7.10
 boot error message-MP Bios Bug 8254 Not Connected to IO apic


I've read the posts for previous solutions for earlier versions of Ubuntu & don't know how to edit the grub to & save changes to it. When I boot after the error message the screen goes dark. When I hit control/alt f1 it will load properly by using the 8139too driver instead.... everything works fine after that except I have no sound.......Flashed the bios w/ latest & found linux drivers for sound from manufacturer  but don't know how to install them on Linux. Using Gutsy on Pentium 3 desktop w/ no problems but this laptop isn't cooperating........ 
Any help would be appreciated especially w/ detailed info

---

### Post by Partyboi2 on 2007-11-19
> I've read the posts for previous solutions for earlier versions of Ubuntu & don't know how to edit the grub to & save changes to it.hi there,
At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. add 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot

If this works and fixes it than you can add it permanent to grub menu.
Open a terminal (Applications-Accessories-terminal)
When it opens type:
```
sudo gedit /boot/grub/menu.lst
```then look for  lines like this:
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splashand add 'noapic' to the line the says  # defoptions=quiet splash (do not uncomment it) Save the changes.
Then in a terminal:
```
update grub
```Then reboot.

Or you could try to disable IOAPIC in your bios. to see if that works.
I had the same problem when I was trying to install feisty on a PC, the only way I got rid of it was installing gusty and for some reason that worked. But you are already running Gusty :-P

---

### Post by Kunks on 2007-11-19
Thanks for your efforts to help but how do I get to the grub boot screen?????? to effect the changes you have suggested.......

---

### Post by jaybombalous on 2007-11-19
u have 3 seconds, when it says grub loading stage 1_5, to press 'esc'.

Read the screen when your computer boots and u will see it.

---

### Post by Kunks on 2007-11-20
when I get to the grub loading screen it goes by to fast to hit escape.....less than three seconds...
It then goes(quickly) to the boot menu for Ubuntu, recovery, memory test, windows xp T
If I ever get to the grub boot screen how do I save changes to it??????
your help is appreciated-sorry it took me a while to post a reply.......
Kunks

---

### Post by Partyboi2 on 2007-11-21
> **Kunks said:**
> when I get to the grub loading screen it goes by to fast to hit escape.....less than three seconds...
It then goes(quickly) to the boot menu for Ubuntu, recovery, memory test, windows xp T
If I ever get to the grub boot screen how do I save changes to it??????
your help is appreciated-sorry it took me a while to post a reply.......
Kunks

At the boot menu for Ubuntu, recovery, memory test, windows Xp.
Highlight using arrow keys:
```
Ubuntu 7.10, kernel 2.6.22-14-generic (the one you highlight to boot into Ubuntu)
```press
```
e
```Scroll down to 'quiet'
press
```
e
```then press space bar once so there is a space between quiet and what you are about to add.
Add 
```
noapic
```press enter
then press 
```
b
```now it will boot ubuntu, if you are no longer getting the "MP Bios Bug 8254 Not Connected to IO apic"
then you can add  "noapic"  to  boot menu  permanently  by following my previous post.
hope this helps:
:)

---

### Post by Kunks on 2007-11-21
I followed your instructions carefully & I'm still getting the same error message... as I mentioned b/4 I did flash my bios to the latest version from toshiba..... I can still boot by hitting control/alt/f1 or f2 & it will boot up ok so I guess I can live with it . it seems like laptops have more issues with Ubuntu as my older pentium 3 desktop has no problems with the same version of linux (Gutsy)
thanks for your time & efforts to help......
Kunks

---

### Post by gcordoba on 2007-12-14
Did you try?:
1) Highlight Ubuntu 7.10, kernel 2.6.22-14-generic (the one you highlight to boot into Ubuntu)
2) Hit F6
3) Remove the word quiet at the end, and change splash to nosplash
4) add noapic irqpoll noirqdebug
5) Hit enter (and then again if that doesn't start up safe mode)

As adviced in threats:
[SOLVED] Installation Problem Mythbuntu 7.10 - Screen stays black
[http://ubuntuforums.org/showthread.php?t=591443](http://ubuntuforums.org/showthread.php?t=591443)
and
[http://ubuntuforums.org/showthread.p...8800gtx&page=3](http://ubuntuforums.org/showthread.p...8800gtx&page=3)

That soved the black screen for me. However this is not the solution for the bug...

---

