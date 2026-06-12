---
title: "grub error 18"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by usea on 2007-05-24
Hello, I'm getting a GRUB error 18 when I try to boot. I'm attempting to install ubuntu (feisty fawn) for the first time on a blank hard drive. Here are the system specs:

Soyo motherboard, SY-TISU
512mb of pc133 SDRAM (running at 100mhz)
Intel Celeron 1300
SBLive
It has a gigabit ethernet network adapter and a geforce FX series graphics card, but I'm not certain of their exact models.

As an aside, I've run memtest86 and verified the integrity of the live cd I'm using.

Once I get to the desktop, booting from the cd, I select the install option. During the install, I select a guided partition/format to encompass the entire disk. When the installation is done, it ejects the CD and asks me to hit enter to restart. I remove the cd and press enter. When the computer attempts to boot from the hard drive, I get the GRUB error 18.

I've searched these forums and found 2 threads on the topic, I also asked the question on irc and received some assistance but I haven't found a resolution yet. Some suggestions were that maybe the BIOS doesn't support a disk of the size I'm using. However, the disk is only 60gb and the bios supports up to 100gb. I've also looked for an LBA option in the bios, but there doesn't seem to be one. The bios does seem to detect the drive just fine though, and lists its size correctly. As far as I can tell, the partition starts at the beginning of the disk. I've typed "sudo fdisk -l" into a terminal and the output is:
```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7288    58540828+  83  Linux
/dev/sda2            7289        7476     1510110    5  Extended
/dev/sda5            7289        7476     1510078+  82  Linux swap / Solaris
```
I've tried some commands from the "howto: reinstall grub" topic, but grub can't seem to find the drives I specify. I've tried installing from the cd 3 times, all with the same result.

Any suggestions? I can't figure out what is wrong or what to do to get ubuntu running. I'm not ruling out that maybe the hard drive is bad, but the signs don't seem to be pointing in that directions. Also, I'm extremely new to linux. It took me a long time to just find the terminal, and I don't know any commands even a basic user might know. I didn't know whether I should reply to one of the other error 18 threads or make a new one. I ended up making a new one, I hope that is okay.

---

### Post by psusi on 2007-05-24
100MB is not a disk size that would or would not be supported by the bios, but if it does not support LBA, then it can't see beyond 8 GB.  You can try reinstalling grub from the livecd and asking it to force the use of lba by doing this:

sudo grub
root (hd0,0)
setup --force-lba (hd0)
exit

If that does not fix it and you can not find an option in your bios to enable lba, then you will have to set up a smaller /boot partition within the first 8 GB of the disk.

---

### Post by vtel57 on 2007-05-24
Hi usea! Welcome to the forum!

Please boot into a Live CD session with your Ubuntu disk. Once the session begins, open the Terminal and type this command:

```
 $ sudo mount /dev/sda1 /mnt
```

This command "mounts" the sda1 partition of the drive so we can check a few things. Now do the following:

```
 $ cd /mnt
```

This will change directory (cd) to the /mnt directory where we just mounted the sda1 partition. Let's look at your GRUB configuration file:

```
 $ sudo gedit /boot/grub/menu.lst
```

Please post a copy of the menu.lst file here, so we can give it a looksee.

Standing by...

---

### Post by usea on 2007-05-24
Somebody on irc earlier today asked me to pastebin the same menu.lst file to him. Strangely it didn't require me to mount anything (it must do it automatically?), I can see the full drive already from the desktop when I boot into ubuntu from the live cd. Here is the previous pastebin of /boot/grub/menu.lst [http://paste.ubuntu-nl.org/22364/](http://paste.ubuntu-nl.org/22364/)

psusui I typed the commands you suggested, it said that it was modifying menu.lst or whatever and appeared to process successfully. I didn't copy the output because it's a hassle relaying text from the computer in question to here. After doing it, I ejected the cd and restarted, but the error persisted.

As for the LBA  setting in the BIOS, I hadn't looked very hard previously because I didn't see it explicitly enabled or disabled anywhere, and it was listing the capacity of the disk as 61496mb so I assumed it was fine. In the interest of being thorough I just now checked, and each IDE device has an option for "access mode: CHS/LBA/Large/**Auto**" and "IDE Primary Master: None/Auto/**Manual**." Selected options in bold. I tried setting the access mode to LBA specifically, but the error persisted. I changed primary master to auto instead of manual, and the problem seems resolved. I don't know what manual did, because I didn't see any further options, and the listed cylinder, sector etc information didn't change. Regardless, the problem is gone now.

Thanks for your help. Without it I would be even more lost than I am already. :) Sorry for the dumb problem

---

### Post by vtel57 on 2007-05-24
COOL! Glad you got it working! :)

---

