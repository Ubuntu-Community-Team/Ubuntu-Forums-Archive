---
title: "wipe a hard drive"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by hhhhhx on 2007-12-22
I have a old HDD that has kubuntu installed, and i want to wipe it so that i can make it into a portable HDD, is there a program that can format it for me.

I am using ubuntu right now and the Kubuntu HDD is connected via usb

THX in advance
xhhux

---

### Post by LaRoza on 2007-12-22
See the link in my sig for GParted Live CD.

It can reformat and partition the drive.

For wiping, [http://dban.sourceforge.net/](http://dban.sourceforge.net/), you don't need that most likely.

---

### Post by taurus on 2007-12-22
You can use gparted (System -> Administration) to reformat that external harddrive.  Just make sure you don't mount it first before you reformat it.  And if you don't have gparted, you can install from synaptic.

---

### Post by santiagoward2000 on 2007-12-22
> **xhhux said:**
> I have a old HDD that has kubuntu installed, and i want to wipe it so that i can make it into a portable HDD, is there a program that can format it for me.

I am using ubuntu right now and the Kubuntu HDD is connected via usb

THX in advance
xhhux

Hi!
You can try **GParted** to format it. Personally, I would suggest using a liveCD if you have one around. Use it to log in, connect the HDD and go to **System/Gnome Partition Editor**. If not, I think you can install it from the repositories.
Cheers!

---

### Post by LaRoza on 2007-12-22
> **taurus said:**
> You can use gparted (System -> Administration) to reformat that external harddrive.  Just make sure you don't mount it first before you reformat it.  And if you don't have gparted, you can install from synaptic.

That also is an option, but you will probably find the live cd very handy some day, I use it all the time.

---

### Post by jaakan on 2007-12-22
DBAN is a great tool but it's over kill unless you going to give the drive away and you don't want anyone to recover your old data. I use that and the GParted Live CD... in the end both will do the job.

---

