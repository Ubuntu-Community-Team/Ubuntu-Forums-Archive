---
title: "Black Screen if starting the suggested update"
date: 2018-04-01
forum: Apple Hardware Users
---

### Post by Balamku on 2018-04-01
I have an iMac in dual boot. Intel® Core&#8482;2 Duo CPU E7600 @ 3.06GHz × 2  Memory 3.9 GiB Graphics Gallium 0.4 on AMD RV730 (DRM 2.36.0 / 3.13.0-96-generic, LLVM 4.0.0) 32 Bit    

Right now I am choosing to boot into ubuntu 16.04 LTS from the advanced options menu. 
Tried several times to install the suggested updates, but ubuntu starts into black screen.  
This seems to be the closest solution to my problem> [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1705369](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1705369)  I am not sure what I should do and since the 16.04 is last on the list I am afraid to run another trial.    


**UPDATE:  **
Also a 18.04 disc boots into a black screen, so I would like to make 16.04 my main default boot option.   In the grub boot manager Ubuntu 16.04 is still an advanced option.  

**All I need to do is de-install/deactivate the Ubuntu 17 versions and make the boot loader start the Ubuntu 16.04 version as the default option. **

In theory this should be easy,  but I do need a copy and paste solution (most Ubuntu User assume one would know).

---

### Post by jeremy31 on 2018-04-01
*Thread moved to **Apple Hardware Users**.*

---

### Post by Balamku on 2018-04-03
If no-one knows how to fix this, I am sure somebody can explain how to make the 16.04 LTS my main boot selection again? (And uninstall the updates?)

---

### Post by gsahli on 2018-04-09
If you hold the Option/Alt key down on startup, do you get Ubuntu as one of the bootable options?

---

### Post by Balamku on 2019-01-13
I can start Ubuntu 16.04 as an advanced option in the grub boot loader (not by default though)

---

### Post by gsahli on 2019-01-13
I just wanted to be sure Ubuntu 16.04 was bootable.
While you're in Ubuntu, run the Terminal command:
sudo update-grub

---

### Post by Balamku on 2019-01-13
Thanks for your reply. If I use the command its shows all the ubuntu options, similar to the advanced start up options. it includes
linux image: /boot/vmlinuz-3-13-0.96-generic and /boot/initrd.img-3.13.0.96-generic. 
This is the last linux option, all others are newer starting with a 4.
I need to make the 3.13 the standard startup option.

---

### Post by gsahli on 2019-01-13
OK, got it.
Follow the instructions near the bottom of this (where it says "226").
[https://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](https://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by Balamku on 2019-01-14
Ok, I was able to understand that I had to change the first line in /etc/default/grub  (after creating a backup) from GRUB DEFAULT=0 to GRUB DEFAULT="Previous  Linux Versions>3.13.0-96-generic"

I tried to install vim but even  though the terminal and the keyring wanted my password, I wasn't able to  save my changes in vim or notepad. 

I searched the forum and  sudo su in the terminal and then gksu gedit /etc/default/grub  did do the trick. 

But I get and error message rebuilding the grub.   These are the terminal messages:  

root@Serval:/home/j# gksu gedit /etc/default/grub

(gedit:2294): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:2294): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:2294): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:2294): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
root@Serval:/home/j# sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-141-generic
Found initrd image: /boot/initrd.img-4.4.0-141-generic
Found linux image: /boot/vmlinuz-4.4.0-139-generic
Found initrd image: /boot/initrd.img-4.4.0-139-generic
Found linux image: /boot/vmlinuz-4.4.0-121-generic
Found initrd image: /boot/initrd.img-4.4.0-121-generic
Found linux image: /boot/vmlinuz-4.4.0-119-generic
Found initrd image: /boot/initrd.img-4.4.0-119-generic
Found linux image: /boot/vmlinuz-4.4.0-116-generic
Found initrd image: /boot/initrd.img-4.4.0-116-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found initrd image: /boot/initrd.img-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-96-generic
Found initrd image: /boot/initrd.img-3.13.0-96-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
done
root@Serval:/home/j# 


Haven't rebooted, afraid it might not boot anymore....
PS the error does not contain the smiley, but even repasting, it edits things....

---

### Post by gsahli on 2019-01-14
update-grub worked without error.
starting up the gedit editor is what gave errors. I don't think they are important. By the way, the sudo su was not necessary. gksu is another route to having superuser privileges in gedit.
Try it and tell us if it worked.
BTW, what's the reason you want to use the older kernel? Why not fix the graphics issue and use the newer kernel?

---

### Post by Balamku on 2019-01-14
I did reboot the system and it boots into black screen. Rebooting with advanced options, selecting the right kernel works as before. The etc/default/grub did save the changes, but the issues remains. I did read a lot regarding the graphics issue, but never found a solution. Tried Ubuntu 18.04 and Ubuntu18.10 disks recently, but the issue remains. Thinking to re-install Ubuntu 16.04 without the dual boot since I do not use the Mac part. Only thing that keeps me from doing so is the complicated Rosegarden environment. Took weeks to run it stable, later I found out, that there is a Ubuntu favor for music - maybe that would be the best option.
Sits for weeks as is, - for next weekend I might rethink trying to solve the graphics issue one more time...

---

