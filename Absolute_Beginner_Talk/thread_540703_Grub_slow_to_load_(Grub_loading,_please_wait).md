---
title: "Grub slow to load (Grub loading, please wait)"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by gustavo :) on 2007-09-01
Hello.
I've got a problem with Grub and none of the threads I read gave me the solution.
When I boot the computer, after the mobo screen, I get
```

Grub Loading Stage 1.5

Grub Loading Please Wait

```
and then 15 seconds later, or more, it loads the menu, where I can choose the OS (Ubuntu or XP).
When I installed Ubuntu, there was no problem and everything was fast. I think this problem began after some update or something like that.
How to solve this?
Thanks.

---

### Post by ramjet_1953 on 2007-09-01
You could try downloading the [COLOR="Blue"]SUPERGRUB Disk[/COLOR] iso and burn it to a CD.

Then boot from the CD and get it to re-write GRUB.

Hopefully this will do the trick.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Don't forget that as it is an iso image to burn it as an iso and to [COLOR="Blue"]burn no faster than 4 X[/COLOR].

Regards,
Roger :cool:

---

### Post by asmoore82 on 2007-09-01
> **ramjet_1953 said:**
>  [COLOR="Blue"]burn no faster than 4 X[/COLOR].

that's nonsense.

we have checksums to verify the data so burn it full out and verify.
you will rarely have a burning issue on GNU/Linux systems.

---

### Post by ramjet_1953 on 2007-09-01
OK, asmoore82, seeing you are the expert.

It is interesting that the forums are full of tales of woe, from those who have tried to burn iso images at high speeds.

Yes, you can get away with it, but more often than not, many people end up with a coaster.

Regards,
Roger 8-)

---

### Post by ningall on 2008-02-13
I have this same problem 

Did the superGRUB disk fix it?

or is there another solution to this?

---

### Post by articpenguin on 2008-02-13
> **ningall said:**
> I have this same problem 

Did the superGRUB disk fix it?

or is there another solution to this?


are you using reiserfs? that is a cause for grub to load forever as reiserfs takes around 10-20 secs to mount.

---

### Post by ningall on 2008-02-14
No im not

here is my partitions in order

RECOVERY FAT16 (From manufacturer)
WINXP PRO NTFS 
UBUNTU EXT3

no in my menu.lst i have commented out my recovery partition and the memtest options and still no speed increase

I also do not mount my recovery as default as i dont use it to store files 

My winxp does auto mount as i need file access to it on ubuntu

any help would be appreciated

---

### Post by thinkdez on 2008-04-07
I just ran into this problem when I changed my OS disk on my home server.  After working on the problem a bit I discovered that this issue was not due Ubuntu or Grub in any way.  It turns out that the issue was with the Hard Drive I was using.  I was using a Western Digital Hard Drive and it would seem that they have three settings on them for the jumpers, one of which wasn't listed on the drive itself.

```

MODE - Jumper Settings - Description
Single    |::|    Drive by itself
Master    ||::    Master Drive with a Slave
Slave     ::||    Slave Drive

| - Jumper connected [ON]
: - Jumper disconnected [OFF]

```

Turns out that if in Master mode the system [even in the POST stage] would look for the slave disk.  Once I added a second disk or put the drive into Single mode the system responded quite quickly.

I am using a WD273AB and the jumper settings are for this drive.  Consult the manufacturer for to make sure your jumper settings are correct.

Hope this helps others

---

