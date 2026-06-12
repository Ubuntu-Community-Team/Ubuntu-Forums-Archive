---
title: "how do i install ubuntu if i have windows?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by eyal_ts on 2006-08-25
hi...
i have windows xp...
can i install ubuntu if i have windows xp installed?
and if i can... can i choose what operating system i want to use everytime i start the computer?
hope to get an answer b4 i will finish downloading ubuntu...
thanks...

---

### Post by benfindlay on 2006-08-25
Indeed you can install them together! You need a separate partition/hard drive to install ubuntu onto. All you need do is put the ubuntu pc in, and then, when you are setting it up, you can choose which partition to stick ubuntu onto. I dual boot it with Windows XP, and had Xp installed before i put ubuntu on.

It will automatically configure a program called GRUB for you so that it will give you a boot menu when loading up. It boots ubuntu by default if you don't pick an option after about 10 seconds, but both the time delay on boot and the default OS to boot can be edited to suit your preferences.

So yes, ubuntu will do everything you want it to do...AND MORE! ;)

---

### Post by eyal_ts on 2006-08-25
hi again...
10x!!!!
i will install it... hope it usfull...
i hope that i can make winsows xp the defalt operting system...
10x again...

---

### Post by Kobalt on 2006-08-25
Hi,

Of course you will be able to keep your Windows XP and have at the same time Ubuntu. When you'll have downloaded and burned your Ubuntu CD, start your computer with the CD inside your Drive. It will start a Live Session, from the CD, and there you will be able to resize your partition of Windows XP to free space for Ubuntu to be installed on. 
But before you do that, I highly recommend you to make a backup of your important files and to completly defragment your hard drive. 
After that you can launch yourself safely into Ubuntu :rolleyes:


Cheers !

---

### Post by mats-a on 2006-08-25
When you boot up it will show a list over the currently installed OS, you just choose which one to boot up and press enter.
The installation is automatic and Ubuntu finds all the others OS's currently installed.

---

### Post by slibuntu on 2006-08-25
Yup, i'd recommend it, works a treat for me, dual between XP and Ubuntu, and the partition manager couldn't be much easier to use

---

### Post by Azlo on 2006-08-25
How exactly do you set the default OS and change the time limit?

Thanks for helping us mere mortals

---

### Post by benfindlay on 2006-08-25
In ubuntu you need o go into terminal and type:

```
cd /boot/grub
gksudo gedit menu.lst

```

This launches the text editor called gedit, and opens menu.lst allowing you to edit it.

There will be a section that reads something like this:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**_default 0_**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**_timeout 3_**

The bits marked in bold and underlined are the bits you want!! **_THEY WON'T ACTUALLY BE BOLD OR UNDERLINED IN THE REAL CONFIG_**

The 0 represents the 1st option in your grub boot list, so say you want windows to boot, and its the 5th option in your boot up list, change the 0 to 4

As for timeout, just change the 3 (or whatever else it reads) to the value you want

---

### Post by Azlo on 2006-08-25
wow!
i love the thoroughness
thanks a ton

---

### Post by Siriushoward on 2006-08-25
> **eyal_ts said:**
> hi...
i have windows xp...
can i install ubuntu if i have windows xp installed?
and if i can... can i choose what operating system i want to use everytime i start the computer?
hope to get an answer b4 i will finish downloading ubuntu...
thanks...

Yes, you can have both Operating Systems on the same computer.  

But firstly, you should read the [Is Ubuntu for You?]("http://www.ubuntuforums.org/showthread.php?t=63315") Article. 

You may need to format your computer (delete everything) then reinstall Ubuntu and XP.  If you feel this is too troublesome, you can try Ubuntu Live (much slower, but allows you to test Ubuntu without affecting your existing XP)

If you are sure that you want to install full Unbuntu with Windows XP, read [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot").

---

### Post by nrwilk on 2006-08-25
_**WARNING!**_  Be extremely careful when following benfindlay's instructions above!

These instructions are correct, but I want to give you a big warning right here.  The file which you will be editing is very critical to your boot manager (GRUB).  If the file gets corrupted or messed up in any way, your machine _**will not boot correctly**_.

PLEASE make a backup of the file BEFORE editing it by issuing this command in a terminal:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` 
This command will make a duplicate copy of the file called menu.lst.backup which you can use to restore the file to a working one if the edit somehow goes awry.

Even the most experienced people make mistakes while editing critical files, so it's always good to backup first.

---

### Post by benfindlay on 2006-08-25
> The file which you will be editing is very critical to your boot manager (GRUB). If the file gets corrupted or messed up in any way, your machine will not boot correctly.

PLEASE make a backup of the file BEFORE editing it

This is very true, should have put that in the post! Cheers nrwilk! ;)

What can I say, my experience with ubuntu is all about trying something and if it goes that badly then I'll just wipe it and try again! Best way to learn is to learn by doing! ;)

It can also be noted that grub.lst is the file to edit in order to get rid of the extra kernels ubuntu lists in your boot screen when you update to the next kernel released, but thats a story for another day! ;)

---

### Post by az on 2006-08-25
> **Azlo said:**
> How exactly do you set the default OS and change the time limit?

Thanks for helping us mere mortals

FYI, there was a tool for configuring Grub in the Administration menu that did just that (Gnome-boot-admin).  You would not have to muck around with a text editor to change the settings.

It created some problem for some systems and has been shelved for a while.

But yeah, someone has thought of making your life easier, it just got sidetracked, unfortunately.

---

