---
title: "Partions and Defrag"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by crav on 2007-06-21
I need to resize my old windows partition to give more space for linux. Someone in #ubuntu told me to use gparted. I got this, but it says I don't have the appropriate plugins.
I understand I'll need to defrag the windows partition in order to extend into it. Is there a way I can defrag AND repartition without having to boot to windows?

What to do!?
many thanks!

---

### Post by logos34 on 2007-06-21
Defrag windows from within windows.  Do it several time if necessary to compact your files as much as possible.  You might need to temporarily disable swap/virtual memory and hibernation until after ubuntu is installed.  Then simply use the version of gparted on the ubuntu live cd to resize/shrink windows partition.  Restart and use the grub menu to choose to boot windows.  Allow it to run CHKDSK, then reboot twice into windows.  After everything is ok in windows, boot into ubuntu.

---

### Post by crav on 2007-06-23
Could someone post a guide a little bit more in depth? After downloading Gparted, it says I lack the neccessary plugins. The version on the live CD has errors when I try to resize my NTFS partition.

Is my only option to completely reformat and start over!?

---

### Post by Inxsible on 2007-06-23
Is there a reason you dont want to log into windows to defrag the drive. Its much better to defrag the windows partition with its own defragger. Defrag it a few times until you are satisfied and then use the Gparted Live CD to shrink the Windows partition and then merge the new unallocated space with the unallocated space from your Linux drive and create a new partition from it.

---

### Post by crav on 2007-06-23
I've done all the defragging from windows, it's the partitioning I'm having trouble with. Partition Magic isn't working correctly in windows. Gparted (running of my HDD) says it lacks the neccessary plugins. Gparted on my live CD (the most recent one I have, which is 6.6) gives an error when trying to modify the partition table. Will the Gparted live Cd fix this?

---

### Post by molly_001 on 2007-06-23
Download the June, 2006, version of the LiveCD of GParted.  version 2.5-2

For some reason, that version has always worked on every machine for me, including ones where a *later* version would give me the problems as you describe.

---

### Post by gigaferz on 2007-06-23
hello, you can find this  free partitioner in a recue cd (gparted,but only use it to make your linux partition,no more):

  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If not 
I remember in theubuntu  live cd there is also qtparted,

Have you tried using qtparted (open a terminal and type sudo qtparted)

to create partitions?

I also remember having troubles with the installer  , It wanted to  partition the whole hda1 again, so I mounted the windows partition  so the installer ignores it
however this happened with 6.10, maybe with the newest it wont be an issue

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by louieb on 2007-06-23
you did not say how big your win partition is or how full it is.  do you have room to shrink?
i like using windows programs like partition magic or disk director to shrink ntfs partitions Linux programs like gparted to resize linux partitions. If partition magic does not want to shrink your win partition i would be wary of trying gparted. 
i would want a full backup before even thinking about it.

---

### Post by crav on 2007-06-27
Some answers:
My win partition is ~60 gigs, ~60% used
My lin partition is ~12 gigs, ~90% used

I'm looking to expand the linux partition because (9 months ago) using linux was a temporary solution to a temporary problem. However, I've liked it so much that I've made it my own. As anyone might guess, 12 gigs really isn't enough for my OS, programs, and lots of data.

With all the trouble I'm having, I'm wondering if it wouldn't be easier to backup and format my whole drive. I'd likely install Ubuntu first, than squeeze WinXP into the smallest possible partition.

Is this whole reformat the best way to do this, or is there some way I could keep my current partitions, and therefore my settings and programs?

I think I've about covered everything!

---

### Post by lisati on 2007-06-27
Don't forget to check the "Temporary" directory from XP - the Windows Cleanmgr program doesn't effectively clean it out.  You might be surprised how much "rubbish" lingers there!

The temporary directory can be viewed by typing "%temp%"  (without the quotes) in the Start->All Programs->Run menu option in XP. Delete as much as you can - Windows might complain about some files being in use, just deselect the files it complains about and try the delete again. Don't forget to empty your recycle bin too! (A program "SImple System Cleaner" is available to do this automatically for Windows 98 from [www.winsite.com](www.winsite.com) and [www.geocities.com/rjv_soft](www.geocities.com/rjv_soft) - unfortunately it doesn't work too well with XP, and since I've lost the source code, I haven't bothered updating it in some time) 

Hope this helps free up a bit more room.

---

