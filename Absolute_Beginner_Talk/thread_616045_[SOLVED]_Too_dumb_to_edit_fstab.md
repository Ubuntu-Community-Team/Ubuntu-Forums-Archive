---
title: "[SOLVED] Too dumb to edit fstab"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by justsomedude on 2007-11-17
So, I created a new ext3 partition (/dev/sda7).

I want to automount it on startup.

However, if I add 

```
UUID=8c37eb3c-749f-4147-b2f2-6d7a92346e1c	/media/sda7	ext3	defaults	0	0
```

or

```
/dev/sda7	/media/sda7	ext3	defaults	0	0
```

to /etc/fstab, it refuses to mount. It just laughs at my face... :(

---

### Post by conjur3r on 2007-11-17
So what error messages do you get?  Try manually mounting and then copy/paste the error message here:

# sudo mount -t ext3 /dev/sda7 /media/sda7

---

### Post by Duck2006 on 2007-11-17
This may help

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by logos34 on 2007-11-17
Maybe you forgot to create a mountpoint?

sudo mkdir /media/sda7

---

### Post by justsomedude on 2007-11-17
Thank you for your help conjur3r, much appreciated. :) I get 

```
sudo mount -t ext3 /dev/sda7 /media/sda7
Password:
mount: mount point /media/sda7 does not exist

```

I thought it would create a mount point automatically if I add the partition to /etc/fstab.

I create a mount point now and see if it helps...

---

### Post by conjur3r on 2007-11-17
There it is.  I assume you've fixed it :)

Nah it doesn't.  Live and learn hey :)

---

### Post by justsomedude on 2007-11-17
Thank you conjur3r, Duck2006 and logos34, you guys are awesome.

Creating a mount point of course did the trick, I feel slightly dumb now...

---

### Post by whazooo on 2007-11-17
> **justsomedude said:**
> 

Creating a mount point of course did the trick, I feel slightly dumb now...

You should instead feel slightly smarter
I know I do.. 
Thanks for this thread

---

