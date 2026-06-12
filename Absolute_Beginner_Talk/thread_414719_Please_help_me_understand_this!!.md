---
title: "Please help me understand this!!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-20
So I got the latest version of xubuntu today, I tried a fresh install.

I ran into a bit of a problem with the HD pation (step 4)
(see more about that here:
[http://ubuntuforums.org/showthread.php?t=414420&highlight=zazen666](http://ubuntuforums.org/showthread.php?t=414420&highlight=zazen666)


Finally, regarding partitioning the HD, by selecting "Manuall"  and accepting the default for ext and swap, Xubuntu installed fine.

However, by clicking on the destop icon "File System", it appears that out of my 40gig hard drive, 8 gigs were used to install? That doesnt seem rigth to me (especially since it should only take 1.5 gigs), but the file mangaers says, 22 items, (8.6mb)free space 32 gigs.

Can anyone explain this? I want to use all avaible space since my llaptop is small. Did I make a mistake on the install?
-thanks

---

### Post by Bachstelze on 2007-04-20
In a terminal :

```
df -h
```

and paste what you get.

---

### Post by alexlex on 2007-04-20
did you take in consideration you have 1 partition for boot one for root one for home and one for swap?

---

### Post by zazen666 on 2007-04-20
> **HymnToLife said:**
> In a terminal :

```
df -h
```

and paste what you get.

This is what I get

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  1.5G   33G   5% /
varrun                252M   96K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  104K  252M   1% /proc/bus/usb
udev                  252M  104K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volat

---

### Post by zazen666 on 2007-04-20
> **alexlex said:**
> did you take in consideration you have 1 partition for boot one for root one for home and one for swap?

if i understand my computer correcntly, I dont *really* have 40 gigs, but rather 37.26 (that is using a program that let me see that actually HD and size)

I know I used 1.5 gigs for the swap

And install takes 1.5

so, 37.26-3 should be 34.26 free, right?
And by the way, why does Sony advertise a viao as 40 gigs if is really less?
Thank for helping me understand my computer

---

### Post by Bachstelze on 2007-04-20
Your hard drive is 36 Gib large and you have 1.5 GiB used, what's the problem ?

---

### Post by AAM on 2007-04-20
just a small point, zazen666

you might want to go back and reinstall your OS and when you mannually partition this time creat three partitions:

1. a / partition (bootable & ext3) of 8GB size
2. a swap file that is twice your RAM in size
3. a /home partition (non-bootable & ext3) of the remaining space

In this way if you decide to install a new OS (Xubuntu 7.04 ... 7.10 ... etc) you won't lose all of your home files in the upgrade. Seems you're at the start so now is the time to set this up. No doubt you will remember the advice when it's too late!

Just a suggestion, do with it what you will,

AAM

---

### Post by zazen666 on 2007-04-20
> **AAM said:**
> just a small point, zazen666

you might want to go back and reinstall your OS and when you mannually partition this time creat three partitions:

1. a / partition (bootable & ext3) of 8GB size
2. a swap file that is twice your RAM in size
3. a /home partition (non-bootable & ext3) of the remaining space

In this way if you decide to install a new OS (Xubuntu 7.04 ... 7.10 ... etc) you won't lose all of your home files in the upgrade. Seems you're at the start so now is the time to set this up. No doubt you will remember the advice when it's too late!

Just a suggestion, do with it what you will,

AAM

Hello AAM,
Thanks for the advice. I do want to try that, as I had read that was the best way. The problem is that when I attempted to manually repartion the HD I kept getting errors (i assume the math was off) untill i accepted the defaults.  
Tomorrow, I will give it a try again using your suggestions.  
thanks again

---

### Post by zazen666 on 2007-04-20
> **AAM said:**
> just a small point, zazen666

you might want to go back and reinstall your OS and when you mannually partition this time creat three partitions:

1. a / partition (bootable & ext3) of 8GB size
2. a swap file that is twice your RAM in size
3. a /home partition (non-bootable & ext3) of the remaining space

In this way if you decide to install a new OS (Xubuntu 7.04 ... 7.10 ... etc) you won't lose all of your home files in the upgrade. Seems you're at the start so now is the time to set this up. No doubt you will remember the advice when it's too late!

Just a suggestion, do with it what you will,

AAM


Ok, herer is the issue I run into:

I try to do Manual. I erase all the old partitions.  I attemt to set up a new patition as per your advice.

I can set up the swap file no problem.
I *assume I am setting up the /   partition correctly.  I set it to 8 gigs I select "use as: ext3" and "Mount point:  /"

So far seems ok?

Next I try the a /home partition (non-bootable & ext3) of the remaining space

Here is the probelm: the "Use as:" option dos not allow me to set it to ext3 &non bootable"
Also the "mount point"  offers no options.

I am not clear on this, so can anyone give advice?
thanks

---

### Post by Bachstelze on 2007-04-20
Soory, can't help you with that as I always use the Alternate CD to install Ubuntu. You could try it too, it is far more powerful and reliable...

---

### Post by zazen666 on 2007-04-20
> **HymnToLife said:**
> Soory, can't help you with that as I always use the Alternate CD to install Ubuntu. You could try it too, it is far more powerful and reliable...

where can i download that (for xubuntu0?

---

### Post by Bachstelze on 2007-04-20
At the same place you got your Live/DEsktop CD from.

---

### Post by AAM on 2007-04-20
zazen666,

there is something about advising to **unmount** the disk before trying to partition. That's one place to start.

I also found the same behaviour, allowing me to partition one but not all partitions. I seem to recall leaving the job partially completed and then rebooting. Reassigning the partition was easy and I was able to finish off the remaining partitions. There also seemed to be much fewer problems with the text installer than the liveCD installer, with regards to partitioning.

Good luck!

---

### Post by zazen666 on 2007-04-20
I got it worked out using gpation. thanks alot, aam expecially

---

