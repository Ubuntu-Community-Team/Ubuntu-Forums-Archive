---
title: "How to repartition in the installer to keep Windos"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-26
Hi all,

I'm about to install Ubuntu 7.10 64 bit on my laptop and would like to keep my Vista install. 

Using the text installer, which of the following partition options is the one I should go with?

There are

Guided - Resize SCSI1 (0,0,0), partition #1 (sda) and use freed space,
"Manual" partitioning, under which I can resize the partition that Windows is on

Which one will keep my Vista install safely?

Jugney

---

### Post by omegamike3 on 2007-12-26
Using 'Manual' partitioning will allow you to use whatever free space is left after resizing with Vista partition. It's recommended that you use vista first to resize it's own partition and then take it from there with Ubuntu. Also, if you've been using the Vista install, you'll want to defrag and clean up the drive before you resize it for optimal shrinkage (in this case, a good thing :p)

---

### Post by cmo220 on 2007-12-26
They should both keep your vista installation.  Do you only have the 1 hard drive?  I used the guided and it worked fine for keeping my vista installation.

---

### Post by Cypher on 2007-12-26
If your laptop came pre-installed with Vista, there probably only is one partition that contains Vista, so you'll have to resize the existing partition and then have the installer create new partitions for Linux.

The guided option should do this, the manual option will just show you want you have..

So first go to Manual and see how many partitions gets listed and how much (if any) free space there is..if there is no free spae and only one option, back up and go with the Guided method..

Backup any data you have in Vista before attempting this and also ensure that you have the Vista recovery CD should something happen and you can't boot back into Vista before trying any of this!

---

### Post by wolfen69 on 2007-12-26
you can use the "slider" button to resize the partitions. make sure to defrag vista first.

---

### Post by Jugney on 2007-12-26
Schneike!

I just discovered there was one super important folder I somehow didn't backup. I realized this after using the partitioner in the installer, but before installing the new Ubuntu luckily.

I'm not sure I used the right partitioning option, though. I went Manual, resized, giving just enough space to Ubuntu so that there was space for Vista. But it calls the Vista partition "FREE SPACE" so I'm not sure if Vista is still there or would be functional anymore.

I haven't installed anything yet, so I'm thinking I can probably recover the needed folder. My problem is I haev no  way of booting my computer - I had a previous version of Ubuntu and used GRUB as my bootlaoder, and then deleted the partition it was on (in order to repartition and give the new Ubuntu more space). So now I can't even boot into Windows Vista...assuming it's still there.....

Any advice for recovery???

---

### Post by LaRoza on 2007-12-26
> **Jugney said:**
> Schneike!

I just discovered there was one super important folder I somehow didn't backup. I went into the Manual install partitioner and it appears that actually didn't recognize my Vista install!

I haven't installed anything yet, so I'm thinking I can probably recover this folder. My problem is I haev no  way of booting my computer - the dual boot used GRUB until I deleted my Ubuntu partition in preparation for re-installing it. So now I can't even boot into Windows Vista...assuming it's still there.....

Any advice for recovery???

Download and burn the Super Grub Disk, see the link in my sig

Boot from it:

Advanced->Windows (Advanced) chose the option to restore the Windows MBR (the first option I think)

---

### Post by Jugney on 2007-12-26
THANK YOU!!!! I'm now rebooting in Windows thanks to Super Grub and you =)

I love all these free tools.

---

