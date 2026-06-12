---
title: "AHHH, I have partitioned my HD like crazy... HELP"
date: 2006-06-26
forum: Apple PPC Users
---

### Post by miikkee on 2006-06-26
Hi, 

I have a PowerBook G4 1.5 GHz. I reshrinked my 80 GB hardrive to 60 GB with parted. This was Ok. But after I made several attempts to install Ubuntu and I have like 5 or 6 partitions on the remaining 20 GB. (I first installed the server version which did not work and after tried to reinstall with live CD, and created a huge partition mess)

I still want to install ubuntu on those 20 GB. But It looks like a mess now. Can I get rid of partitions?????

Ideally, I would like to keep my 60 GB partition with all my MAC data + a 20 GB free space for the ubuntu installation. 

Sorry for the trouble... And Thanks for the help... 

Miikkee

---

### Post by glotz on 2006-06-26
The installer can add and remove partitions. Don't remove your mac partition by mistake...

---

### Post by miikkee on 2006-06-26
Ok thanks, the installer helped me...

---

### Post by macgig on 2006-07-11
im a total linux newbie, and my first install attempt, I made 3 partitions on the linux drive. dont ask me how. lol. guess I was buzzing through the install menus fast and didnt see it. LOL](*,) 

it pays to go slow and read, pay attention :mrgreen:

---

### Post by namaui on 2006-07-11
I am not new to linux but have never set up a Dual-Boot situation with Mac OS X and Linux. I am using a very old iMac. It is a Revision D machine, tray loading, 333mhz, 160MB ram and 80 GB Hard Drive split up like this:

HFS+ Macintosh HD 7.61 GB
HFS+ Extra OS X Partition 44.8 GB
Mixed filesystems used by Ubuntu in a 21.3 GB

When re-installing OS X 10.3.9 on this machine I made 3 partitions 2 HFS+ drives and 1, 21.3 GB free space that I auto-partitioned in the Ubuntu 5.10 Installation CD with the default partitioner. It finished copying all the installation packages and restarted, but on restart I got a grey screen with the text "Can't Open" over and over again. Even Zapping the pram didnt do much. I had to reboot off the OS X install CD and select "Macintosh HD" as the boot drive in Startup Disk, then that finally did it, but i cant get back to my ubuntu boot partion which i believe is #11 for yaboot on the list. Can any provide any info as how to set up an easy dual boot setup, somewhat like grub? Just incase you dont know, even though apple has this machine listed as NewWorld, it is very similar to the beige g3 in the fact that it cant use the option key to select a boot drive at startup, or use the L or X cds to choose.

Thanks, Nick

---

### Post by 3rdalbum on 2006-07-13
It's possibly a long-shot, but try booting your computer with Command-Option-O-F held down. At the prompt, type:

```
boot hd:2,yaboot
```

If that doesn't work, try increasing that number until it works. (on my iMac, the magic number is 6)

---

### Post by suloku on 2006-07-13
Aren't this partitiones "/", "/home" and "swap"?

If they are ubuntu auto partitioned your hardisk the best way you can aprtition a linux hardisk.

Well, in my case I have a 965 mb swap partition but I'm almost never needing it with 2 gb of ram...

---

