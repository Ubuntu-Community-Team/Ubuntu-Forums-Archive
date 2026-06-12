---
title: "I didn't read anything...and I'm worried"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by redvolvodavid on 2008-04-01
Alright...lets get out of the way that I'm an idiot and just jumped the gun on the Ubuntu install.  Its very stupid, I know, but I was just fooling around on the computer today and thought why not.

Anyway-
[LIST]
[*]I've installed on my Vista machine running Home Premium.
[*]Like a fool, I assumed without reading that because of the way I installed, I would have a dual boot option automatically-not the case. 
[*]I've looked for an answer-but found that the way for this to work would be DURING installation, not after.
[*]As far as I know...my windows files are still on the disk somewhere.  I popped the HD in an external enclosure-but wasn't able to open it to pull my files off.  I just didn't see the volume.  On my mac I saw the volume (containing my windows partition) but wasn't able to do anything to it.
[/LIST]
Luckily its my work computer and I don't care about all the work, wait-I do.  In fact, I'm in a bit of a panic mode.  

Any help, whether pointing me towards a link that helps-or your own advice-would be GREATLY appreciated.

I'm an idiot!
Thank You in advance (hopefully)!

---

### Post by liquidfunk on 2008-04-01
When you boot up are you able to choose Windows or Ubuntu?

---

### Post by bodhi.zazen on 2008-04-01
First of all, STOP running from the hard drive for a minute.

Boot the Ubuntu CD, open a terminal, and post the output of :

```
sudo fdisk -l
```

That will list your partitions. If you know which is vista we can mount it and take a look. From there we can determine if it is a matter of configuration (configure grub to dual boot) or data recovery (you installed Ubuntu on top of vista).

---

### Post by Doorslammer on 2008-04-01
```
 fdisk -l 
```
fdisk -l. Lists the partitions on all available hard disks
fdisk -l  thats an L not an i

post the out put



edit man your fast :)

---

### Post by redvolvodavid on 2008-04-01
/dev/sda1  1   10328   82959628+   83   Linux
/dev/sda2  38166   38913   6008310   5   Extended
/dev/sda3 * 10329   38165   223600702+   83   Linux
/dev/sda5 38540   38913   3004123+   82   Linux swap/Solaris
/dev/sda6   38166   38539   3004092   82   Linux swap/Solaris

My guess is that I installed over the vista from the looks of this...

THANKS!!!

---

### Post by nachomania on 2008-04-01
Welcome...under my same circumstances...!

---

### Post by bodhi.zazen on 2008-04-01
Looks that way to me too.

You can try recovery tools such as testdisk or photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Partial recovery may be possible, you may be able to do it from the Ubutu Live CD as I believe both apps are in the repos.

---

