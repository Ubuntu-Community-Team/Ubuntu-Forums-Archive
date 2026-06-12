---
title: "[SOLVED] Slow Ubuntu booting"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by moeness86 on 2008-03-09
My Lenovo 3000 N200 boots rather slowly now .. a friend of mine told me that this was because it checked the file systems every time , and  i do see the fsck step during the boot and that it does stay for a long period..

solutions, plz ?

---

### Post by jken146 on 2008-03-09
fsck only happens every ~30 boots, so it shouldn't be an issue most of the time.

---

### Post by moeness86 on 2008-03-09
it doesnt do the one with the line of equal signs "==============" except every 30 times or so yes

but even though it doesnt do it , it is sooo slow and that is what i get

---

### Post by Rocket2DMn on 2008-03-09
I'm not sure about your fsck problem, but here is a great way to speed up your boot.  It "reprofiles" your boot sequence so it can memorize some stuff for future boots: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by Tatty on 2008-03-09
how slow is it?

try installing bootchart:

```
sudo apt-get install bootchart
```

Reboot your machine, when it loads it will analise how long it is taking to complete each part of the boot...  it will save a bootchart at /var/log/bootchart

Please post this so we can see if there are any specific problems during boot.

---

### Post by moeness86 on 2008-03-09
here is the link to the bootchart pic:

[http://upl.zorpia.com/org/0/4162/26640898.8e06e1.png](http://upl.zorpia.com/org/0/4162/26640898.8e06e1.png)

---

### Post by Tatty on 2008-03-09
Yes it does look like there is some problem with fsck running there... you say this happens every single boot?
It should not be doing that.

[http://ubuntuforums.org/showthread.php?t=300477]("http://ubuntuforums.org/showthread.php?t=300477")

This thread tells you how to change the number of boots before a new fsck check.  Try using this to change the number of boots to something like 30 or 50, then see if it still fscks on boot.

---

### Post by moeness86 on 2008-03-28
sorry i couldnt respond fast ..
it still checks them :(
what do i do now ? is there any other option to change in fsck ?

---

### Post by CazperII on 2008-03-29
You can adjust many parameters with tune2fs.

e.g:
```

sudo tune2fs -c 60 /dev/sda1
```

With this command fsck will check the filesystem every 60 times /dev/sda1 is mounted.

For more options look at the manpage:

```
man tune2fs
```

---

### Post by moeness86 on 2008-04-12
Thank a lot
I tried that and this is what I get :

tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.


it might help that i say that i dual boot gutsy with windows XP SP2

---

### Post by CazperII on 2008-04-12
You can only alter the Linux-partitions, in most systems the first partition (/dev/sda1) is the windows partition. Type in this command:

```
df -h
```

and look which partition has / mounted on it.

So the command to alter the number of boots before a file check of the partition,  will look like this:

```
sudo tune2fs -c 60 /dev/sda**X**
```

with X being the partion number.

If you have  multiple linux partitions (e.g. for data) you should alter them too.

---

### Post by moeness86 on 2008-04-14
Problem Fixed !!
Turend out that most probably my windows partition did have a problem
I reinstalled windows and fixed grub back with super grub CD and now all is well
Thank you very much

---

