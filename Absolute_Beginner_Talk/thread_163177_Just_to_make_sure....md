---
title: "Just to make sure..."
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Melhisedek on 2006-04-20
There is only one CD needed to install Ubuntu, and it is recommended to use Live CD right?

How does Live CD works, lets say I want to code some program, where do I save my work? Can it write to Windows file system (NTFS in my case)? 

Thank you for your time!

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=Melhisedek]There is only one CD needed to install Ubuntu, and it is recommended to use Live CD right?
[/quote]
right now, with the stable ubuntu (5.10), the install CD is needed to install ubuntu... 
[QUOTE=Melhisedek]
How does Live CD works, lets say I want to code some program, where do I save my work? Can it write to Windows file system (NTFS in my case)? 
[/quote]
it can write to a fat32, but you won't be able to write to an ntfs partition.

---

### Post by Melhisedek on 2006-04-20
I see, I was checking Dapper beta and it looks like you can install it with Live CD as well if I'm not mistaken :)

So no writing to ntfs... Can it read it? Like I get to use my mp3s while I check it out :)

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=Melhisedek]Dapper beta can install it with Live CD [/quote] that's correct :)
[QUOTE=Melhisedek]
So no writing to ntfs... Can it read it? Like I get to use my mp3s while I check it out :)[/QUOTE]
it can read it. though I'm not sure if it mounts it automatically.

---

### Post by Melhisedek on 2006-04-20
Mate you bloody rock ! Thanks for swift replies! I'll have to make you my deity for next 1.64361256153 minutes... You like dead or live offerings? ;)

---

### Post by towsonu2003 on 2006-04-20
lol
have fun :)

---

### Post by mostwanted on 2006-04-20
The Live CD installer in Dapper is not really good enough for "production use". It's bugged out on me a couple times while using it. I recommend you get the regular install CD.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=mostwanted]The Live CD installer in Dapper is not really good enough for "production use". It's bugged out on me a couple times while using it. I recommend you get the regular install CD.[/QUOTE]
it seems they prefer to promote the live cd for installations as well: [http://distrowatch.com/?newsid=03376#0](http://distrowatch.com/?newsid=03376#0)

anyway, for production systems, don't use dapper.

---

### Post by mostwanted on 2006-04-20
[QUOTE=towsonu2003]it seems they prefer to promote the live cd for installations as well: [http://distrowatch.com/?newsid=03376#0](http://distrowatch.com/?newsid=03376#0)

anyway, for production systems, don't use dapper.[/QUOTE]

That news blob just says it can be used for both purposes; not like it's promoting it. When you start up Espresso it even reads "this was only certified to work on the author's system" and I can personally say that it's not of a high enough quality to earn my recommendation.

---

### Post by towsonu2003 on 2006-04-20
> **mostwanted]That news blob just says it can be used for both purposes said:**
> 
from the official announcement (linked in distrowatch update) [https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000065.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000065.html)

[quote]
The Ubuntu team is proud to announce the Beta Release of Ubuntu 6.06 LTS -
codenamed "Dapper Drake". The Beta Release introduces the new Desktop CD,
which can be used both to try Ubuntu "live" and to install the system.

Ubuntu is a Linux distribution for your desktop or server, with a fast and
easy install, regular releases, a tight selection of excellent packages
installed by default, every other package you can imagine available from the
network, and professional technical support from Canonical Ltd and hundreds
of other companies around the world.

Ubuntu 6.06 LTS (long-term support) will be the first Ubuntu release to be
supported for three years on the desktop, and five years on the server.
They don't specifically mention the install CD but the LiveCD instead, hence I thought they prefer people to use the LiveCD. sorry for the misunderstanding.

---

### Post by Melhisedek on 2006-04-21
Well install from liveCD crashed 2-ce on me :/ And it seem that my laptop can't even open start menu without spinning up and down like crazy, everything lags. So I'm downloading install CD :) Hope I can manage to resize one of my partitions and than install Ubuntu.

IIRC there should be 3 partitions... One swap, and 2 others... What file system should they use? Or does it matter...

---

### Post by Sef on 2006-04-21
> IIRC there should be 3 partitions... One swap, and 2 others... What file system should they use? Or does it matter...

For just Linux/GNU:

/boot  reiserfs or ext 3
/home reiserfs or ext3
/swap

For Linux/GNU and Windows (Dual Boot)

/NTFS - already installed (Windows)
/FAT32 or /ext2 - for sharing between Ubutntu and Windows
/boot - reiserfs or ext3
/home -reiserfs or ext3
/swap

---

### Post by Melhisedek on 2006-04-21
What is difference between reiser and ext3? Which do you guys use?

---

### Post by towsonu2003 on 2006-04-21
[QUOTE=Sef]For just Linux/GNU:

/boot  reiserfs or ext 3
/home reiserfs or ext3
/swap

For Linux/GNU and Windows (Dual Boot)

/NTFS - already installed (Windows)
/FAT32 or /ext2 - for sharing between Ubutntu and Windows
/boot - reiserfs or ext3
/home -reiserfs or ext3
/swap[/QUOTE]
excuse my stupidity, but where did / (root) partition go? does /boot include /?

a reference on partitioning: [www.tldp.org/HOWTO/Partition/](www.tldp.org/HOWTO/Partition/)
a reference on filesystems (I use ext3): [www.tldp.org/HOWTO/Filesystems-HOWTO.html](www.tldp.org/HOWTO/Filesystems-HOWTO.html)

---

