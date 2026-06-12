---
title: "Cannot install Ubuntu."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Nikko2 on 2007-10-28
Guys, Total newbie to this so please dont flame grill me.

After a recent windows XP problem giving me the complete **** with MS. Without going into war and peace. XP pretty much wouldnt do anything other than through up dll and registry erros one day. I tried to repair it but that seemed to only reinstall it all again and needed re registering. So I gave up.

I then downloaded this ubuntu file and put it to CD.

ubuntu-7.10-desktop-i386.iso

Of course it wont install as XP was halfway through an install. I then used partition magic to format the c:

Then when I put in the ubuntu disk it would not boot the cd. NTLDR is missing.

So after a bit of searching I copied some files across from the XP disc to the c: as described in another thread here.

Now when I stick in the ubuntu disc I get windows could not start because the following file is missing or corrupt. Windows root\system32\hal.dll

Have I downloaded the wrong ubuntu version? I thought it might install like XP put in the CD and sit back. Is it right that I have to copy windows files over to the c: to get the ubuntu disc to load?

 Many thanks in advance.

---

### Post by kellemes on 2007-10-28
I would start over to be honest..
Don't use Partition Magic but boot a GNU/Linux-LiveCD (Gparted-LiveCD, Knoppix or Ubuntu itself) and use GParted to clean your disk, delete/format!!
Think about a partition-scheme and set it up using GParted..
Install Windows fresh (first partition of bootdisk) and see to it everything works..
Then install Ubuntu..

If you can give me a little more info on your installed disks and a general idea on how you want your system setup, maybe having a sparedisk or something..
I can help you with a partition-scheme..

---

### Post by Nikko2 on 2007-10-28
Oh oh schoolboy error my ubuntu disc hasone large  image file on.

hopefully will post back with success shortly.

---

### Post by kellemes on 2007-10-28
> **Nikko2 said:**
> Oh oh schoolboy error my ubuntu disc hasone large  image file on.

hopefully will post back with success shortly.

You need to burn **as ISO**, don't burn the ISO.

---

### Post by Nikko2 on 2007-10-28
That did the trick it started ti install now I am at a screen in dos

busybox v1.1.3 built in shell enterhelp for list of commands

(intitramfs)

Searching google now for guide as to what to type in next

---

### Post by Phrellex on 2007-10-30
I currently run Ubuntu 7.10 Gutsy, which was upgraded from 7.04 Feisty. I am unhappy about how 7.10 does not work well with my nvidia geforce 6200 card and would like to reformat and downgrade. The problem is the first time I managed to install from the CD, I spent numerous hours being faced with various failed messages as the disc worked past the loading bar and spammed lines  of "User not known to the underlying authentication module." I get this with all the CDs I have burnt, and of different versions of Ubuntu. The time it actually loaded, I gather was by luck. Anyone have any idea, what is wrong with my computer or discs?

---

