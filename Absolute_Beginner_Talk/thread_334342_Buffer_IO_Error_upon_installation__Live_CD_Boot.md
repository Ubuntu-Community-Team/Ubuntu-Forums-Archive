---
title: "Buffer I/O Error upon installation / Live CD Boot"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by afin on 2007-01-08
While I've seen numerous threads about some variant of the I/O error, I have never come across one that seems applicable to my case (of course I may be wrong).

In any case, upon installing (or, for that matter, merely booting from the Ubuntu 6.10 Live CD), I come across the following error:

"...Buffer I/O error on device sr0 logical block 357564"

My computer specs are as follows:

Supermicro Super X6DAL-G
Dual Xeon 2.8 800 Mhz
NVIDIA Quadro FX 1300
1 Gig of Ram
(2) HDs: 80 gig and 200 gig

I have partitioned my 80 gig into a ~40 gig NTFS C: drive for Windows XP; a ~36 gig Ext3 for the Ubuntu boot; and a 2048mb swap. I am undecided as to how I'm going to split my 200 gig drive, but that is irrelevant for this, I assume. It also seems to make no difference whether I set the Ext3 and Swap drives to logical or primary (using Partition Magic). I assume the reference to "sr0" in the error message is to my first (80 gig) hard-drive, but I am not sure why.

Is the problem my hardware? Must I manually install Ubuntu? Can I install Ubuntu from Windows onto the Ext3 partition? If so, are there any references for this? I am completely new to Ubuntu.

Thanks.
-Adam

---

### Post by Tdonohue on 2007-01-11
I am getting the exact same error.  Whether I hit "start Ubuntu" or "check CD for defects" it does the same thing; says "loading kernel", then screen goes black for two minutes and comes back with this error (usually 6 lines of the same error, differing only by the last number)

I am installing on an Inspiron 6000.  The md5 checksums match.  I burned .iso to two different brands of disks.  

Would love to get this distro working, had Fedora core 5 on same laptop in past but had trouble learning linux on it (I'm very new to this).  Any help would be appreciated.

Tim

---

### Post by shareMenaPeace on 2007-01-11
I always get this but after awhile it starts.
Takes like 4 minutes?

---

### Post by Tdonohue on 2007-01-11
So, Share, do you think if we just leave it alone after those errors come up, the installer will go through.  Is this what you've done?  I'll give it a try.  In the meantime, since my last post, I tried an install with the same disk on an old PC (old as in 333mz, 256mb ram). It didn't work, but as primarily a windows user, I can't tell why.  I'm so used to being able to solve any problem in windows that, when I hit a roadblock in Linux, I feel so.....naked and vulnerable.

---

### Post by Tdonohue on 2007-01-13
THANK YOU! Just waiting worked.  The install proceeded flawlessly after about 5 minutes or so.

---

