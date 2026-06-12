---
title: "Complete Linux noob - Need help installing to External HD"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by cooljdude on 2007-11-23
I've attempted linux before. Another distro, unfortunately. Completely corrupted hard drive, long story.

So, I have a new 500GB external HD. I was wondering if there was a way I could install:

50 GB: Ubuntu
50 GB: Edubuntu
The rest: For backup on my Windows.

Then, I would be able to have 400 GB for backup in Windows. I would still have Edubuntu and Ubuntu though. Is that possible? I have no clue how to partition my drive, or how I would boot into the Linux partitions.

I need a way that wouldn't install Linux onto my internal HD, and have no chance of ruining it.

Any suggestions/walkthroughs.

(I need Ubuntu for myself, Edubuntu for one of the younger members of the house.) 

:confused:

---

### Post by dips_xe on 2007-11-23
i installed a distro to an external hdd before. i really wouldn't recommend it. if you do, make sure that grub is installed on the internal hdd instead of the external.

---

### Post by cooljdude on 2007-11-23
OK, but is there any type of guide?

---

### Post by dips_xe on 2007-11-23
you don't need a guide specifically for external hdd's. it's the same process as installing to an internal hdd, and there's lots of documentation that can help you with that... 

again, just make sure grub is on your internal drive.
make three partitions on your external drive,
one 49 gig, format to ext3, reiser, etc
one 49 gig, format to ext3, reiser, etc
one 1 gig swap
one 400 gig, format to ntfs

install ubuntu to the 49 gig, and once your done the installation, pop in edubuntu, but don't partition this time, just pick where you want to install it (obviously the only 49 gig left). you can use the same swap space for each os.

(by the way, you don't need to add a whole new distro to get the benefits of edubuntu. you could add the relevant packages and add this person as a user on your system)

---

### Post by backflip on 2007-11-23
> **dips_xe said:**
> i installed a distro to an external hdd before. i really wouldn't recommend it. if you do, make sure that grub is installed on the internal hdd instead of the external.

Mmmm......not my experience. I installed on an external on my desktop and if I switch the external on the ubuntu auto boots there, but if I turn it off, then I boot into Vista. I changed the bios to usb/hdd/cd.
I dual boot on my laptop  (with XP) and actually wish I had the same set-up as the desktop.

---

### Post by rsambuca on 2007-11-23
I would save yourself some drive space and just install either Ubuntu or Edubuntu.  They are the same OS, with different setups.  You can just have different logins and achieve the same result, with one less partition.

---

### Post by MozartlovesUbun2 on 2007-11-23
yes no need to install both Ubuntu and Edubuntu, just install one and get what ever apps you need later through synaptics, etc.

i just got an external drive, so i'll try suse 10.3, etc on it

and kde 4 is shaping up so nicely

---

### Post by cooljdude on 2007-11-23
Alright, I'll stick with Ubuntu. Now, is there any partitioning software for External HDs? (Sorry if I'm annoying you all :( )

---

### Post by backflip on 2007-11-23
You need gparted. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Download and burn the iso.

---

### Post by bitterbug on 2007-11-23
External install is surprisingly simple :)

(this method requires a bios that allows USB booting)

The easiest and safest way to do a USB install if you're not an experienced user is to just disconnect the hard drives in your computer, leaving only the CD/DVD drive and USB drives connected.

Go through the installation process as normal. On the very last step when you need to commit to the install, there's going to be an advanced button. Click on it, and you'll see the option to install grub on the master boot record of the main drive. If the other hard drives are connected, you don't want to do that. So make sure grub is going on the USB drive. It keeps the drive portable and doesn't break anything if you remove it from the system.

When booting from the usb drive for the first time you may get an error 17. This could be caused by the drive orders changing when IDE or SATA drives are reconnected. To fix it just select the line with```
root (hd1,0)
``` or 1,1 etc. and edit it to reflect the drive number and partition you installed to. Partition and drive numbers start at 0, so you can work your way up from there if necessary... 0,1, 1,0, 1,1, 2,0 etc.

Once you've found the location that will boot, you can then edit the menu to use the correct value by logging in and editing /boot/grub/menu.lst with the working value.

This is not the most elegant way to do it, but it removes the risk of a new user accidentally fragging their internal drives, and introduces them to grub and drive numbering in the process. :)

---

### Post by cooljdude on 2007-11-24
OK, but I already have a GRUB from my awful/broken installation of SuSE on my internal. Will that affect anything? Also, is there any way to do it that doesn't require me removing my HD?

---

### Post by backflip on 2007-11-24
This is an excellent article on installing on a usb drive and makes it easy.
[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by cooljdude on 2007-11-24
That looks great, backflip! But...will that still work in 7.10?

---

### Post by cooljdude on 2007-11-24
Also, can I make a partition in Windows Disk Management, and use it instead of my entire drive?

---

### Post by backflip on 2007-11-24
That is the steps I followed , and 'yes' I used it for 7.10. I used Windows disk management to make free space then opted for a 'manual' install from the live cd and made a / partition, a ext 3 /home partition and a swap partition. Just make sure the swap isn't ticked as a primary. That caused me a bit of grief until I realised what was wrong.
Regarding any old grub remnants on your internal, wouldn't your  windows installation cd give you access to recovery console and then you could input  fixmbr   at the prompt? I've never had to do that but it  is what I'd try.

---

### Post by cooljdude on 2007-11-24
Meh, the GRUB works and all, it's just that SuSE has this awful problem with my screen. 

That's why I want Ubuntu. I'll do what you said. Thanks for the help!

---

### Post by backflip on 2007-11-24
If you are intending to install grub on the external drive after disengaging your internal drive,  just make sure first that your bios can actually  boot from usb.  I've mine set to usb/hdd/cd.
Set the bios to boot initially from cd to load the live cd, then once ubuntu is installed you'll need to go back and change the bios to let usb have pre-eminence in the boot order.

---

### Post by cooljdude on 2007-11-25
Yes, my BIOS has a "Boot From USB" option.

---

