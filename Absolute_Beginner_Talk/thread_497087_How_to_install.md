---
title: "How to install?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by S3NTYN3L on 2007-07-09
I have XP Home on my 250GB hard drive.
There is only the one (primary) partition. (well, there's 8MB free, but I don't count that)...

Can someone walk me through (READ: HOLD MY HAND) how to SAFELY edit the partition via the Ubuntu installer?

I DO NOT want all my XP crap to go bye-bye...

Thanks...

---

### Post by FNDII on 2007-07-09
I dont think you can partition a part of the HD off with windows still on it.

---

### Post by be4truth on 2007-07-09
I would download gparted and burn it on a CD. [http://http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163]("http://http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163")
[SIZE="6"]Backup all your data:KS[/SIZE]
Use your brand new gparted CD Boot from it and resize your XP installation.
Make an unallocated space (grey colour) of a minimum of 15 GB,  better more.
Now boot into Ubuntu and when asked in the partition manager what to do, tell it to use the "unallocated space".

---

### Post by overdrank on 2007-07-09
> **S3NTYN3L said:**
> I have XP Home on my 250GB hard drive.
There is only the one (primary) partition. (well, there's 8MB free, but I don't count that)...

Can someone walk me through (READ: HOLD MY HAND) how to SAFELY edit the partition via the Ubuntu installer?

I DO NOT want all my XP crap to go bye-bye...

Thanks...

Hi and welcome, this link may help you and it has some screen shots to let you know what to look for.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Good luck!

---

### Post by Nekiruhs on 2007-07-09
> **FNDII said:**
> I dont think you can partition a part of the HD off with windows still on it.
You can so. You just resize the NTFS partition and Filesystem and make a new ext3 partition and filesystem in the free space.

---

### Post by S3NTYN3L on 2007-07-10
OK I've got it installed...

When I was booting from the Live CD I had to change the display mode from VGA to the highest available res for anything Ubuntu to display on my screen.

Now that I've got everything installed, how the hell do I get my display to, well, display?

I'm on a custom build and I'm running a EVGA 8800GTS hooked up to a 22in LCD via DVI...

---

