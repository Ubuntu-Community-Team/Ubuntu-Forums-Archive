---
title: "To remove Utunbu 7.04 and install Xp.."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-19
I got Utunbu like 2 weeks ago and I tried to use but..it's just too hard for me..:'(

so I'm trying to install Xp again.

I tried to install Xp but I couldn't, when I boot, it will say GRUB loading error 17..

and I looked up some forums but I don't really get it..

can anyone help me ? 

Thank you :)

---

### Post by aysiu on 2007-05-19
Try [this](http://support.microsoft.com/kb/314458).

---

### Post by Sef on 2007-05-19
From the [Gentoo error]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6") collection:

> 5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it. 

How did you install it?

---

### Post by rocketboys on 2007-05-19
> **aysiu said:**
> Try [this](http://support.microsoft.com/kb/314458).

Thank you for your response!


To remove Linux from your computer and install Windows XP, follow these steps:
1.	Remove the native, swap, and boot partitions used by Linux:
a. 	Start your computer with the Linux Setup floppy disk, type fdisk at the command prompt, and then press ENTER.

NOTE: For help with using the Fdisk tool, type m at the command prompt, and then press ENTER.
b. 	Type p at the command prompt, and then press ENTER to display partition information. The first item listed is hard disk 1, partition 1 information, and the second item listed is hard disk 1, partition 2 information.
c. 	Type d at the command prompt, and then press ENTER. You are then prompted for the partition number that you want to delete. Type 1, and then press ENTER to delete partition number 1. Repeat this step until all the partitions have been deleted.
d. 	Type w, and then press ENTER to write this information to the partition table. Some error messages may be generated (because information is written to the partition table), but they should not be significant at this point because the next step is to restart the computer and then install the new operating system.
e. 	Type q at the command prompt, and then press ENTER to quit the Fdisk tool.
f. 	Insert either a bootable floppy disk or the bootable Windows XP CD-ROM, and then press CTRL+ALT+DELETE to restart your computer.

I saw the link you gave me and I tried that, but first, I don't get that 

"Start your computer with the Linux Setup floppy disk,"

because I don't have a floppy disk..

or am I misunderstanding something? can I do this on terminal on utunbu..?

thank you. :)

---

### Post by mrbungle on 2007-05-19
you can't just format your hard drive with the windows xp cd?

seems like that would work, but haven't tried before.

---

### Post by aysiu on 2007-05-19
You can use GParted on the Ubuntu live CD to reformat the drive (it's kind of like a graphical version of *fdisk*). You can "install" (it goes to your RAM during the live session and then disappears right afterwards) GParted [using Synaptic Package Manager](http://www.monkeyblog.org/ubuntu/installing).

Or, if you prefer [the terminal](http://www.psychocats.net/ubuntu/terminal), boot up the live CD and then paste this command in the terminal: ```
sudo apt-get update && sudo apt-get install gparted gksu && gksudo gparted
```

---

### Post by rocketboys on 2007-05-19
> **aysiu said:**
> You can use GParted on the Ubuntu live CD to reformat the drive (it's kind of like a graphical version of *fdisk*). You can "install" (it goes to your RAM during the live session and then disappears right afterwards) GParted [using Synaptic Package Manager](http://www.monkeyblog.org/ubuntu/installing).

Or, if you prefer [the terminal](http://www.psychocats.net/ubuntu/terminal), boot up the live CD and then paste this command in the terminal: ```
sudo apt-get update && sudo apt-get install gparted gksu && gksudo gparted
```

Thank you for the response!

I did the code you gave me.

I see this graphical fdisk thing now..

but I don't really know what to do right now. 

I'm looking at dev/sda right now which is the drive I want to install my windows.

and I can right click on it. Do I press format to ntfs here?

thank you :)

---

### Post by aysiu on 2007-05-19
I believe you can right-click to delete the partition and then right-click again to reformat it as NTFS. If you can't reformat it as NTFS, you have two choices--1. install NTFS support (I think it's *ntfsprogs* you have to install) or 2. format it as FAT32 (Windows' installer should be able to recognize and change FAT32 to NTFS during the installation process).

---

### Post by sandman55 on 2007-05-19
It seems pretty clear from your first post that you originally replaced XP with Ubuntu but if you dual booted then post back because it quite easy to get back to windows from there and if in the future you want to try Ubuntu again then do a dual boot because you can fall back on windows for some things you find hard and that gives you an easier path to Ubuntu

---

### Post by rodrigo juarez on 2007-05-19
I've found issues overwriting Linux (any flavor) with windows (98-xp) and I believe the problem has always been that windows doesn't know that grub/lilo are installed (shouldn't be like that I guess).
Windows installs fine but upon reboot you¡ll find grub/lilo still there not being able to mount anything. So I would try to uninstall grub/lilo with a grub/lilo floppy and then use windows fdisk to get rid of the partitions, then creating new ones and installing there.

Hope it helps/hope you'll think it twice.
=D

Get him boys!
We are loosing him!

---

### Post by mrbungle on 2007-05-19
what about using a program like killdisk?  what this make a clean slate for a xp install?

---

### Post by eentonig on 2007-05-19
Sorry for the off-topic rant.

 But Windows is soo advanced and easy to install. It just takes care of everything :mrgreen:

I espacially like the guide in the microsoft website "take your linux setup floppy..."

Strange that an OS with such fame can't adjust the bootloader itself. And redo whatever partitioning that is in place.

---

### Post by hyper_ch on 2007-05-19
Where is that m$ site? I'd love to see that on my own :)

---

### Post by trishacupra on 2007-05-19
Just checking - is your BIOS boot order set up to boot from your XP install disk first, or your hard drive?

In my mind, if you're booting from the WinXP setup disk, the installation should wipe everything on your hard drive.

Tell us exactly what steps you're taking, please, and how far you've gotten.

---

### Post by mahy on 2007-05-19
> **rodrigo juarez said:**
> 
Get him boys!
We are loosing him!

I believe questions related to replacing Linux with windows should be strictly offtopic (and banned) in this forum. If you don't like Linux, then good-bye. There are far more windows forums and usenet groups than Linux ones.

To the OP: if you BOOT the windows cd and install XP from it, i'm sure it'll remove Grub straight away.

---

### Post by hyper_ch on 2007-05-19
mahy

If he doesn't like it then there's no need to force him to stay here... by helping him we show the outside world that we are different from corporta monopolies... we actually help a human being when we can...

---

