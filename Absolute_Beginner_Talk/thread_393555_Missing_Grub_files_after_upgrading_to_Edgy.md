---
title: "Missing Grub files after upgrading to Edgy"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by dsicher on 2007-03-25
I just upgraded to Edgy and after restarting my computer, I get to the grub menu, select ubuntu, and it gives me 
> Errot 15: Cannot find file
Press any Key to Continue...
So i do and it sets me back at the menu.
I can still load my window though
I read something about the super grub disk and have tried that but even then it still gives me the same thing, that or i just don't really understand how to use it.
I was wondering if there was a way to use the live cd to fix any thing or what?

---

### Post by cowlip on 2007-03-25
Can you try this? [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) 

> Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

### Post by dsicher on 2007-03-26
I haven't tried that but i have done this, from the same thread.
Aren't they the same thing?
Also i don't think its my MBR that is broken.


> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.



I have have tried following these Guides already and nothing has been fixed
[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?")

---

### Post by dstew on 2007-03-26
Grub error 15 means that it could not find the kernel file or the initrd file in the partition designated as root in the grub menu. It found the partition ok, but the file was not there, or the name did not match. To solve the problem, we need to see the grub menu list entries. An easy way to do this is press 'E' at the grub menu. This enters the menu edit mode, and we can see the file names.

---

### Post by dsicher on 2007-03-26
Using the live disk i am able to get to the grub menu
> 
title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro singleinitrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=2d9714ef-9da1-431e-966a-1d1c96d7e7cf ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1



also I don't know if it is important but my /boot is a separate partition

---

### Post by dsicher on 2007-03-26
Also here is a list of files in /boot

abi-2.6.15-26-386   
abi-2.6.15-28-386     
abi-2.6.17-11-386    
grub
System.map-2.6.15-26-386                      
System.map-2.6.15-28-386
System.map-2.6.17-11-386
initrd.img-2.6.15-26-386              
initrd.img-2.6.15-28-386  
initrd.img-2.6.17-11-386
vmlinuz-2.6.15-26-386
vmlinuz-2.6.15-28-386
vmlinuz-2.6.17-11-386
config-2.6.15-26-386         
config-2.6.15-28-386  
config-2.6.17-11-386       
lost+found                      
memtest86+.bin

---

### Post by dstew on 2007-03-26
Let's see your partition list. Post the output of **sudo fdisk -l**

---

### Post by dsicher on 2007-03-26
Output of 'sudo fdisk-l'

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  
Device       Boot      Start      End        Blocks         Id     System
/dev/hda1             1            637        5116671      2    XENIX root        #win restore part
/dev/hda2   *        638         7583      55793745    7    HPFS/NTFS        #Win Xp
/dev/hda3             7597       14593    56203402+  5    Extended          #(holds hda5-8 )
/dev/hda4             7584       7596      104422+     83   Linux                #/boot(or should be)
/dev/hda5            13085      14129     8393931     83   Linux                #/
/dev/hda6            14130      14403     2200873+   83   Linux                #/home  
/dev/hda7            14404      14593     1526143+   82   Linux swap / Solaris
/dev/hda8            7597        13084     44082297    7    HPFS/NTFS       #storage partion
Sorry its jumbled, can't figure out how to fix.

does the asterisk in the 'Boot' column have something to do with it? There isn't one for linux.

---

### Post by dstew on 2007-03-26
I don't see anything obviously wrong. The asterisk in the boot column doesn't make a difference, as far as I know.

Since grub found its menu, it must have been able to locate and mount the boot partition. The file names seem ok. Perhaps the UUID for the linux partition is not correct, but I don't know how to assess that.

---

### Post by dsicher on 2007-03-26
Thanks, I'll try and find out about the UUID.

---

