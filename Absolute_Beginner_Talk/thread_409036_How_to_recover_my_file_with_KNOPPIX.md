---
title: "How to recover my file with KNOPPIX??"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by sebdj on 2007-04-14
Hi! 

I have send a post here to find some help about my computer don<t boot up after instaling ubuntu. 

THey give this knoppix I have burn it and now I<m using it to write this message. 

I just will like to know   how am I suposed to see my file and burn it in a cd? 

After that I will do a complete format.

---

### Post by n3tfury on 2007-04-14
> **sebdj said:**
> Hi! 

I have send a post here to find some help about my computer don<t boot up after instaling ubuntu. 

THey give this knoppix I have burn it and now I<m using it to write this message. 

I just will like to know   how am I suposed to see my file and burn it in a cd? 

After that I will do a complete format.

iirc, i believe Knoppix (and its variant Kanotix) uses k3b - look for that.  of course, that's only going to work if you have one cdrom drive and one cdburner drive, etc etc.

if your file will fit, use a thumb drive instead.

---

### Post by confused57 on 2007-04-14
I don't know if TestDisk will work for you, but you might want to read Herman's reply in this thread:
[http://ubuntuforums.org/showthread.php?t=408834](http://ubuntuforums.org/showthread.php?t=408834)

---

### Post by n3tfury on 2007-04-14
> **confused57 said:**
> I don't know if TestDisk will work for you, but you might want to read Herman's reply in this thread:
[http://ubuntuforums.org/showthread.php?t=408834](http://ubuntuforums.org/showthread.php?t=408834)

i believe he was going to wipe his HDD and just install Ubuntu (read from another thread).  plus, even if testdisk repairs the partitions, he'd still wind up burning data.  if he's got two drives, may as well do it now and get it over with.

---

### Post by confused57 on 2007-04-14
> **n3tfury said:**
> i believe he was going to wipe his HDD and just install Ubuntu (read from another thread).  plus, even if testdisk repairs the partitions, he'd still wind up burning data.  if he's got two drives, may as well do it now and get it over with.
Yes, he probably might as well go ahead and recover data & reinstall.
I was searching Knoppix cheatcodes & you can use the "toram" boot parameter:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

at least 1 Gb of ram is required, but it allows you to remove the cd & write to another blank cd, Knoppix runs from ram & this frees up the cd drive.

---

### Post by n3tfury on 2007-04-14
> **confused57 said:**
> Yes, he probably might as well go ahead and recover data & reinstall.
I was searching Knoppix cheatcodes & you can use the "toram" boot parameter:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

at least 1 Gb of ram is required, but it allows you to remove the cd & write to another blank cd, Knoppix runs from ram & this frees up the cd drive.

nice find!!

---

