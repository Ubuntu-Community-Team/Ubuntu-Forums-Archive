---
title: "[SOLVED] Vista, Ubuntu 7.04, HP Recovery"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-25
I bought an HP laptop which came pre-installed with Vista Premium.

I have a 160GB hard drive. HP has created a 6.6GB partition called HP_RECOVERY 
which is obviously for recovery purposes. I cannot see any of the files in this partition thru Vista, however Ubuntu LiveCD shows all the files in there   :)

My problem is that this Recovery partition is at the end of the drive.  I have read on many threads that /swap should be placed at the end of the drive.

How will i move the data from HP_RECOVERY partition so that I can place /swap at the end of the drive and NOT losing the recovery data in the process?

EDIT : I have uploaded a screen-shot of GParted which shows my drive structure. Should I move HP_RECOVERY to the front of the drive and if so how will I be able to do it without losing the data on it?

---

### Post by Inxsible on 2007-04-25
Bump.
 
Anybody ?

---

### Post by nu2this on 2007-04-25
It did it this way for Edgy I 'm pretty sure it'll apply to Fiesty too. You won't have to worry about that go on & dual boot. Just run a defrag in windows 1st. Then install Feisty just go with the defaults you should be fine.

---

### Post by tekguy on 2007-04-25
I have an HP dv9000t and it also came with an HP_Recovery partition. You should have received a restore DVD from HP. If that's the case you can actually dump that recovery partition. The recovery partition is there to use their app that you can launch on a reboot to restore without the DVD. 

At least that has been my experience on my laptop. I removed the recovery partition and can still recover from the DVD.

On another machine I have my /swap file in the middle of my partition list. I haven't had any issues.

As far as moving, I see that your Resize/Move is grayed out. Mine is too. You may have to boot off of your live CD, Knoppix, or a GParted boot disk. This should let you simply drag your first partitions to the back of the free space and then move your HP_recovery to the front. Even a Partition Magic boot disk would work. It seems though that being logged in to Ubuntu I can not modify the hard drive I am installed on. My other hard drives show up with no issue.

Hope that helps.

---

### Post by Inxsible on 2007-04-25
> **tekguy said:**
> I have an HP dv9000t and it also came with an HP_Recovery partition. You should have received a restore DVD from HP. If that's the case you can actually dump that recovery partition. The recovery partition is there to use their app that you can launch on a reboot to restore without the DVD. 

At least that has been my experience on my laptop. I removed the recovery partition and can still recover from the DVD.

On another machine I have my /swap file in the middle of my partition list. I haven't had any issues.

As far as moving, I see that your Resize/Move is grayed out. Mine is too. You may have to boot off of your live CD, Knoppix, or a GParted boot disk. This should let you simply drag your first partitions to the back of the free space and then move your HP_recovery to the front. Even a Partition Magic boot disk would work. It seems though that being logged in to Ubuntu I can not modify the hard drive I am installed on. My other hard drives show up with no issue.

Hope that helps.

Thanks tekguy,
a couple more questions...since you have the same computer as mine..maybe you'd help me out here.

1) HP did give me a DVD which says Windows Anytime Upgrade on it. Is that the same as the recovery disc ?

2) Did you get your integrated webcam and microphone to work with Ubuntu ?

I haven't tried those out since I am still on the Live CD.

Thanks

---

### Post by LaRoza on 2007-04-25
Anytime Upgrade is not bootable, it is so you can upgrade Vista to a more expensive version by paying online for the code.

The advice to defag then install is erroneous, you must use Vista to resize the partitions so you can install Ubuntu to that partition. If you try to edit partitions with third party tools, like Ubuntu and GParted, you will destroy the file system.

In Vista's case, this will mean it won't work at all; I do not know what will happen to Ubuntu.

If you have no need for Vista i.e. everything works in Ubuntu or can be made to work and you don't live on Windows games, you could overwrite it, like me.

---

### Post by az on 2007-04-25
The swap can be anywhere on the drive.  That does not affect performance.

---

### Post by az on 2007-04-25
> **LaRoza said:**
> 
The advice to defag then install is erroneous, you must use Vista to resize the partitions so you can install Ubuntu to that partition. If you try to edit partitions with third party tools, like Ubuntu and GParted, you will destroy the file system.

Not true anymore.  That bug in libntfs was fixed before feisty's release.

---

### Post by Inxsible on 2007-04-25
If its fixed.....great !!
 
 
However I have already created my Vista partitions (thru Vista utility) and I have my unallocated disk where I plan to install Ubuntu.
 
 
I guess I shall just keep the Recovery partition where its at !!

---

### Post by thefoolisme on 2007-04-25
Newer HP's don't come with CDs anymore.  There should instead be software on your system that will allow you to make restore disks from the information located in your recovery directory.  You should probably make those CDs before anything happens.  :-)

---

### Post by LaRoza on 2007-04-25
On my compaq with Vista Home Premium, the option to make recovery disks did not work.

---

### Post by Inxsible on 2007-04-25
That's a good idea. I plan to do that. However, since the total recovery size is 6.6 GB, I shall need DVD's and I have been a lil lazy since I keep playing with my new machine.

I cant access the files on that partition thru Vista, but Ubuntu shows me all the files. Can I simply copy all of that onto my 500GB External Drive. Will the recovery still work ( in case.. i need it)?

---

### Post by Loki-uk on 2007-04-25
Check on you laptop somewhere there will be an option to make a recovery DVD this will back up all the files in your hidden partition and burn them to DVD allowing you to do whatever you want with them.

You could always download virtual pc free from microsoft and run ubuntu in that.

Loki

---

### Post by tekguy on 2007-04-26
> **Inxsible said:**
> Thanks tekguy,
a couple more questions...since you have the same computer as mine..maybe you'd help me out here.

1) HP did give me a DVD which says Windows Anytime Upgrade on it. Is that the same as the recovery disc ?

2) Did you get your integrated webcam and microphone to work with Ubuntu ?

I haven't tried those out since I am still on the Live CD.

Thanks


Loki is right about the fact that there should be an option to create a restore disk. My laptop came with XP Media Center. I got it at the end of last year. So I don't have the Windows Anytime Upgrade disk.

I have integrated webcam and microphone. I'm actually backing all of my data up as we speak and am going to try to install Ubuntu again. I tried Edgy and I was concerned with how much more warmer my laptop felt so I went back to XP. But I am going to give it another try now.

---

### Post by jpyanowski on 2007-06-09
If you want a HP recovery DVD you have to have HP send you one (very cheap). You can use the Anytime upgrade DVD to repair the MBR if you screw it up (speaks from experience) :roll:

---

