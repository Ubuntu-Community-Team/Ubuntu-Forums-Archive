---
title: "my server is broken :("
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-04-07
I had a power outage and now when i boot my server it says

```
mount point /dev/shm does not exist
mount point /dev/pts does not exist

```

```
the device node for the root filesystem is missing or incorrect or there is no entry for the root filesystem listed in /etc/fstab
```

then it starts a maintenance shell and when i try to edit /etc/fstab with vim i get

```
command 'vim' is located at /usr/bin/vim

/usr/bin is not included in the path environment variables
```

---

### Post by The Cog on 2008-04-07
I would be inclined to use a live CD (perhaps the desktop installer CD would do), mount the hard disk root partition and use the editors from the live CD to edit what broken files you can find. The first one to go for is /etc/fstab.

---

### Post by e1ektrob0y on 2008-04-07
it has no cd drive :( but i plugged the hard drive into my main pc and edited /etc/fstab. Now it starts up but hangs at 
```
*running local boots scripts /etc/rc.local
```

??

---

### Post by Joeb454 on 2008-04-07
Try hitting enter after a few minutes, I've had to do that before :p

---

### Post by e1ektrob0y on 2008-04-08
> **Joeb454 said:**
> Try hitting enter after a few minutes, I've had to do that before :p

Nope :( that just starts a new line and nothing happens...Can anyone help pleeeeease!

---

### Post by njparton on 2008-04-08
It looks like you had an unclean shutdown so your disk is all messed up. I think you need to run fsck on it to see if anything can be recovered, else it's a reinstall.
 
What filesystem was it running, ext3?
 
I've never used fsck myself so you'll have to do some searching about it.

---

### Post by njparton on 2008-04-08
Just stumbled across some fsck advice in this thread:
 
[http://ubuntuforums.org/showthread.php?t=748287](http://ubuntuforums.org/showthread.php?t=748287)

---

### Post by e1ektrob0y on 2008-04-08
> **njparton said:**
> Just stumbled across some fsck advice in this thread:
 
[http://ubuntuforums.org/showthread.php?t=748287](http://ubuntuforums.org/showthread.php?t=748287)

Thanks. I followed that and it still doesn't work :( e2fsck found heaps of bad blocks and deleted them but the same thing every time...I can run a maintenance shell as root and access the hard drive now. I can run vim and edit files but still i can't fix it :(

---

### Post by njparton on 2008-04-08
It could be too far gone.  Is there data stored on there that you need to retrieve?
 
If not it may be quicker just to re-install.

---

