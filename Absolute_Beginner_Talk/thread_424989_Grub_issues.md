---
title: "Grub issues"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-04-27
I ran a search to see if this was posted already, so sorry if it is.

I installed Ubuntu 7.04 to my Dell Latitude D620 laptop and it worked fine for a while, but when I booted into Windows XP and then restarted, I couldn't boot into anything.  I think it's because Windows writes over the MBR.  I used a rescue cd to boot back into Windows, but it won't let me boot into Linux.  I'm almost positive that if I put Grub on the same partition as Ubuntu that I could use GAG to boot into both Ubuntu or Windows XP.  I have no idea how to install Grub though, I have an ISO of Ubuntu that I downloaded and could probably install Grub from that, but I don't know how to tell Grub to install to the same partition as Ubuntu, can any one help?

I know the easy alternative would be to delete windows but my laptop was provided by my college so I can't.

---

### Post by swamytk on 2007-04-27
You are right! You boot the system with your Ubuntu CD. You can ask grub to install grub with root directory as Ubuntu root. For that,
1.Boot with Ubuntu CD.
2. Go to command line.
3. Mount your existing Ubuntu installation root partition in a temp directory. (e.g):
$ sudo mount /dev/sda2 /mnt/tmp
4. Check /mnt/tmp/boot/grub/menu.lst and ensure that both ubuntu and Windows entries are in tact.
5. Run grub to update the MBR (e.g.):
$ sudo grub-install --root-directory=/mnt/tmp /dev/sda
6. Reboot the system

---

### Post by riminicat on 2007-04-27
Thanks, I'm new to the Linux world and have no idea how any thing works, your step by step instructions help.  When I update the MBR, will GAG still be my boot loader?

---

### Post by riminicat on 2007-04-27
Hey one more question, what command would I use to find out what partition Ubuntu is on, because once I find that out, I should be able to tell Grub to install to that partition.

---

### Post by swamytk on 2007-04-27
Once you follow this procedure, still you will have Grub as your bootloader. It will be exactly same as that of what ubuntu installation wizard did.
Regarding which partition you installed ubuntu (you are supposed to remember it.. no problem.. ) here is how it is:
Primary Master first partition: /dev/sda1, second partition: /dev/sda2....
Primary Slave first partition: /dev/sdb1, second partition: /dev/sdb2....
Secondary Master first partition: /dev/sdc1, second partition: /dev/sdc2....
Secondary Slave first partition: /dev/sdd1, second partition: /dev/sdd2....

---

### Post by laidback on 2007-04-27
This is worth a read:-
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and for grub manual

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by riminicat on 2007-04-27
Awsome, thank you

---

### Post by riminicat on 2007-04-27
Hey thanks for the help

---

### Post by darkworld on 2007-04-27
Hey I think you may have an answer to a problem I have. Could you confirm im right.

I have Kubuntu dapper installed and xp dual boot from Grub? menu.

I need to test a usb linux flash drive but bios only supports USB-FDD boot, also my pc floppy drive is dead, so floppy boot image is out.

From what has been said above I get the impression I could boot the stick from command line grub. Am I right?

---

### Post by riminicat on 2007-04-27
I have an idea!! Please forgive me for being ignorant.

grub> find /boot/grub/stage1

I run this to find out where grub is installed, it should tell me that grub is installed to the MBR, but will also tell me what partition it is on, which is where Ubuntu will be.

grub> root 

I put what ever I want Grub to install from (for example hd0,1)

grub> setup (hd0)

I replace (hdo) with the partition I want grub to install to, in my case, the partition that contains linux.

I think this will work

---

### Post by riminicat on 2007-04-27
darkworld-
that should work, but some BIOS's wont allow booting from USB drives, so make sure you configure your BIOS to check USB drives, you can usually do this by hitting the F2 button when your computer starts.  You should then be able to tell Grub to load from your USB

---

### Post by medya on 2007-04-27
this should help you [recover your grub easily ]("http://blog.shevin.info/2007/04/messed-up-boot-loader-dont-worry.html")

---

### Post by riminicat on 2007-04-27
Yes it helped.  One question, I take it at the end where it says "setup (hd0)" The hd0 is the MBR, so, if I want to install the Grub menu to the ubuntu drive, can I put in "setup (hd1,3)"?

---

### Post by riminicat on 2007-04-27
Does any one else know if this will work?

---

### Post by dstew on 2007-04-27
Before grub is installed as the boot loader, the files stage1 and stage2 are in the /boot/grub directory of your linux file system. The grub stage1 file is the skeleton of the booter that will eventually go into the MBR. The installation process puts into the stage1 skeleton the information on where grub will find stage2, and its menu, and merges it with the partition table, and puts all that into the MBR.

When you begin to install grub, the first command **root (hd0,1)** is telling grub where it will find its stage1 skeleton, stage2, and its menu. The command setup (hd0) tells grub to make the final assembly of the stage1 and put it into the MBR.

The MBR is not part of any partition, nor of any file system, so there is no file named "stage1" in the MBR once grub is installed. The installation process puts into the stage1 skeleton the information on where grub will find stage2, and its menu, and merges it with the partition table, and puts all that into the MBR.

---

### Post by riminicat on 2007-04-27
Hey thanks, I got it all worked out, windows wouldn't stop rewriting over Grub so I put grub on the same partition as Ubuntu, and then put Gag in the MBR, it worked!

---

