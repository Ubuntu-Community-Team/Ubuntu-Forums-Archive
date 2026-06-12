---
title: "xmnt2002 error"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by jbag on 2006-08-26
Hello

I am new to Linux & Ubuntu.

I recently, (about 4 hours ago), installed Ubuntu 6.06.15 on my system.
It boots to Ubuntu through GRUB fine. The problem is that when I try to load Windows XP it gets to the loading screen & then the blue screen of death,(not suppose to happen with XP, or so they say), appears. 

The error is as follows

xmnt 2002 program not found - skipping autochk
Autochk program not found - skipping autochk

I heard somewhere that this could be a problem related to Partition Magic.
Seeing as how I used Partition Magic to partition the drive, I checked with Symantec.
What they say to do basically is to boot into Windows & modify a line in the registry. The problem is that I can't get into windows even in safe mode or any other way for that matter.

Does anyone know of any other mehtod to remedy this problem or of some way to access the registry.

I have a 160 gb hard drive with XP on hda1 Ubuntu is on partition 3 & the swap file is on partition 2. I don't know if any of this helps or not.

Any info would be appreciated.

I used Ubuntu for about 6 weeks from the Live CD & really liked it. Now that I am ready for the prime time so to speak I would really like to get everything up & running.

Thanks

jbag

---

### Post by Bachstelze on 2006-08-26
Hi and welcome to Ubuntu :)

So all in all : don't use Partition Magic :p Can you afford reinstalling Windows ?

---

### Post by jbag on 2006-08-26
Thamks for the reply.

If I had to do anything at all I would prefer to uninstall Ubuntu & using the XP install disk I could use fixmbr & fixboot through the repair console. That would render Ubuntu non bootable. 

The problem is that my son has things on the Windows partition that I was on the impression that he backed up. These are important documents & proprietary programs that he no longer has the disks for, (he can't find the originals & never made a backup copy), & of course the programs are no longer available.

If there is a way to make it so that I can get Windows to boot without uninstalling Ubuntu, then that is the way I would rather go. If not then removing Ubuntu might be the answer. I could then, I think, repartition The hard drive using another partitioner. Although I'm not sure what one to use.

My next step is to load another Linux Distro on. Maybe Freespire or Xandros or something similar. I would then have a tri-boot system. One thing at a time however.

Maybe I'm flogging a dead horse & need to just remove Ubuntu, do the repair, repartition using another partitioner, & reload Ubuntu. But I am like a lot of other people & look for an easy out. I am Basically lazy when it comes to things like this.

Thanks

jbag

---

### Post by jbag on 2006-08-26
Ok!!!!

Looks like I got it

I found a copy of Ultimate Boot CD (UBCD). An older version but what the hey.
Tried using GAG & Super GRUB Disk but wouldn't work. I used Smart Boot Manager & was able to boot into Windows. This allowed me to go into Regedit & 
edit the registry as instructions per Symantec. 

I can now boot into both Ubuntu & Linux.

I am going to use this setup for now but a little later on try to add another Linux distro & hopefully be able to tri-boot. 

I may also make sure that all is backed up & reformat the hard drive & partition with something else. I have been reading some other posts & most seem to like Gpart or QTparted. 

Thanks for listening & your input.


jbag:D:D :D

---

