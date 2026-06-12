---
title: "Boot Edit options"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by icspl on 2006-10-05
I run all my PCs with a linux grub bootl loader.  Due to reasons mostly beyond my control the default boot should be Windows.

A close inspection of configuration tools does not reveal a boot menu list editor.

I think menu list is the file to edit but defaults are not (to me) obvious, based on previous distributions.

Could someone point me in the ubuntu direction.

A real positive ubuntu (debian) is the only distribution that will find multiple instances of linux.  A real feature!!

Many thanks in anticipation

---

### Post by xyz on 2006-10-05
Hi-
One way of editing boot loader is here:
[http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed)

Another way: 
- to change default OS to load find this line "default 0" in:
```
sudo gedit (or nano) /boot/grub/menu.lst
```

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

In other words, in menu.lst, scroll down to where your listed kernels are and start counting them ...the 1st one is = to 0; the 2nd one is = 1...and so on until you get to Windows. Then type that number here: "default X = whatever number you came up with"

You can also make a backup of your menu.lst in case something goes wrong.

---

### Post by louieb on 2006-10-05
You did not find one because there ain't one. You are correct sir /boot/grub/menu.lst is the file you want to edit. To edit it open a terminal window and:
```
gksudo gedit /boot/grub/menu.lst
```  

As for what to do when you get there check this thread [Dual Boot - Default booting option]("http://www.ubuntuforums.org/showthread.php?t=271718")
In the future you might want to use the search function.

---

