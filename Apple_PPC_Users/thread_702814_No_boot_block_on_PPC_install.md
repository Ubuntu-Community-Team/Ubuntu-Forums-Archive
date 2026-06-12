---
title: "No boot block on PPC install"
date: 2008-02-20
forum: Apple PPC Users
---

### Post by ruru on 2008-02-20
I have just attempted an install of Xubuntu 7.10 on a Power Mac G5 but a boot block was never written.
The LiveCD works fine and I used gparted to resize my OSX partition (HFS non-journaled) (Disk utility didn't want to cooperate here), then the install appeared to be fine until the very end when I got a message about not being able to find an Apple New World Boot Block.
The machine still boots fine into the resized HFS partition (running Tiger), but there appears to be no way to boot into the linux partition.

That's where my understanding ends! Is it possible to add/modify a boot block, or boot from a CD without doing a new full install? Does anyone know why this didn't work?

---

### Post by stream303 on 2008-02-21
What I'd do is boot with the install disk into "rescue" mode and try mounting one of the ubuntu partitions, ie sda3, sda4, sda5, sdb3 sdb4, sdb5 etc (don't know how you are partitioned so when prompted you can try these)

Take a look at your /etc/yaboot.conf file.  If the "device=" line looks like it contains an openfirmware path, then I'd issue these:

```
mkofboot -v
ybin -v
```

Or you can try the yabootconfig utility and see if that works.

Note that I don't dual-boot anymore, and always be prepared with original OSX install disks if it all goes haywire.  Just being honest. :)

---

### Post by ruru on 2008-02-21
Thanks for the reply...

> Take a look at your /etc/yaboot.conf file
There is no such file - I guess this confirms that a new boot block was never written.

I'll just do some googling to try to get up to speed on how yaboot works (I only get about an hour a night to work on this)...

---

### Post by ruru on 2008-02-22
OK, here's what I did last night...
I reinstalled xubuntu (over the previous install) using the alternate CD - ((formated partition to ext2 which I believe should give me write access from OSX)) - and hit the same error as before "no NewWorld boot block found".
This is where I got adventurous and simply set one of the two 'free' small partitions as a NewWorld Boot Block. I don't know why the partition I used was even there (I never created it!) but it was labeled as unassigned...
Now the install progresses fine and I have a functioning yaboot screen on startup and boots into xubuntu - great!
When I try booting into OSX though (from yaboot or open firmware) it won't work.

yaboot.conf seems OK and is set to use the correct OSX partition (not at that computer now, could post the file later today).

The OSX boot loader is obviously missing something it had before- but I don't understand what?

---

### Post by stream303 on 2008-02-22
I wrote a quickie manual partitioning guide that might help:

[http://ubuntuforums.org/showthread.php?t=322872](http://ubuntuforums.org/showthread.php?t=322872)

Most of the other threads are way more comprehensive than this, and the biggest issue for me back then was making the New World partition as bootable.

Can you get into OSX by holding down the ALT/Option key when booting?

---

### Post by ruru on 2008-02-22
>  Can you get into OSX by holding down the ALT/Option key when booting? 

No. The boot loader shows the apple screen, waits about a minute, then shows a 'no go' icon and the fans go mad. The same as if I try to boot from yaboot.

Unfortunately, as this is a work machine, a functioning osx install is essential. I am going to have one more try (I've not got heaps of time to dedicate to this issue sadly) and then Leopard will go onto the hard disc and I will investigate getting a new machine for my linux work...

---

### Post by stream303 on 2008-02-22
Ok, to get OSX recognized, have you tried booting the OSX installer disk, and instead of reinstalling, gone into disk-utility and made the OSX partition the "startup disk" ?

Now that I think about it, this might be the New World boot that the Ubuntu install is looking for so it won't have to create a new one on it's own in a dual-boot situation.....

Let's see if this gets your OSX back at least...

---

