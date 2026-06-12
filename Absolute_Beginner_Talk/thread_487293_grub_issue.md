---
title: "grub issue"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-06-28
I was dual booting xp and ubuntu... and then decided to just run ubuntu on my laptop. so i ran partition magic on my desktop to erase the linux partitions and thought everything was all good. then when i rebooted it grub came up with an error 22. so i was like shoot, i guess i'll just have to dual boot till i find out how to get rid of or bypass grub. so i go to reinstall ubuntu and when it comes to resizing the drive it freezes. so i reset the pc and try over and now linux isn't recognizing the windows that was on there before. right now when it asks how to partition the disk it says
guided-use entire disk
when before there was a meter that i could define the size i wanted.
so
1.did my hd get wiped out when i reset my computer?
2.is there a way to bypass grub from bios?
-

---

### Post by seetho on 2007-06-28
> **azizzle said:**
> I was dual booting xp and ubuntu... and then decided to just run ubuntu on my laptop. so i ran partition magic on my desktop to erase the linux partitions and thought everything was all good. then when i rebooted it grub came up with an error 22. so i was like shoot, i guess i'll just have to dual boot till i find out how to get rid of or bypass grub. so i go to reinstall ubuntu and when it comes to resizing the drive it freezes. so i reset the pc and try over and now linux isn't recognizing the windows that was on there before. right now when it asks how to partition the disk it says
guided-use entire disk
when before there was a meter that i could define the size i wanted.
so
1.did my hd get wiped out when i reset my computer?
2.is there a way to bypass grub from bios?
-

Your post is a little confusing.  Please clarify before someone here can attempt to help you.

You said you wanted just Ubuntu but deleted the Linux partition.  Did you erased the Ubuntu or XP partition?

You said you reinstalled Ubuntu but it is not recognising the XP partition.  I thought you already erased that?

Maybe this bit of information can help you.  Usually in a dual boot (XP and Ubuntu) the GRUB is installed on the XP partition.  If you erased that then GRUB is also gone so you won't be able to boot up after that.  You can fix it using the gparted live CD.  Since you already reinstall then just do a fresh install from your Ubuntu CD (I prefer the alternate CD).

---

### Post by rickycodie on 2007-06-28
if you removed the linux partition then you shouldn't be able to boot ubuntu. if you erased the entire windows partition then you disk recovery software. do not delete grub, it is what boots your computer.

---

