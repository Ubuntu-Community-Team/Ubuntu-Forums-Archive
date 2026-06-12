---
title: "Grub"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-18
I have just had to rebuild a s***t installation of XP. (Xtra Pissed-off) yet again and I have lost the GRUB boot loader. I haven't re-formatted the Slave hard disc, nor have I mucked about with anything the Ubuntu install placed there. Can I replace the Grub bootloader without making a re-install of Ubuntu? If I did a full re-install i'd lose the e-mail messages in my Inbox on Evolution.

---

### Post by Seisen on 2007-04-18
Yes you can as long as you have a live cd. 

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Neil Purling on 2007-04-18
I have got the Live CD in the CD-ROM drive, which is how I am managing to type this.
The foul alternative is to use that other OS.
I just used *Synaptic* to find them. I need to find where it put the two packages.

---

### Post by Neil Purling on 2007-04-18
I have looked at the thread suggested by Seisen: No Joy

Is there anything I can do to restore the bootloader without wiping out my previous install? 
I just need a repair job.

---

### Post by indytim on 2007-04-18
Use the "other" operating system to download and burn a copy of SuperGrub.  After you have burned the CD, boot to it and use it to restore your Grub.  Please DON'T re-install your Lx ops - not needed!

Here's the link:

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")


Good Luck!

IndyTim

---

### Post by Harkainos on 2007-04-18
from what i understand (i am in the same boat you are) you can download 'super grub' and configure it in ubuntu. once configured you can install it and reboot.

someone please correct me if i am wrong.... i plan on doing this later today


EDIT: DOH .... that is what i get for not refreshing a page. Beat me too it

---

### Post by Neil Purling on 2007-04-18
I went looking for SuperGrub and got referred to a link that was broken.

So far (with the Live CD) I have used Gparted to find the references of the Linux partitions,
hdb2 being boot.
Then I did this:
mkdir /mnt/ubuntu
sudo mount -t ext2 /dev/hdb2 /mnt/ubuntu.
I can now see 'stage1' in the installed Ubuntu. 
However.....
ubuntu@ubuntu:~$ /mnt/ubuntu/boot/grub/stage1
bash: /mnt/ubuntu/boot/grub/stage1: Permission denied
ubuntu@ubuntu:~$ sudo /mnt/ubuntu/boot/grub/stage1
sudo: /mnt/ubuntu/boot/grub/stage1: command not found
ubuntu@ubuntu:~$


What do I need to do. Help me put it (back) together.

---

### Post by sailor2001 on 2007-04-18
download and use MEPIS as a live disk. In the install section you can repair boot loader

---

### Post by Neil Purling on 2007-04-18
You are referring to MEPIS Linux?

---

### Post by sailor2001 on 2007-04-18
yes.  and keep the disk as a repair disk

---

### Post by freebird54 on 2007-04-18
The Live CD and the instructions here should get you going - but having the Super GRub Disk is a good thing too.  Actually there is an even nicer tool out there as an .iso file, that consists of Super Grub Disk/Gparted/System REscue all together.  I think the link for that is on this page too...

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If not I'll try to find out where I got it myself :)

---

### Post by Neil Purling on 2007-04-18
I damn well hope that the download of MEPIS Linux can be used to repair my exisitng installation of Ubuntu without installing Mepis. 
The swine is going to take another 2hr 47min..............
I would have thought that Ubuntu would have had a repair facility to re-install/repair the Grub bootloader.
You may have to make 2 full re-installs of XP to get one that is bug free.
As I have beenable to mount hdb2 is it possible to export the 'Inbox' and 'Sent' diles and then import them to a clean re-install of Ubuntu? Just a thought if this MEPIS disc doesn't work.............

---

### Post by Neil Purling on 2007-04-18
Another thing... That given link to SuperGrub didn't work either.

---

### Post by freebird54 on 2007-04-18
Well - here is a better combo sidk anyway...  It just worked for a little while ago!

[http://forjamari.linex.org/forum/forum.php?forum_id=298](http://forjamari.linex.org/forum/forum.php?forum_id=298)

The procedure from the live CD, as detailed in the link I gave you before should be all you need for this rescue though.

Look for the menu entry  **Re-install Grub with a GRUB shell eg; with Live CD..................................................** on that page.  Nice step by step for exactly your situation.

---

### Post by Neil Purling on 2007-04-18
freebird: I took a look at that link. It's another big file.
Hopefully I won't need it..............

---

### Post by freebird54 on 2007-04-18
Sometime when you have time it is a great recovery tool.  DOn't need it for this problem though.  Actually the live CD is pretty good recovery tool itself.  I used it the other day to rescue a Win system's files :)

---

### Post by Neil Purling on 2007-04-19
So.... MEPIS has a repair function. Why not a similar procedure with Ubuntu?
There is nothing wrong with the installation of Ubuntu as that was unaffected by my having to rebuild Bill Gates's manure heap AGAIN. 
With the live Ubuntu CD I can mount the slave HDD where Ubuntu residesand find the'stage1' file in it's 'boot' direcory (see post #7). Maybe this is something to consider for future distros of Ubuntu.

Let me make this crystal clear. Ubuntu didn't f**k up, that other pile of shite did.

Does anyone know enough about Evolution to be able to tell me if the 'Inbox' and 'Sent' can be backed up or exported. That way I haven't lost any e-mail records.

---

### Post by Neil Purling on 2007-04-20
I can reccomend the link in post #14 of this thread. I have used it to restore the GRUB bootloader to the MBR of my master HDD, where a certain other OS resides.

By the way I used the option to manually restore GRUB after the auto version didn't do the job.

---

