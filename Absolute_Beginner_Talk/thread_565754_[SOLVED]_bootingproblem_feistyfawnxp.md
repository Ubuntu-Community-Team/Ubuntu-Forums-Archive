---
title: "[SOLVED] bootingproblem feistyfawn/xp"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Arizon_Dread on 2007-10-02
Hello!

I had a problem a couple of months ago with my hardware. I bought a new mobo and processor and installed ubuntu feisty fawn. I've been happy ever since. I got the boot loader on startup (not sure if it was GRUB or the windows boot loader). Since I had a windows xp install prior to my moboswitch, that didn't work anymore. I didn't bother until today when I installed a fresh xp on the old xp partition (after formatting it).

Now I cannot get the boot loader up on startup, and it goes directly to windows.
My linux is installed on another disk (SATA) than my windows (IDE), and I cannot see my satadisk from windows neither can I access ubuntu in any way (that I know of).

All I want is to get the boot loader to show up on startup, and then I'll start from there if I can't get my ubuntu as a choice. Can anyone help me with this? (when I open the msconfig and click the boot.ini-part, only windows comes up as a bootable option, but before my install, I had a number of linux' (safe mode and stuff) to choose from in the boot loader, and also the windows XP which didn't work.

Any help on this matter would be greatly appreciated. If I can't get it working, I'll say goodbye to windows and hope to get my ubuntu working if I uninstall windows xp. comments on this?

---

### Post by kellemes on 2007-10-02
There are a couple of options you have..
The easiest may be to burn [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and use this to boot your system.. with it you can restore your Ubuntu bootloader (Grub).

---

### Post by Arizon_Dread on 2007-10-03
Thank you Kellemes! I will try it once I get home from work today.

I just burn it and boot from the CD and follow instructions, right?

---

### Post by kellemes on 2007-10-03
yep..

---

### Post by Arizon_Dread on 2007-10-03
hmm.. Can't really get it working.. not sure what to do in the menus either..

kellemes, authorize my msn-request? :D

---

### Post by Arizon_Dread on 2007-10-03
OK. I messed around with the super grub disc before. couldn't get it working. entered bios and booted from my linuxdrive instead of my windows drive. now I get GRUB to show. it has:

> 
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional


When I try to boot my first ubuntu choice, i get:

> 
Error 22: No such partition

Press any key to continue...

and when I try to boot windows I get:

> 
Error 12: Invalid device requested

Press any key to continue...


Can I fix this with the Super GRUB Disc in some way?

---

### Post by w4ett on 2007-10-03
Here is some info to help you:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Arizon_Dread on 2007-10-03
OK. I tried the suggested material

the live-cd-thing didn't work since I have to reformat my root partition, which I hope to avoid for as long as possible

the cmdline-stuff with grub didn't work with the live cd. I can't mount my harddrives, which is wierd..


would it be a good idea to edit my BOOT.INI to include the ubuntu option? how do I go about with that?

---

### Post by LowSky on 2007-10-03
try diconnecting the windows drive, then use a ubuntu live CD to choose the option to boot from hard disk and see what happens

---

### Post by Arizon_Dread on 2007-10-04
w00000000t! I've got it working finally!

THIS IS A HOWTO BOOT UBUNTU FROM YOUR WINDOWS MBR IF YOU CANNOT BOOT UBUNTU.

the problem was: I had ubuntu feisty fawn installed in my satadrive, then I installed windows xp in my IDE drive and could no longer boot to my ubuntu OS.

after a lot of googling and help from a friend, I got it working with windows boot.ini. 
What I did was follow this guide:  [http://ubuntuforums.org/showpost.php?p=1229036&postcount=9](http://ubuntuforums.org/showpost.php?p=1229036&postcount=9)

I will now guide you through my version of that guide:

(this guide might not be totally complete, let me know if you miss something)
I assume you have installed both windows and ubuntu, and that you can't get your grub working, nor boot your ubuntu in another way, but that you can, in fact, boot windows. (maybe not necessary, but you need MBR to work and you need to be able to write and edit files to your first partition on your first disk, C:\ on my comp.) 

here we go:
1. Boot Ubuntu with the live cd.
2. Open up a terminal and write "sudo gparted"
This mounted both my drives all partitions. I had installed GRUB to a separate partition (which I don't know if it was really good). 
Now your partitions will be mounted under /media/
3. Find your "/" partition and the /boot folder from a terminal, you can get help with the path by finding it in your nautilus explorer and then copy the path from the address bar. (or type df in a terminal) When I opened my /boot folder, it was empty, so I moved my GRUB folder to /boot/grub and that did the trick, i think. this is probably risky business though.
4. Connect a USB memorystick or an ordinary floppy to your computer and mount it (if it doesn't mount automatically)
5. Find the path to your memory stick or floppy. (I will call it memory stick from now on)
6. bring your term back up and write this line:

[FONT="System"]dd if=<bootpath> of=<memory stick path>/bootsect.ubu bs=512 count=1[/FONT]

exchange <bootpath> to your personal boot path, and <memory stick path> to the path where your memorystick is mounted.

This will create a boot file on your memorystick called bootsect.ubu.

7. Reboot to windows and remove the live cd
8. Connect the memory stick or floppy.
9. Open Explorer and go to your C:\   or your first partition on your first disk (hd0,0 in linux) (the place where you can find boot.ini)
10. Make your explorer show hidden files and operating system files from the 'folder options' menu.
11. open boot.ini after you've removed the writeprotection.
12. type this line at the end of the file: 
C:\BOOTSECT.UBU="Ubuntu"
if your boot.ini resides at C:\
13. You can guess what to do now, right? if not, copy your bootsect.ubu from your memorystick to your C:\ (or your first partition on your first drive, the same place as boot.ini)
14. Hit Winkey + pause and click the Advanced tab and then click "settings" under "Startup and Recovery". choose which os you want to have as default in the drop down (where you now should see your windows os, and "Ubuntu". (this is merely a gui version of the boot.ini file)
15. Reboot.
16. Windows MBR should now be displayed and you should be able to choose between Ubuntu and Windows. When I choose Ubuntu I get the GRUB loaded and it's possible to load Ubuntu from it.

Hope someone get helped from this guide. 

THIS GUIDE DOES NOT OVERWRITE YOUR MBR.

I cannot guarantee that this will fix your problem, nor that it is risk free, but it worked for me.

---

