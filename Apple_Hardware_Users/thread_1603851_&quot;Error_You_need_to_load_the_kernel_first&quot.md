---
title: "&quot;Error: You need to load the kernel first&quot; on Ubuntu boot"
date: 2010-10-23
forum: Apple Hardware Users
---

### Post by penguin1024 on 2010-10-23
Hello everybody!
I have installed Ubuntu 10.10 on a USB 2.0 flash drive (8GB),like this: [http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)
The installation was successfull, but when i want to boot ubuntu, it shows the grub, and after it, an error message:
"You need to load the kernel first. Press any key to continue"
I've got a Macbook Pro 13'' (2010 edition) with a Intel processor.
my grub.cfg file is here:
```
# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
        fakebios
        root=hd0,2
        linux /vmlinuz root=/dev/sdb2 video=efifb agp=off
        initrd /initrd.img
}
```Can anyone help me please?:confused:
Many thanks :)
penguin1024

---

### Post by linuxopjemac on 2010-10-23
are you sure that root resides on hd0,2 ? I would think, another number, like hd1,2? 0,2 is probably your hard drive, 2nd partition.

---

### Post by penguin1024 on 2010-10-23
no, it's on sdb2 , sdc2,or sdd2 ,i have tried the three.
sda is the hard disk of the Mac.

 Maybe you have a method for checking the disks letters? i don't know how to do it...:confused:
after the line "  root=hd0,2   "  there is a line "root=/dev/sdb2"
Do i need to erase the line "root=hd0,2" ??
Thanks!!!!!
penguin1024

---

### Post by linuxopjemac on 2010-10-23
This is how the grub.cfg on my MacBook looks like (boots from hard drive):

menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 7ad7bd93-0e40-4e1f-8c78-a543ed7c4d48
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=7ad7bd93-0e40-4e1f-8c78-a543ed7c4d48 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic


you might want to change a few things. What definitely looks wrong is the initrd line, it should probablt start with /boot/initrd.img

Good luck, I am not very familiar with grub. I use PowerPC Linux much more often.

---

### Post by penguin1024 on 2010-10-23
I don't know, i'm also not familiar with grub...:)
I've tried it, but it doesn't work.
In the installation, the /initrd.img is a symbolic link to the /boot/initrd.img file (i think).
many thanks for the idea :P
penguin1024

---

### Post by penguin1024 on 2010-10-24
Another suggestion?:confused:
Thanks :P
penguin1024

---

### Post by penguin1024 on 2010-10-24
It looks like an error in EFI bootloader or in GRUB... :(
No ideas? ](*,)
Thanks!!
penguin1024

PS: Can't do it without EFI using another partition with the /boot folder- there isn't a universal filesystem fully supported by Ubuntu and Mac OS X. :(

---

### Post by penguin1024 on 2010-11-14
no ideas????

---

### Post by kayec on 2010-11-24
Just want to let you know i have a Dell d620 with XP (hd0,1) and 10.04LTS (hd0,6).  

Not sure what happened (windows update?)... something and now i'm getting the "You need to load the Kernel first.".

---

### Post by kayec on 2010-11-24
OK, found it!

Maybe i did it, not sure (would still like to blame a Windows update somehow)...

1. Booted from the live CD.

2. Follow these steps to mount your hard disk and mount your Linux partition
[http://ubuntuforums.org/showthread.php?t=1014708&highlight=howto+bootloader](http://ubuntuforums.org/showthread.php?t=1014708&highlight=howto+bootloader)

3. Once mounted type 
[PHP]ls -la /media/sda5/boot[/PHP]

4. Look for the newest vmlinuz-2.6.##-## and initrd.img-2.6.##-## (for me it was 2.6.32-25)

5. Type
[PHP]sudo gedit /media/sda5/boot/grub/grub.cfg[/PHP]

6. ** THIS WAS MY ISSUE **
In my config file these lines pointed to a vmlinuz# that didn't exist on my hard drive!
[PHP]root (hd0,5)
kernel /boot/vmlinuz-2.6.##-##-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.##-##-generic[/PHP]

7. Once corrected and saved, reboot.

Hope that helps someone.

---

### Post by penguin1024 on 2010-11-29
Thanks kayec
but on my installation (on USB pendrive )the grub.cfg is using a symbolic link /vmlinuz pointing to /boot/vmlinuz........ (the newest kernel). 
i think it isn't the problem with my installation, but thanks for your idea!!
penguin1024
PS: i'm on a MacBook Pro...

---

### Post by penguin1024 on 2011-01-29
hey guys, I know that the thread is old, but... maybe i found something...
i don't know if it's correct, but rEFIt says"legacy os" and not "linux"... maybe the os must have a BIOS part that is missing on Mac? (a "legacy" support?)

maybe some other ideas?  ;)

penguin1024

PS: sorry for my VERY bad english... :roll:

---

### Post by penguin1024 on 2011-04-10
No clue for this old thread...
I think the config files are correct, but the kernel can't be loaded for some reason...
Maybe the kernel is not compatible with the Mac???

i don't know... stupid EFI! :D

Waiting for ideas, guys...  ;)

penguin 1024

PS: I've got a 7,1 MacBook pro with Intel... maybe the EFI firmware is too recent (Apple has changed something??)

PPS: again, sorry for my English

---

