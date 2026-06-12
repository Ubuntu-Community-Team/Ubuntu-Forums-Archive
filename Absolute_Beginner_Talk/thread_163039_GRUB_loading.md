---
title: "GRUB loading"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-04-20
I have installed Ubunutu on the family computer...however the first choice on the GRUB is Ubunutu i.e.e if u switch the comp on and walk away ubunut loads up. 

Needless to say, the family complains (heathens that worship at the alter of Bill Gates). IN order to soothe these souls, how do i change the boot sequence of GRUB. I have done it debian...but where do i go in UBuntu to manipulate the GRUB system??

---

### Post by dcstar on 2006-04-20
[QUOTE=neelabhro]I have installed Ubunutu on the family computer...however the first choice on the GRUB is Ubunutu i.e.e if u switch the comp on and walk away ubunut loads up. 

Needless to say, the family complains (heathens that worship at the alter of Bill Gates). IN order to soothe these souls, how do i change the boot sequence of GRUB. I have done it debian...but where do i go in UBuntu to manipulate the GRUB system??[/QUOTE]
```
sudo gedit /boot/grub/menu.lst
```and change the relevant line to:
```
default		saved
```
and the last used selection will be the default.

---

### Post by Mustard on 2006-04-20
The above solution isn't too bad, unless the Ubuntu menu choice also has savedefault (which by chance, it does in a default install), in which case it will end up being the next one loaded after someone uses Ubuntu.  To make windows permanently be the default choice there is another setting labelled 'default=0' usually.  Basically you count down the menu options (starting the count at 0) and when you work out which menu selection windows is, you change the value of default=0 to the appropriate value.  Example..

If these were your choices..

Ubuntu (newer kernel version)    ->default=0
Recovery mode 
Ubuntu (older kernel version)     ->default=2
Recovery mode
Memtest
Windows                                 -> default=5

(I haven't included values, 1,3,4 in the example, because there isn't much of a reason to boot into recovery mode or memtest by default)

So given the example above you would do this...

**Make a backup of menu.lst**
```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
#always make backups of files before changing them
#it will save you a lot of problems if you make a mistake
```

**Open menu.lst for editing**
```
sudo gedit /boot/grub/menu.lst
#open the menu.lst file for editing
```

Find the line with this in it

```
default=0
```

Change it to this..

```
default=5
#or whatever value is appropriate for your particular installation.
```

**Remove any 'savedefault' options in other menu choices**
You might want to also remove the line in your first menu entry, referring to the Ubuntu kernel...

```
savedefault
#remove this line so that it doesnt save it as default next time it is used
```

[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

---

### Post by IconK7 on 2006-05-25
Found a good site on this subject: 

Relevant page: [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

Site Home page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

After 6 months trying to install Ubuntu on my AMD64 machine, I finally succeeded: a triple-boot with WinXP SATA Raid, SUSE 10.1 64-bit, and Kubuntu Breezy 32-bit. I still have problems with Ubuntu, but these links solved the Grub boot-order problem for me. I used kwrite to edit the file, starting in the Konsole terminal with this command:

       sudo kwrite /boot/grub/menu.lst

This is same as above, substituting KDE's *kwrite* for Gnome's *gedit*.
This method obtained the default boot value by counting the number of times the word '**title**' appeared in the kwrite Grub menu list. (same as counting the OS lines in the startup Grub boot menu)


   --My machine: AMD64 4400 dual-core, Asus A8N5X, 2 x  SATA 80G hdd, 1 x  IDE 80G hdd, 2 x 1G OCZ memory, ATI X800XL videocard

---

