---
title: "[SOLVED] Update to 7.10 from 6.04 using CD - partition question"
date: 2008-03-04
forum: Apple PPC Users
---

### Post by jake74 on 2008-03-04
Hello all, please excuse me if this is old ground or incredibly basic, but I'm another FNG.

I've had 6.06 installed on an old 12" Powerbook for a while, and I want to update it to 7.10

I've downloaded the 7.10 install CD, as the Update Manager wasn't working with a few packages, but now when I boot off the CD and start the install process, I'm kinda stumped as to what to do.

It comes down to the disk partitions. I originally partitioned my hard drive into 30GB for Mac OS X, and 10GB for Ubuntu (erased as "Free Space" when I initialised the drive).

When I did the install dance for 6.06, it was easy, use largest amount of Free Space.

Now, I've got a drive that's partitioned, and don't really want to have to back up the Mac OS X partition (I know I should, best practice and all), I just want to install 7.10 over 6.06, but the drive is now partition as so

[FONT="Courier New"]/dev/hda1     Size: 0MB   Used: unknown
free space
/dev/hda3     Size: 29270MB   Used: 20800
/dev/hda2     Size: 1MB   Used: 0MB    Type: newworld
/dev/hda4     Size: 10132MB    Used: 2900MB     Type: ext3
/dev/hda5     Size: 470MB     Used: 0MB    Type: swap
[/FONT]

Question is, how do I just install Ubuntu over the ext3 partition?
If I do Guided - resize IDE1 etc. over hda4, will it partition the drive for the swap sessions and newworld?

Does this even make sense?! :D

thanks for any help
jake

---

### Post by Bruce M. on 2008-03-04
> **jake74 said:**
> Does this even make sense?! :D

Yes!

> **jake74 said:**
> I've had 6.06 installed on an old 12" Powerbook for a while, and I want to update it to 7.10

OLD!  How old?  Are you sure 7.10 will run on it?
Is your CD **Ubuntu** or **Xubuntu** (*Xubuntu is better for older computers*)

> **jake74 said:**
> I've downloaded the 7.10 install CD, as the Update Manager wasn't working with a few packages, but now when I boot off the CD and start the install process, I'm kinda stumped as to what to do.

Which CD?  LiveCD or Alternate CD?

> **jake74 said:**
> It comes down to the disk partitions. I originally partitioned my hard drive into 30GB for Mac OS X, and 10GB for Ubuntu (erased as "Free Space" when I initialised the drive).

> **jake74 said:**
> 
[FONT="Courier New"]/dev/hda1     Size: 0MB   Used: unknown
free space
/dev/hda3     Size: 29270MB   Used: 20800
/dev/hda2     Size: 1MB   Used: 0MB    Type: newworld
/dev/hda4     Size: 10132MB    Used: 2900MB     Type: ext3
/dev/hda5     Size: 470MB     Used: 0MB    Type: swap
[/FONT]

Question is, how do I just install Ubuntu over the ext3 partition?
If I do Guided - resize IDE1 etc. over hda4, will it partition the drive for the swap sessions and newworld?

I'm not sure what newworld is, are you sure it's not a Mac thing?
After all:  29.270MB + 1MB = 30.27MB that you gave to the Mac.

hda4 - is Ubuntu with the ext3 format.
hda5 - Ubuntu's swap

Now the reason I asked if you had the Alt CD, when it comes to partitioning:

hda4 - reformat as ext3 - Mount Point as: / (root)
hda5 - Mount Point as: swap

---

### Post by stream303 on 2008-03-04
No problem.  Those special partitions are normal and necessary for new world ppc.

If you like your old partitioning scheme, the easiest thing to do is to choose **manual partitioning** at the start, and delete the existing 4 ppc ubuntu partitions and let it write the new partitioning scheme, which will just give you your free space back.

Then TAB and use the *go-back button* to reach the point where you can let Ubuntu **guided partitioning** use *free space*!  Bingo.

---

### Post by jake74 on 2008-03-07
Apologies for the late reply. Pretty poor of me considering how quickly you guys came to my aid.

Using a bit of information from each of the posts I decided to Manual edit the partitions and erased hda4, then chose that for the install, everything worked fine. However, I still can't connect to any of my APs, but that's another story...

The quality of 7.10 over 6.04 is a big jump, and I'm looking forward to the final of Hardy Heron.

I'm taking a dead G3 home this weekend to see if I can't get Ubuntu up and running and get my 64 year old dad online!

---

### Post by stream303 on 2008-03-07
> **jake74 said:**
> Apologies for the late reply. Pretty poor of me considering how quickly you guys came to my aid.

No apologies needed.  Glad you were able to get it working.

> I'm taking a dead G3 home this weekend to see if I can't get Ubuntu up and running and get my 64 year old dad online!

Now there's the spirit of Ubuntu!

You might want to check this out and see if it is helpful:

[http://ubuntuforums.org/showthread.php?t=717074](http://ubuntuforums.org/showthread.php?t=717074)

Let us know!

---

