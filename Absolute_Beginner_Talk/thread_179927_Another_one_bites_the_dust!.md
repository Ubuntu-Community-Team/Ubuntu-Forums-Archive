---
title: "Another one bites the dust!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-21
Well almost.  I am currently dual booting with windoze on my primary drive on the computer I am using for linux.  I have found myself going to windows on this computer less and less.  Until now I just want to format the windoze drive.  Thing is Ubuntu is on the slave drive.  I know I must redo the jumpers so that linux is master and windoze is slave but what do I do after that so that linux automatically boots without having to wipe the drive and redo everything.

---

### Post by ctgray on 2006-05-21
It would most probably be easiest to just save all important data and do a clean install.

I tried once to do what you want, but stuffed it up and just bit the bullet.

Good luck either way. Sorry I couldn't be of more help.

---

### Post by skippy81 on 2006-05-21
[QUOTE=ctgray]It would most probably be easiest to just save all important data and do a clean install.

I tried once to do what you want, but stuffed it up and just bit the bullet.

Good luck either way. Sorry I couldn't be of more help.[/QUOTE]

I agree with him about it being best to assume you will have to do a clean install and backing everything up.

Howeever once you are backed up and ready to lose everything you could try this:

1) Boot from an ubuntu live CD, with your ubuntu hard drive set to master and your windows drive disconnected.     

2) Open a terminal and type "sudo grub-install /dev/hda" 

3) With a bit of luck this will install grub to the master boot record of the first hard disk, if you are using sata you may have to use "sudo grub-install /dev/sda".

4) Once grub has sucessfully installed itself on the MBA of the first hard disk, you should be able to then connect the old windowze disk as a slave, and reformat it etc. 

If you don't have a live CD then it is possible to make a floppy disk with a grub booter and the files needed to install grub on it, have a search for "grub boot floppy" if this is the case.

DISCLAIMER: I have never actually done this before, so please don't follow these instructions unless you are backed up and in a posistion to fully reinstall anyway.

---

### Post by JNowka on 2006-05-21
And I just got linux the way I like it ....

---

### Post by Ecthelion on 2006-05-21
I've found this easier to reinstall grub:

[http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")

---

### Post by iball on 2006-05-21
When you say that you want Linux to boot automatically, do you currently get a GRUB screen for you to select Windows or Linux?  If so, have you changed the default boot option for Grub to be Windows?  Why not just change it back to Linux?

Then you can format your windows partition, and create an ext3 file system on it, and mount it somewhere of your choosing (say /data) and use it for documents, music etc.  Search the web for how to do this.  This way, you are not touching GRUB on the MBR of the first hard drive.  Linux will quite happily live on a slave hard disk, the Master / Slave is not important when it comes to performance anyway.  

I hope this helps
--Ian

---

### Post by JNowka on 2006-05-21
If you format the windows drive, wouldn't you be touching the MBR just a little bit?

---

### Post by Harleen on 2006-05-21
No, the MBR isn't affected by formating the drive. Iball's solution is probably the best one. I recently tried to change a Linux HD from slave to master, but never got it running. For that to work, I changed the device names in /etc/fstab (from /dev/hdb to /dev/hda) and also in /etc/mtab (yes, I really had to do this to make grub happy). But on the next step I failed miserably: Reconfiguring grub. I did it already a couple of times after windows installations and was finally able to install it on the MBR, but it could never boot Linux. I probably could have figured out how to solve this, but since the computer was about to be given away and the new owner wanted to format it anyway I refused to put in any more work.

So even if I didn't have much success with it, I've still learned something: Do not change the device name of your Linux partition or you will lose a couple of hours in the desperate try to get it running again (or until you give up).

---

