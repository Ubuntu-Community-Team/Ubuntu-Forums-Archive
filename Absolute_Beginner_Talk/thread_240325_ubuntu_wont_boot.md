---
title: "ubuntu wont boot"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by schreck494 on 2006-08-20
I have a dual boot set up with xp and ubuntu(with both gnome and kde).  I tried to shrink my xp partition with gparted, and it somewhat worked, but xp wouldn't boot.  So then I had to reinstall xp.   Then I had to install grub again.  Now when I try to boot ubuntu I get this error.

root(hd0,1)
Filesystem type is fat, partition type 0xb
Kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
Error 15: File not found

What do I need to do to be able to boot Ubuntu?

---

### Post by Iarwain ben-adar on 2006-08-20
I think you changed some partitions... (meaning, adding/deleting a partition)

Try to boot with the live-cd,then try these...
(in konsole)
```
sudo fdisk -l #see which one is your /
sudo kate /boot/grub/menu.lst

```
and change your /dev/hda2 with the current / partition (eg. /dev/hda3)


Iarwain

---

### Post by schreck494 on 2006-08-20
My live cd is ubuntu so it won't let me use kate.

---

### Post by Iarwain ben-adar on 2006-08-20
euhm,

then replace kate with the editor from gnome :D (gedit?)


Iarwain

---

### Post by schreck494 on 2006-08-20
gedit has nothing in it.  What do I do now?

---

### Post by Iarwain ben-adar on 2006-08-20
What do you mean, has nothing in it?

You have to use the command
```
sudo gedit /boot/grub/menu.lst
```


Iarwain

---

### Post by schreck494 on 2006-08-20
I used that code but when gedit opens menu.lst the file is totally empty.  No text or anything.

---

### Post by Iarwain ben-adar on 2006-08-20
Hmm, 
strange :s

Do you have a file called menu.lst~ ? (with the ~)


Iarwain

---

### Post by schreck494 on 2006-08-20
Same thing as without the ~

---

### Post by Iarwain ben-adar on 2006-08-20
I really don't know what could have caused that :-/

Just one last (desperate) try:
```
sudo nano /boot/grub/menu.lst
```


Iarwain

---

### Post by schreck494 on 2006-08-20
Same as gedit.

---

### Post by tuxcantfly on 2006-08-20
first, you have to make a mount point for the partition like this:

sudo mkdir /media/harddrive

check which is your ubuntu disk

sudo fdisk -l

whichever one says ext3, reiserfs, or whatever fs you're using, take that /dev/something (for example, /dev/hda2) and insert it here to mount:

sudo mount /dev/hda2 /media/harddrive

now try to edit menu.lst

sudo gedit /media/harddrive/boot/grub/menu.lst

---

### Post by tuxcantfly on 2006-08-20
actually, try sudo nautilus /media/harddisk after doing the mounting, do you actually see your harddrive's contents? if not, you didn't do the mounting correctly. if you see your harddrive's contents after doing sudo nautilus /media/harddisk, just check the boot folder, is there one? if so, check the grub folder, is there one? if so, see if there's a menu.lst in your grub folder, and edit it if there is one. If there isn't, do sudo chroot /media/harddisk, then sudo update-grub

---

### Post by mkquist on 2006-08-20
might wanna check your file path again then, because it should have something.  Ive noticed in linux it'll 'open' a file that doesn't exist.  Maybe assumes you want to make one. g/l with this because I'm having a similar problem on my second machine dual booting.  It  worked before but after reinstalling now all I get is grub error.  ](*,)

---

### Post by mkquist on 2006-08-20
sorry, just goes to show its easy to sit here and not refresh...

---

### Post by schreck494 on 2006-08-20
Thank you guys for all of your help, but it is giving me a new error.  I am just going to mount the hd and copy over any important files, and then do a fresh install.

---

### Post by tuxcantfly on 2006-08-21
what's the error? the mount or the update-grub?

before you reformat, just try mounting, chrooting and doing an update-grub

---

