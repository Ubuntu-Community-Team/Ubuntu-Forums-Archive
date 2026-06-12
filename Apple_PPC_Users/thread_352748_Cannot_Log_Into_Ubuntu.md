---
title: "Cannot Log Into Ubuntu"
date: 2007-02-03
forum: Apple PPC Users
---

### Post by jernomer on 2007-02-03
Hi, me again.

I might have done something really stupid when trying to get the sound to work on my Powerbook (I am running 6.10). I added the sound card to /etc/module/ (I think) as per one of the tutorials. And, now I cannot log into Ubuntu.

Here is the error message I get when it attempts to boot up:
"undevd-event[2607]: run_program: '/sbin/modprobe' abnormal exit"

Does anyone know how to fix this? I figure all I need to do is somehow get to that file I changed and remove the line I added. But, how do I do that without being able to boot into Ubuntu?

I tried booting up OSX from an external drive, but (of course) I could not access the Linux partitions on my Powerbook's hard drive. I also tried booting from a 'live' Ubuntu CD on my wife's iBook and then connect to my Powerbook via firewire - thinking that I would be able to read the Linux partitions on my Powerbook from the 'live' CD - but that did not work.

Do you have any suggestions that would not result in doing a fresh install of Ubuntu? Thanks.

---

### Post by Garyu on 2007-02-03
Do you get the GRUB menu when you power on your computer? If you don't, pressing "Esc" will bring it up (not sure if that key exists on a mac...but there is some sort of key with this function anyway). From this menu you can enter "Recovery mode" where you get a terminal. You can then edit your /etc/modules with

sudo nano /etc/modules

and remove your faulty entry.

(Sorry, I'm a PC user, but you should be able to figure out a way to get the GRUB menu)

BTW, if you have a live cd, why don't you boot from it on your mac rather than trying to access through the network?

---

### Post by grazie on 2007-02-03
No grub on PPC so you need to do things a liitle differently. Boot your system with your live cd to remove your edit.

Open a terminal. Applications > System > Terminal
```
$ sudo mac-fdisk -l /dev/hda
```
This will list your partitions on /dev/hda. If your installed system is on /dev/hdb, etc, modify accordingly. Your system partition will labelled 'Linux native' on the right hand side. Make a note of the /dev/hdax on the left hand where x=number.If you have more than one 'Linux native' partition (you probably will not) post the details. I'm assuming the ubuntu system partition is /dev/hda5 for this example.
```
$ sudo mkdir /mnt/tmp
$ sudo mount /dev/hda5 /mnt/tmp
$ cd /mnt/tmp
```
With the editor you normally use, remove your change. I use vim, so
```
$ sudo vim etc/modules
$ cd 
$ sudo umount /mnt/tmp
```
Reboot your system.

Voila.

---

### Post by jernomer on 2007-02-04
Wow, thanks a lot, grazie (and Garyu), it worked. I wondered if booting via the live CD and using terminal would work, but I had no idea how to do it.

Thanks, again, for all the help.

---

