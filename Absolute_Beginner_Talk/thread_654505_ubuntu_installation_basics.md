---
title: "ubuntu installation basics"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-12-31
I have learned from this site many things about installing and running Ubuntu, but I need to ask something about start up partitioning basics.
 When I first put Ubuntu on my machine, all I had was Ubuntu on the main partition and a 500 mg swap file. Lately I added a 11 gig home partition besides swap and /. Is there another partition I should have as well, or will these three do for me?

---

### Post by mikewhatever on 2007-12-31
Yes, they should. Given it is so easy to backup the home, I don't really see the need to make it a separate partition.

---

### Post by laidback on 2007-12-31
I've been running 6.04,6.10 and 7.04 with just / and swap. ~./home is within my /root partition and it's been just fine, even for upgrading.

---

### Post by Cypher on 2007-12-31
Having a /, /usr, /home and SWAP should largley suffice for most people. The nice thing about location /home and your user directory in it's own partition means that you can backup your data quickly without having to worry about Ubuntu files.

Additionally, when you upgrade you can have the installer just avoid formatting the /home partition and you get to retain all your information while enjoying the newer version of Linux..

But, the bottom line is that there is no golden rule about partitioning, a lot of it is from people's personal experiences. 

At one point in time, I used to create a /, /boot, /usr, /tmp, /var, /home and SWAP. As you can imagine making sure each of the partitions have enough space becomes quick tricky and it's a pain if suddenly you realize you're out of space on one partition..

---

### Post by LowSky on 2007-12-31
A hard drive can only have 4 primary partitions. So if you want to install more than one operating system it good to create an Extended partition.

---

### Post by meindian523 on 2007-12-31
Why do you need a /usr?A simple du command shows that it's not worth making the HDD more fragmented just to have a separate partition for /usr.

---

### Post by pdlethbridge on 2008-01-01
thanks for all the input, as this is all new to me the last few months.
Now a few more questions on the same subject.
What are the advantages of creating a usr or temp partition?
why the boot and var?
If you only have ubuntu, what would be the best use of an 80 gig hd?

---

### Post by eternicode on 2008-01-01
One of the main advantages to making separate partitions (for /home and /tmp, at least) are so that the users can't fill the drive with their files, and leave the OS with no room to work with.

With the /tmp, you could also mount it with the noexec option, making that dir a little safer.

I'm guessing the advantages of a /boot partition may be read times (depending on the fs), and the ability to mount it read-only.

/var would have the same reasons as /tmp, but really only for server environments.

Not sure about /usr

-----

Most users could just use a swap space as big as the amount of RAM they have, and give the rest to a normal root partition.

If you insist on having a /home partition, give / (root) about 6-8GB, and the rest for /home.

Depends entirely on how the system is used, though ;)

---

### Post by pdlethbridge on 2008-01-02
The system is a single non networked computer that is used for web serving and collecting train photos, mostly steam. I would like to keep all my photos save and seperate from my OS.

---

### Post by meindian523 on 2008-01-02
The it's preferable to use a /home partition.

---

### Post by pdlethbridge on 2008-01-03
I changed how I have my file system, but I'd like to correct it. here's a screen shot of gparted I want my home to get that extra space, 55 gig. How do I do it without loosing my home files?
[IMG]http://i167.photobucket.com/albums/u134/pdleth/snapshot1.png[/IMG]

---

### Post by eternicode on 2008-01-03
You will have to boot to a live environment before you can modify your home partition.  If you have it, the Ubuntu LiveCD should already have GParted.

What data is on sda4?  If there's nothing on it (or if the data can be moved to your /home or / partitions):

0) Move the data, if any, to the appropriate place
1) Delete sda4
2) Move sda2 all the way to the left
3) Resize sda2 to the right to fill the extra space.

If you want to leave the data on sda4 untouched:

1) resize sda4 from the right; give it at least 8MiB of free space (use the mouse to drag the right-hand side all the way to the left, then add 8MiB to the "New Size")
2) Move sda2 all the way to the left.
3) Resize sda2 to the right to fill  the unallocated space.

---

### Post by pdlethbridge on 2008-01-04
tried and failed, I'm enjoying my fresh install with / as a 70 gig, oh well. Better luck next time. The only way I can do this would be to copy everything in /home to another drive, then do a total format and resize on the drive.

---

### Post by meindian523 on 2008-01-04
Not exactly,you can use this:

[Separate /home on a already-installed Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by hyper_ch on 2008-01-04
well, if you want to install mutliple distros then I'd suggest using a seperate /boot partition also.

---

### Post by meindian523 on 2008-01-04
But how does that matter?The ways to multi-boot several distros are:
1]Chainload Grub
2]Add the relevant entries to the master Grub.

How does having a separate /boot help in any of those cases?Please don't take this as refuting or disputing your point,but I would like to know(gain a little more knowledge) whether there is a valid case for separate /boot.

---

