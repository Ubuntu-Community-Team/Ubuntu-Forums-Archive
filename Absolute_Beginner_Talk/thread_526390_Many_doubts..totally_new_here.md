---
title: "Many doubts..totally new here"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by jocejas3112 on 2007-08-15
hello guys..
I've decided to try Ubuntu..
actually I run my HP pavilion dv1000, windows xp, 80gb hard disk drive, 512mb ram, 1.60mghtz processor..
first question, is my notebook capable of running ubuntu efficiently??
I have the LiveCD and I'm trying to install it, but when I'm on step 5/6 I go for the "resize the main partition and use the freed space" option, nothing happens..so i have to cancel the process..
I'm not sure how to make a partition of my hard drive, although I read "partition magic" would help...
any  help you guys can provide, would be hugely welcome..

---

### Post by overdrank on 2007-08-15
> **jocejas3112 said:**
> hello guys..
I've decided to try Ubuntu..
actually I run my HP pavilion dv1000, windows xp, 80gb hard disk drive, 512mb ram, 1.60mghtz processor..
first question, is my notebook capable of running ubuntu efficiently??
I have the LiveCD and I'm trying to install it, but when I'm on step 5/6 I go for the "resize the main partition and use the freed space" option, nothing happens..so i have to cancel the process..
I'm not sure how to make a partition of my hard drive, although I read "partition magic" would help...
any  help you guys can provide, would be hugely welcome..

Hi and welcome, if you have run the live cd with no problem then once you install you should have the same results (in most cases). You may have to defrag windows a couple of time  before you try to install ubuntu and also make sure that the drive is not mounted when trying to install ubuntu. YOu can do this by right clicking on your drive if it is mounted on your desktop with the live cd and select unmount. Good luck!

---

### Post by Hallvor on 2007-08-15
> **jocejas3112 said:**
> hello guys..
I've decided to try Ubuntu..
actually I run my HP pavilion dv1000, windows xp, 80gb hard disk drive, 512mb ram, 1.60mghtz processor..
first question, is my notebook capable of running ubuntu efficiently??


In my experience Ubuntu runs a little slower than a clean install of Windows XP, but faster than Windows XP with more installed applications. Ubuntu does not slow down as much as Windows XP as time goes by. So your notebook will run Ubuntu just fine. I run Ubuntu on a 1,83 mhz AMD with 512 mb ram without any problems. The system is actually very snappy, so I guess I can easily use these specs for a few more years without the need to upgrade.

---

### Post by oeolycus on 2007-08-15
I'm new as well. With your system (which is roughly equivalent to mine, but that doesn't mean results won't vary) I think you'll be fine. Ubuntu runs faster on my 4 year old laptop does than Windows XP did. I had to turn all the graphical settings down on XP, but I've run some zany graphics stuff on this relic with Ubuntu!

I wish you much luck!

---

### Post by iver2435 on 2007-08-15
First of all, I'm glad you decided to try Ubuntu.  I think you'll be pleasantly surprised with the outcome! :-)

Those notebook specs sound great for running Ubuntu, you shouldn't have any problems there.

One thing I'm kind of confused about is are you trying to dual-boot with Windows, or are you trying to wipe the drive and install Ubuntu as the only OS.

If you're trying to do the second option, then I would just choose the "guided" option that erases all partitions and uses the whole hard disk for Ubuntu.

If you're trying to dual boot, how long would you say you wait after clicking the "resize" option before determining that "nothing happened".  The only reason I ask is I have gotten myself in trouble in the past by jumping the gun and assuming programs were hung, when in fact they were just so busy, they didn't have time to tell me :-)

---

### Post by sailor2001 on 2007-08-15
when resizing partition (for dual boot) it does take time to format the free space and prepare it. You have to be a little patient here...I hope you have defragged you xp first.

---

### Post by jocejas3112 on 2007-08-15
thank you very much for your time/help guys...
I am trying to install Ubuntu from the LiveCD..and previously i tried to dual boot from XP but I dont know if i did it correctly...
when i try to install ubuntu, on the "prepare disk space" step, it freezes when i pick the first option "resize master...and use freed space"...nothing ever happens so i have to cancel and i cant proceed...
I dont want to delete XP from my  notebook in case something goes wrong..but im kind of stuck here in the middle of this....any suggestions? comments? help!!!!!!

---

### Post by jocejas3112 on 2007-08-15
I have defragged my hard drive, i have 49% of free space (out of 80gb).. 
On XP i got PartionMagic 8.0, and when i try to creat a new partition on  my local disk (C:) it just doesnt let me, i dont know what im doing wrong, or what am i supposed to do???

---

### Post by LaRoza on 2007-08-15
> **jocejas3112 said:**
> I have defragged my hard drive, i have 49% of free space (out of 80gb).. 
On XP i got PartionMagic 8.0, and when i try to creat a new partition on  my local disk (C:) it just doesnt let me, i dont know what im doing wrong, or what am i supposed to do???

I have never used PartitionMagic, only GParted (link in my sig).

If they are similar, which they should be, you must first shrink the partition and create a new one with the freed space.

Can you not just use the install cd to resize?

---

### Post by vexorian on 2007-08-15
once you get it running I advice you to try to upgrade to the gutsy kernel: [http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel)

The reason is that there are issues with laptop hard drives in the kernel included with feisty. Downloading and running the script should be easy enough.

---

### Post by dptxp on 2007-08-15
Suggest download GParted, make Live CD like Ubuntu, boot with it, view your partitions and post. You can actually use Gparted to make your new partitions, post if you are confused. 6-8 GB for / (root), 1-2 GB for SWAP, rest /home (ext3 format). Data will go to /home/<user> by default.

Resize your partition first to first 50% or whatever you want. Resize next for / (ext3 format). Resize next for /home(ext3 format). SWAP at the end. 4 partitions, so all can be primary.

---

### Post by jocejas3112 on 2007-08-15
Hey LaRoza..
Im now trying to figure out with GAarted..
I see my 80gb disk, where there's /dev/hda1 37.79gb used / 36.54gb unused ..
unallocated 7.84mb and a third one /dev/hda2 unknown ...

which one am i supposed to resize? or where should i create the new partition? im affraid of formatting my hard drive and losing all my data....any help!?!

---

### Post by jocejas3112 on 2007-08-15
> **dptxp said:**
> Suggest download GParted, make Live CD like Ubuntu, boot with it, view your partitions and post. You can actually use Gparted to make your new partitions, post if you are confused. 6-8 GB for / (root), 1-2 GB for SWAP, rest /home (ext3 format). Data will go to /home/<user> by default.

Resize your partition first to first 50% or whatever you want. Resize next for / (ext3 format). Resize next for /home(ext3 format). SWAP at the end. 4 partitions, so all can be primary.

-------
hey there...
i think i understand you, but not quite sure...im still on GParted..(went out for lunch)..
when i select my hard drive (is this the one i have to make the partition to??) i only have the option resize/move.. so basically..the 6-8GB  (root) and 1-2GB for SWAP, where do i make those changes!?

---

### Post by dptxp on 2007-08-16
> **jocejas3112 said:**
> -------
hey there...
i think i understand you, but not quite sure...im still on GParted..(went out for lunch)..
when i select my hard drive (is this the one i have to make the partition to??) i only have the option resize/move.. so basically..the 6-8GB  (root) and 1-2GB for SWAP, where do i make those changes!?

1) Resize the 80 GB hard disk single partition to say 40 GB.
2) You will get 40 GB unused partition.
3) Resize it to 6-8 GB for / (root), ext3 format. You can make this primary too.
4) Resize the 32 to 34 GB unused balance space to leave 1-2 GB for SWAP. ext3 format.
This will be /home when you install Ubuntu. You can have this as primary too.
5) Last 1-2 GB shall be formatted as SWAP.

Since you are having total 4 partitions, you can make all Primary.

---

### Post by misfitpierce on 2007-08-16
May have bad disc or may need to wait longer on the install part. Your laptop is more than capable to run ubuntu though. Got people on PII with 256 ram running ubuntu :)

---

