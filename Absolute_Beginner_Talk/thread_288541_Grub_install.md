---
title: "Grub install"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by thor908 on 2006-10-30
when i try to install  right before i start i get this:
GRUB will be installed to (hd0)
what is hd0? ithink its my computers harddrive...but i want it on my external hardrive with the rest of ubuntu... the external is a fujitsu firelite what do i replace hd0 with? 

help suggestions.....please

---

### Post by kinanti on 2006-10-30
Hello. I'm new to Ubuntu and Linux, but i'll try to help you. GRUB gave me headaches (and now I have all kinds of other problems : suspend and hibernation mode, wifi, scanner, etc…. might give up soon… :( )

Anyway.

**(hd0)** is effectively, normally, your computer's hard drive (Ubuntu live cd will install grub on your internal drive.) 

So **(hd1)** should be your external hard drive if you have only 1 internal hd an 1 external hd.

You'll have to boot with your external drive (so set your bios appropriately) to have your Grub working if set written to hd1's mbr (master boot record – first sectors of you HD).


If you get stuck after installation, try this (taken from someone else in the forum) :
 
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal (in applications, accessories, I think).

3. Type "sudo grub". Enter root passwords as necessary.
 which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd1,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd1,3)" (hd1,3 being whatever your computer's output was for the previous step).

6. Type "setup (hd1)". This is to write GRUB to the MBR of the HD. If you want it on your Linux root partition, use the code you used in the previous step ((hd1,3), in my case -- means hd #1, partition #3).

7. Type "quit".

8. Restart the system. Remove the bootable CD.


9…… If you get a "Grub error 22" or 17 or something like that, you might need to edit your "menu.lst" file. use the live Cd, mount your linux partition, find the /boot/grub directory. The file is there somewhere.

Just make sure that these are right :
**root (hdx,y)** 
[where the x an y correpond to the rigt numbers - see step 4]
and
**kernel /boot/vmlinuz-2.6.12-10-386 root=dev/*hdax* ro quiet splash**
[where the ***hdax*** correponds to the right device - use the gnome parition manager from the live cd to get the right name for your device]

And if you can't boot your other OS for some reasons, try the **GAG bootloader**.
**[http://gag.sourceforge.net/](http://gag.sourceforge.net/)**

Hope this helps. :) 

Kinanti

---

