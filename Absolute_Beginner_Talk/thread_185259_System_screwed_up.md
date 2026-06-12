---
title: "System screwed up"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-05-31
Hi,

I tried to install Gentoo over my ubuntu just to test it. But I'm waaaay to noob for gentoo so I kind of messed up my computer.
When I start up I get some weird colours and whatever I do it keeps rebooting ...
My windows partition of 150 GB is still there but how can i get that back ???
So, how can I boot into MS ??

Btw :: Gentoo wasn't completely installed, I just rebooted my system during the install cause I didn't understand anything of it ;)

Grtz PingunZ

---

### Post by glotz on 2006-05-31
Insert windows disk and run mbr on the disk, it'll overwrite the master boot record and then windows will work again.

BTW, in your firefox speed up guide you recommend setting network.http.pipelining.maxrequests to 30, however the maximum for that setting is 8. See [http://kb.mozillazine.org/Network.http.pipelining.maxrequests](http://kb.mozillazine.org/Network.http.pipelining.maxrequests)

---

### Post by PingunZ on 2006-05-31
And how do I go in that mbr ???
BTW :: I'll change it, TY ;)

Grtz PingunZ

---

### Post by PingunZ on 2006-05-31
So I boot up my cd :
- Install Windows
- Repair Broken System 

??

Grtz PingunZ

---

### Post by glotz on 2006-05-31
Sorry, can't remember exactly. Been so long on Ubuntu. Googling produces this

[quote="[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)"]you can boot from startup floppy disks or CD-ROM, choose repair option during setup, and run Recovery Console. When you are logged on, you can run FIXMBR command to fix MBR.[/quote]

---

### Post by PingunZ on 2006-05-31
It works, to bad MS already formatted my hdd :s
But Thanks anyway ;)

Grtz PingunZ

---

### Post by Dr. Nick on 2006-05-31
[quote=PingunZ]It works, to bad MS already formatted my hdd :s
But Thanks anyway ;)

Grtz PingunZ[/quote] 
For future refrence If you boot a XP Cd then it should ask before the install wether you want to repair your installation from a recovery console. Choose yes then it is "fixboot" or "fixmbr" one of them 2 should get your mbr back to windows only.

Of course formating and reinstalling works aswell

---

### Post by user1397 on 2006-05-31
On a side not, you should research more on big subjects, like installing gentoo, because you might have succesfully installed it, and none of this would've happened.  Installing OS's is an involving and dangerous process, especially if you don't know what you're doing, and if you don't back-up.  Just my suggestion, that's all.  This is not criticism of any kind.

---

