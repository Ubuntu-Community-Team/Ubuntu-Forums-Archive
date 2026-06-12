---
title: "How to remove Ubuntu from the boot menu?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by SpectrumDT on 2008-02-26
Hello. 

I recently installed Ubuntu. I have two hard drives in the comp, one with Windows and one with Linux. I installed Ubuntu on the Linux one, but for some reason it's installed its boot menu on the Windows hard drive. I don't want that. I want to boot Windows from the Windows HD and Linux from the Linux HD. As it is now, to boot Windows I need to select the Windows HD and THEN bypass the Ubuntu boot menu to get to the Windows one. 

Can anyone tell me how to fix this? How do I get rid of the Ubuntu boot menu and make it enter the Windows boot menu by default again?

Thanks in advance.

---

### Post by benfindlay on 2008-02-26
GRUB installs itself by default into the primary hard drive, replacing the MBR boot sequence that windows uses. This isn't a problem however as you can boot windows by default

To get windows to boot as default do the following
Take a look at the boot list, and count down the options from the top. Whatever number Windows is, make it 1 less (see below for why), so if its the 5th in the list it becomes number 4

Type the following: ```
sudo gedit /boot/grub/menu.lst
```

Near the top of the dile there will be a section looking like this: > ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0


Change the default value of 0(zero) to the value you worked out for windows (how far down the list, minus 1). The reason you knock one off is that 0(zero) is the default boot, which is the top item in the list.

Hope this helps!

---

### Post by SpectrumDT on 2008-02-26
Thanks, but that's not what I was fishing for. I want to get rid of the Ubuntu boot menu entirely, so that the comp just goes straight to my old boot menu, never giving me the option of booting Ubuntu. Is that possible?

(Of course, I suppose I could simulate this by setting the timeout to zero, but that's ugly. What I want is to uninstall the Ubuntu boot menu.)

Thanks.

---

### Post by timbounceback on 2008-02-26
Why would you want to do that? Anyway, if you want to do this, you need to reinstall Window's mbr. To do this, I think you need to boot into a recovery disc and run "fixmbr" or something like that.

---

### Post by SpectrumDT on 2008-02-26
> **timbounceback said:**
> Why would you want to do that? 
Actually, I don't need Ubuntu at all. I am running Fedora Linux, but [my Fedora is being unstable](http://forums.fedoraforum.org/showthread.php?p=969875), so I wanted to try Ubuntu and see if it solved the problem. It didn't. Rather, Ubuntu freezes up even faster than Fedora does. Hence, I would rather keep trying to get Fedora to work rather than setting up a new distribution from scratch.

> **timbounceback said:**
> Anyway, if you want to do this, you need to reinstall Window's mbr. To do this, I think you need to boot into a recovery disc and run "fixmbr" or something like that.
OK. The help file warns that fixmbr can screw up the partitions, so I don't want to mess around and risk killing my Windows, until I have a working and stable Linux. 

Thanks for the help.

---

### Post by timbounceback on 2008-02-26
Ah, so you mean you don't want to boot straight to Windows instead of Linux (most people do). In that case, simple edit the menu.lst.

---

### Post by louieb on 2008-02-26
Replace the IPL (initial program load) in the MBR. Replace it with code that points to the windows boot loader. Lot of ways.


[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by SpectrumDT on 2008-02-27
I'll try to fix it, but only as soon as I have a reliable Linux. Thanks for the replies. :)

---

