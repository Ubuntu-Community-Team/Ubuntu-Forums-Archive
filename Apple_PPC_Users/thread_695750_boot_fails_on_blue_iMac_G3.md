---
title: "boot fails on blue iMac G3"
date: 2008-02-13
forum: Apple PPC Users
---

### Post by pspspeed on 2008-02-13
Well i have an iMac G3 333 160 ram and i just installed ubuntu 6.10 on it with the alternate install disc. I just put a 40gb hard drive in it and installed MacOs 9.2 just fine so i know everything is hooked up fine. after ubuntu install reboots, yaboot loads with an error, here it is...

```
Please wait, loading kernel...
/pci@80000000/mac-io@10/ide@20000/disk@0:3,/boot/vmlinux: Input/output error
boot:
```

 Thats what it does, and i'm not dual booting, but i did try dual booting beforethat and got the same result.

---

### Post by pspspeed on 2008-02-13
Is there something i need to edit in the yaboot.conf? But if i do how can I when i can't get it to boot into linux at all. Can it be done through the install cd? Please Help!!!

---

### Post by stream303 on 2008-02-13
I wonder if you are running into the old 8GB limitation for that machine?

[http://ubuntuforums.org/showthread.php?t=108266&highlight=imac+333](http://ubuntuforums.org/showthread.php?t=108266&highlight=imac+333)

(Thanks OswaldKelso)

If so, you might want to manually partition it so that Ubuntu doesn't go past 8gb and leave the rest free, or make them just data partitions.

Since you have OS9 running, you may want to take a peek at the Apple firmware updates for that box:

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

To get to yaboot.conf, you can boot from an install disk and enter rescue mode.  If it is an "alternate" installer, you can type

```
Linux single
```

at the boot: prompt, and get to it that way.

---

### Post by pspspeed on 2008-02-13
Thanks man, I didn't even think about putting it all in the first 8 gigs. I thought it could start in it and extend as far as you want. I'll try some of it and let you know.

---

### Post by pspspeed on 2008-02-13
I tried that before and it didn't work but that was something to do with dualbooting. I put just ubuntu in the 1st 8 gigs and it worked. You rock man!!!

---

### Post by stream303 on 2008-02-13
Fantastic!  Thanks to oswaldkelso!

While we're on a brand new hd, you may want to consider the addition of at least noatime to  your /etc/fstab

It's not critical, but might be worth considering:

[http://ubuntuforums.org/showthread.php?t=692318](http://ubuntuforums.org/showthread.php?t=692318)

---

### Post by pspspeed on 2008-02-13
What exactly is noatime. Does it speed loading of some things or what exactly does it do? And you just add that option to fstab or what? I read that post but I couldn't make much of it.

---

### Post by stream303 on 2008-02-14
Linus' argument was that for the average desktop user, having the system write timestamps to each file that it only needs to read from, is a waste of hard drive speed and unecessary wear and tear.

Old-school programs such as mailers used to rely on this timestamp to let you know when you had new mail, etc, but may be irrelevant these days.  I suppose it is a great idea for ultra-security when utilities need to know what time a file was actually read, but for us, it might not be needed.

I would think that cutting down on wear and tear on hard drives, especially those of us with older drives in our PPC's might find using noatime in /etc/fstab on our ext3 partitions useful.

For me, so far so good!

---

