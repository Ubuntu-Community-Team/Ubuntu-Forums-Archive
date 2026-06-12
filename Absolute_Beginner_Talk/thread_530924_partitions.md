---
title: "partitions ?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2007-08-21
Hi,

     what's the difference b/w logical partion & physical partition?

Can i install ubuntu on logical partition?

---

### Post by Sye d'Burns on 2007-08-21
There can be up to four primary partitions on a physical drive. To get around this limitation an extended partition which is a kind of shell that can hold logical partitions within it is used. 

You can install ubuntu to a logical partition without issue.

---

### Post by Aishiko on 2007-08-21
physical partition? never heard of one unless it is an obscure term for a hard drive.

you can only install on a logical partition, that is the space on a hard drive that has been prepared to hold data, ie it has been formated.

Now that i think about it a physical partition might be the techincal term for the platters of the HDD or maybe the over all term for all the logical partitions on a hard drive.  It's been over a decade since my really indepth computer course that was heavy on the termanology.

but the short answer is you can only install on a logical partition, it doesn't matter if it is a primary or extended partition.  Ubuntu will prompt you to create a compatable partition.

---

### Post by bdsatish on 2007-08-21
OK...

  I've an 80 GB hard-disk partitioned into four 20GB drives:

 C: ,  D: ,  E: ,  F:         (as seen from Win XP)

 So, if i want to install ubuntu (dual-boot) should i create an extended (logical) partition in the C: drive (having Win XP) ?

Anyways, i have upto 10 GB free space on the C: drive...

---

### Post by Sye d'Burns on 2007-08-21
You can resize the C drive but if you're planning on dual booting you're needlessly playing with fire. 

I would recommend moving files from a drive that doesn't contain XP, F for instance,... get everything off from F. Then blast that partition and create your Ubuntu partition from that space.

---

### Post by bdsatish on 2007-08-21
Oh.. dat sounds great..

OK, i'll clean-up my F:\ drive and completely free-up the 20 GB..Then install ubuntu on it..

If i still want to dual-boot...

Shouldnt WinXP and Ubuntu need to be installed on the same partition for dual-boot to occur?

---

### Post by mikewhatever on 2007-08-21
You may have a problem here. If all four partitions are primary, you would not be able to create any more of them for Ubuntu without deleting one.
Another reason to delete one of the partitions is, resizing C will leave you with little free space for both Windows and Ubuntu.

---

### Post by Sye d'Burns on 2007-08-21
No, when you install Ubuntu, during the Grub install Ubuntu will scan for any other OS and add XP automagically. Just put it to the MBR and you should be good to go.*

*-There are other options, floppy etc, but MBR should be fine for what you want to do.

---

### Post by Sye d'Burns on 2007-08-21
Oh, I suggested he blast the F drive (I should've said delete the partition but it's 1:30am- oops)  

Yeah, you'll definitely want to delete that partition once you've cleared it because you'll still need to create a swap partition as well.

---

### Post by bdsatish on 2007-08-21
Ohho...

 This is getting messier... I'm a complete newbie and things like deleting a partition sounds scary !

---

### Post by ubuntu27 on 2007-08-21
Here is a guide on [How to PLAN the partition that suits your NEEDS]("http://www.psychocats.net/ubuntu/partitioning")

Don't be afraid bdsatish. I know partitioning is scary. It was scary for me too when I first tried it. You just have to patient, be razonable, and pay attention.

In your other thread you said you were going to remove Win XP. If you still want to do it, you don't have to worry about partitioning. Just do the **default** partitioning process (erase whole disc) and the installes will do the rest like creating swap partition.

But, if you want to have a dual-boot (Good idea if you don't want to jump in a hurry), then let's make a plan about your partition.

Tell us what your partitions are and **what are they for**? Back-up partition?

---

### Post by bdsatish on 2007-08-21
My partitions:
                             
                    Free space                 Used space
C:                    10.5 GB                        9 GB
D:                      8.5 GB                        11 GB
E:                     11.3 GB                        8.2 GB
F:                      10  GB                         9.5 GB

 I dont have any back-up partitions.

As usual, I've installed XP on C: drive ...

---

### Post by Sye d'Burns on 2007-08-21
If you save what you plan to save from F and delete the partition you will need to set up a 1 gig (personal preference if you want more really) swap partition and the rest of the available space as a root partition. 

I can understand being nervous. When you play with the partition table there is always the chance that something could go funky. I wholeheartedly recommend that you back up anything on any partition that you aren't willing to gamble (no matter how long the odds of anything actually going wrong.) 

Go in there with a plan of attack, follow ubuntu27's link, it's good advice. It's 2:40am, I'm going to hit the sack. Good luck.

---

### Post by ubuntu27 on 2007-08-21
> **bdsatish said:**
> My partitions:
                             
                    Free space                 Used space
C:                    10.5 GB                        9 GB
D:                      8.5 GB                        11 GB
E:                     11.3 GB                        8.2 GB
F:                      10  GB                         9.5 GB

 I dont have any back-up partitions.

As usual, I've installed XP on C: drive ...

OK, so, is it alright for you to delete D, E, and F (not that you have to eliminate all three. You have to delete at least one) What do you have on D, E, and F? Are they important?

Make a back up of your files in the partition that you are going to delete.

Also, in the mean time, if you don't have the UBuntu CD, then download the iso
from here:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by bdsatish on 2007-08-21
Since, i've some 25 GB stuff on these 3 drives, it'll take a long time for me to back-up...

I'm thinking of transferring the stuff from F: to E: ... it'll completely fit..

Then i'll be ready to delete the F: drive...

Thnks for the link, i've downloaded the ISO and burnt it to a cd yesterday.. The CD is working fine.. i'm able see the start-up scrren of ubuntu..

---

### Post by ubuntu27 on 2007-08-21
Great! After moving your files. You will be ready to install Ubuntu.
If you need help for installing, just create a new thread. People usually skip threads that already has some replies thinking they already got the answer. 
This thread is about partitioning, create a new thread about installing UBuntu.  :)

Many questions are answered in this [Ubuntu Guide]("http://www.psychocats.net/ubuntu/index.php")

[How to install ubuntu using Desktop CD]("http://www.psychocats.net/ubuntu/installing")

It's 12:09 AM where I am. I'll go to sleep.
Good luck!

---

### Post by gupta_sumesh63 on 2007-08-21
Best is to backup all files in D E and F. Delete all three. Boot with Ubuntu Live CD. Select install. and then manually manage your partitions when the partition phase comes. You can increase Window partition. and choose what you require for Ubuntu, Swap and Fat32 if desired.
But Defrag your Windows maybe twice before you do all this.

---

