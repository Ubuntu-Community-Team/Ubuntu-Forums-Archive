---
title: "PMagic Partition, weird thing happened!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-21
I leave my computer running because I am doing some partitioning stuffs. I know before I left my computer, it has jobs, resizing it's partitions, so I slept for more than 5 hours.

After waking up, I checked it out immediately and was shocked with the results, as if nothing happened.:( 

I badly needed some free space, because I think Ubuntu runs slow, and unstable because of I only have less than 2 gb of free space...:confused: my swap is 2GB though..

**Partitioning:**

[[IMG]http://img251.imageshack.us/img251/2250/partedmagic21feb152419ip7.th.jpg[/IMG]](http://img251.imageshack.us/my.php?image=partedmagic21feb152419ip7.jpg)

[[IMG]http://img139.imageshack.us/img139/3260/partedmagic21feb152527oj6.th.jpg[/IMG]](http://img139.imageshack.us/my.php?image=partedmagic21feb152527oj6.jpg)

[[IMG]http://img99.imageshack.us/img99/865/partedmagic21feb152634ud6.th.jpg[/IMG]](http://img99.imageshack.us/my.php?image=partedmagic21feb152634ud6.jpg)

[[IMG]http://img227.imageshack.us/img227/4044/partedmagic21feb152713st5.th.jpg[/IMG]](http://img227.imageshack.us/my.php?image=partedmagic21feb152713st5.jpg)

**After patitioning:**

[[IMG]http://img223.imageshack.us/img223/3438/partedmagic21feb232026yz4.th.jpg[/IMG]](http://img223.imageshack.us/my.php?image=partedmagic21feb232026yz4.jpg)

**After booting up:**

[[IMG]http://img126.imageshack.us/img126/9616/partitionresultsgo0.th.jpg[/IMG]](http://img126.imageshack.us/my.php?image=partitionresultsgo0.jpg)

---

### Post by Duck2006 on 2008-02-21
Did you try doing it one step at a time?

---

### Post by metallicamaster3 on 2008-02-21
Try using GParted/GNOME Partition editor instead. There is a LiveCD available [here.]("http://gparted.sourceforge.net/livecd.php")

I would suggest using the LiveCD instead of running it under an installed OS, as it just works more often/better. This way, it's a CD/RAM trying to modify your disk, instead of your disk modifying your disk, which I've also found is a lot faster.

Try it, and see if that gives you any luck.

---

### Post by Duck2006 on 2008-02-21
> **metallicamaster3 said:**
> Try using GParted/GNOME Partition editor instead. There is a LiveCD available [here.]("http://gparted.sourceforge.net/livecd.php")

I would suggest using the LiveCD instead of running it under an installed OS, as it just works more often/better. This way, it's a CD/RAM trying to modify your disk, instead of your disk modifying your disk, which I've also found is a lot faster.

Try it, and see if that gives you any luck.

pmagic uses gparted to edit the partitions.

---

### Post by metallicamaster3 on 2008-02-21
Yes, but is it running from a booted disk? I was trying to emphasize the fact to try to use a LiveCD, not change the application he his using. 

Sorry for the confusion :)

---

### Post by karlo on 2008-02-21
> **metallicamaster3 said:**
> Try using GParted/GNOME Partition editor instead. There is a LiveCD available [here.]("http://gparted.sourceforge.net/livecd.php")

I would suggest using the LiveCD instead of running it under an installed OS, as it just works more often/better. This way, it's a CD/RAM trying to modify your disk, instead of your disk modifying your disk, which I've also found is a lot faster.

Try it, and see if that gives you any luck.

I've **[COLOR="Red"]TRIED[/COLOR]** **gParted** beforre, before I installed Ubuntu Linux...  Now I used pMagic ..

**Obviously** if you see the interface of my screenshots, you'll notice it's on a **live cd**..

---

### Post by karlo on 2008-02-21
here's my problem [http://ubuntuforums.org/showthread.php?t=703436](http://ubuntuforums.org/showthread.php?t=703436)

attached in this message is the support.htm file of pMagic.

take note, i am using a livecd...

[http://kinux.uni.cc/visparted_details.htm](http://kinux.uni.cc/visparted_details.htm)

---

### Post by metallicamaster3 on 2008-02-21
Ah, okay, so you are on a LiveCD then.

Sounds like your table is screwed up pretty good, all those errors...

A bit harsh, but starting over from scratch by setting a new disklabel might solve your issues with partitioning your disk.

---

### Post by metallicamaster3 on 2008-02-21
No need to get loud :S

1.) I did not know you tried gParted before
2.) The interface of your UI means nothing, really, there's so many skins out there, plus I've seen themes like that under linux plenty of times before.

Sorry, just trying to help :P

---

### Post by karlo on 2008-02-21
> **metallicamaster3 said:**
> Ah, okay, so you are on a LiveCD then.

Sounds like your table is screwed up pretty good, all those errors...

A bit harsh, but starting over from scratch by setting a new disklabel might solve your issues with partitioning your disk.

[http://kinux.uni.cc/visparted/](http://kinux.uni.cc/visparted/)

---

### Post by karlo on 2008-02-21
> **metallicamaster3 said:**
> No need to get loud :S

1.) I did not know you tried gParted before
2.) The interface of your UI means nothing, really, there's so many skins out there, plus I've seen themes like that under linux plenty of times before.

Sorry, just trying to help :P

Thanks for your concern, I am not against you or anything. I am going to post a new thread here, regarding my disappointment with ubuntu..:(

---

