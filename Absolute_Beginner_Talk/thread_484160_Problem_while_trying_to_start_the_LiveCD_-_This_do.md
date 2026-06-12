---
title: "Problem while trying to start the LiveCD - This does not look good. :("
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Bensky on 2007-06-25
So I downloaded ubuntu 7.04 today, made sure that the md5 matched (to make sure I didn't have a bad disk), and restarted my pc with the CD in. I'm presented with the screen that says "install/run" or whatever, I choose run.

The ubuntu logo with the loading bar appears and starts loading. I notice that for some reason my floppy drive starts making noises like it's active. Then, my screen turns black and I'm presented with this:
```

bin/sh: can't access tty; job control turned off
ata 2.00: failed to set xfermode (err_mask = 0x4)

```

At that point, it kept repeating the second line (the one that starts with ata 2.00), so I just restarted my pc.

I had previously used a Ubuntu 6.10 livecd, and this NEVER happened to me, so I'm really confused as to what is going on. Is my boot order messed up maybe, or is my floppy being weird? No idea.

Can someone help please? :(

EDIT: By the way, this has happened with all the 7.04 disks I have used on my computer for some reason. I had burned another disc a while ago and the same thing happened, but I assumed that it was a bad CD. Not this time. :X

---

### Post by Seisen on 2007-06-25
Therei is a bug report listed for that exact problem 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864")

There is a few workarounds listed in the bug report that might work for you.

---

### Post by Bensky on 2007-06-25
Thanks. I think I found a way that will work, but I have a question about the 2nd error. Is the 2nd line related to the first one, in that if I fix the job control error, the 2nd error will go away? (the one about ata 2.00)

---

