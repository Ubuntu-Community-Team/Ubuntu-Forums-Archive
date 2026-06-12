---
title: "Transfer music from windows to linux"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by khoda on 2006-09-06
Hey,

What's the best way for me to:

a) transfer the music from my windows partition to linux partition

b) allow both partitions to play my music (and/or videos)

---

### Post by electricshoes on 2006-09-06
Transfering from an NTFS partition to linux should be as easy as drag and drop or copy if your Windows partition is mounted in Ubuntu.

If all your music/videos are on your windows partition it shouldnt be a problem and you can see them from Ubuntu. Im not to sure if your music is on your linux partition, I dont think there is a good way to read linux partitions in windows.

Better yet you could have a seperate partition or drive to put all of you media on (ntfs or fat32) so that both ubuntu and windows will read it.

---

### Post by jaboit on 2006-09-07
> **electricshoes said:**
> Better yet you could have a seperate partition or drive to put all of you media on (ntfs or fat32) so that both ubuntu and windows will read it.

What kind of seperate partition would you need for OSX and Ubuntu? Or, to put it another way, would PPC Ubuntu read files on an hfs+ partition?

PS Sorry for the off topic

thanks!

---

### Post by electricshoes on 2006-09-07
If you want to read a partition or a seperate drive from Ubuntu, Windows and OSX, Fat32 is your best bet.

There is an hfsplus (mac native) driver for Linux, im not sure how well it works.

Fat32 i think would be best for read/write access from all 3 OS's

---

### Post by khoda on 2006-09-12
How do I mount the Windows partition in Ubuntu?

---

### Post by stmiller on 2006-09-12
[http://www.google.com/search?hl=en&q=how+to+mount+windows+partition+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=how+to+mount+windows+partition+linux&btnG=Google+Search)

[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

This is probably the most asked Linux question of the decade...

---

### Post by xyz on 2006-09-12
Also: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
*khoda* hope you'll figure it out using any of the links. It's true that a little searching never hurts esp. on such issues.
For instance, try typing "mount windows ubuntuforums.org" in Google!
You can substitue "mount windows" with anything you may be looking for.
It's just ONE of the ways to try and find your way aroung.

Quite late where I'm at...I'll go and try to...*/mount* my bed.
Signing off!

---

### Post by 3rdalbum on 2006-09-13
PPC Ubuntu can mount and read HFS and HFS Plus partitions.

---

