---
title: "MacBook 3,1 Can't get hibernate to work"
date: 2010-07-07
forum: Apple Hardware Users
---

### Post by peterx14 on 2010-07-07
Hi all,

I've recently installed Ubuntu 10.04 (amd64) on my MacBook 3,1 (1GB memory). Most things work perfectly on install, and I've got the iSight working now too!

However, although suspend works fine, hibernate does not. When I try to hibernate, the screen goes blank with the back light on for a few seconds, then the screen goes off completely for about 0.1 of a scond and I hear the optical drive whirr (like it does when booting), and then about 4 or 5 seconds after that it finally powers off.

Then, when I restart, I see the rEFIt menu, then the GRUB menu and it appears to boot like normal and *not* resume from hibernate!

I'm not sure what log I should look in? When I look in /var/log/pm-suspend.log the last line says "performing hibernate", but there's nothing about even attempting to resume.

Any ideas?

Peter.

UPDATE: Forgot to mention, I have a swap partition that is larger than 1GB.

UPDATE 2: Also, after attempting to hibernate, when the system restarts, WiFi has been disabled -- I have to double-tap (right-click) on the WiFi icon and re-enable it. I *think* this is because the hibernate process disables networking, but it then fails to re-enable it because is fails to resume.

---

### Post by peterx14 on 2010-07-08
Another question: can anyone confirm that hibernate does work on a MacBook 3,1 with Ubuntu 10.04?

What I didn't mention before is that when I first installed Ubuntu, I installed it on a single partition with no swap space at all. I believe I have correctly enabled swap (it does show with the "free" command), but if this isn't a common problem, then perhaps that's where the problem lies?

---

### Post by peterx14 on 2010-07-13
Bump!

---

### Post by v41 on 2010-07-19
One possibility is that the swap space is misconfigured.

To check the swap configuration, search for "swap" in /etc/fstab.  There should be a line like this,

```
UUID=ab...     none            swap    sw              0       0
```If the swap UUID is incorrect, then the system will not resume from hibernate.

To get the correct swap UUID, open a terminal and type,

```
sudo blkid
```

---

### Post by peterx14 on 2010-07-24
I previously had the following in my fstab (/dev/sda4 *is* my swap partition btw!):
```
/dev/sda4  none  swap  sw  0 0
```

The "free" command was showing available swap space, so I think it was working correctly, but in the interests of giving anything a shot, I tried it with a UUID instead...  but that didn't seem to change anything!


However, to cut a slightly long story short, I figured out what I was doing wrong -- I needed to create the file /etc/initramfs-tools/conf.d/resume containing:
```
resume=UUID=a39a-etc-etc-etc
```

So thanks for getting me going in the right direction! :D


The only other slight issue is that it takes about 45 seconds to hibernate and then about 40 seconds to resume (after going thru the rEFIt and grub menus). Is this normal?

---

### Post by v41 on 2010-07-25
> **peterx14 said:**
> 
However, to cut a slightly long story short, I figured out what I was doing wrong -- I needed to create the file /etc/initramfs-tools/conf.d/resume containing:
```
resume=UUID=a39a-etc-etc-etc
```So thanks for getting me going in the right direction! :D

Well done!  Now that you mention it, precisely the same thing happened to me #-o.  It took me ages to discover the /etc/initramfs-tools/conf.d/resume file .  Unfortunately I subsequently forgot about it, so you had to endure the pain of rediscovery :( .

> 
The only other slight issue is that it takes about 45 seconds to hibernate and then about 40 seconds to resume (after going thru the rEFIt and grub menus). Is this normal?The time to hibernate depends on how much memory is in use since this is all written to disk.  So if you hibernate shortly after a system restart then hibernate should be fairly quick.  But if there are lots of open applications and the uptime is a week or more then hibernate will be slow.

---

