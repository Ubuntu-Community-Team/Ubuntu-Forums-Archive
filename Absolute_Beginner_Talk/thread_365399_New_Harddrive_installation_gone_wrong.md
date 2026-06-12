---
title: "New Harddrive installation gone wrong"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Kasper42 on 2007-02-19
I was trying to install my new hard disk drive and followed [this guide]("https://help.ubuntu.com/community/InstallingANewHardDrive") I tried to reboot and on startup I get taken to a shell and the error message "/dev/hdb3:
Inode 834121 has illegal block(s)" It then goes on to tell me to run fsck manually. It also says fsck died with exit status 4. What do I do? Do I run fsck manually, how do I do this?

I was just wondering hdb3 is the partition with ubuntu installed on it and I was trying to install a new harddrive. I'm lost:( Please help!

---

### Post by petri on 2007-02-19
Well that happens time to time. I usually run **fsck -y** which means yes to questions but you may use only **fsck** right there at the prompt where you can read "...on to tell me to run fsck manually." 

If you have something important on that partition, you might back it up with LiveCD because you have to answer yes to questions and they sometimes moves or deletes some broken files. I have never had problem though, yet. :)

---

### Post by Kasper42 on 2007-02-19
A big thanks for the reply, Petri :) 

I did as you said, I didn't back up as I have a seperate partition with work/media. I rebooted and I am now faced with a different error.

> fsck.ext3: Bad magic number in super-block while trying to open /dev/hdd
/dev/hdd:
The superblock could not be read or does not describe a correct ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
   e2fsck -b 8193 <device>

fsck died with exit status 8

/dev/hdd is what I named the new partition and though it is a 300GB harddrive (279GB usuable) it displayed as 1.6Gb :confused: I can wipe this drive as i has nothing saved on it yet.

Thanks in advance :)

---

### Post by petri on 2007-02-19
I found similar thread, I have never had this kind of problem so I really don't know. I hope you find an answer here: [http://ubuntuforums.org/showthread.php?t=365251&highlight=e2fsck](http://ubuntuforums.org/showthread.php?t=365251&highlight=e2fsck)

---

### Post by Drakkor on 2007-02-19
> /dev/hdd is what I named the new partition
Isn't that already utilized ?  In my system /dev/hdd is the DVDRW/CDRW optical removable drive ! :confused:

---

### Post by petri on 2007-02-19
> **Drakkor said:**
> Isn't that already utilized ?  In my system /dev/hdd is the DVDRW/CDRW optical removable drive ! :confused:
... and in my DVDRW/CDRW is on /dev/hdb. It simply depends on where the DVDRW/CDRW is connected on the cable and motherboard.

---

### Post by Kasper42 on 2007-02-19
In the end, I ran > sudo mke2fs -j /dev/hdd which sorted the drive out. Then I ran  > sudo tune2fs -m 1 /dev/hdd to make the reserved files smaller and rebooted crossing my fingers. Thankfully, it worked well and I was relieved to see the gui!

GParted had seemed to corrupt the drive in some way. It was probably my fault but I have no idea how I caused this, as I've used GParted before and it's a great piece of software.

Thanks for helping me !:)

---

