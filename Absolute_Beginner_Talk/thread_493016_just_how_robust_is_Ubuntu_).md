---
title: "just how robust is Ubuntu? :)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by wog on 2007-07-05
Just to check.

If I move a linux hard drive to a new machine, I'm going to have to reinstall linux on that drive, right? Linux won't automagically figure out what it's new environment is and cope?

I wasn't sure if Ubuntu was quite *that* robust. :)

---

### Post by moredhel on 2007-07-05
I did that, and it worked :) Give it a try ;)

EDIT: It's not like windows when i change my dvd-rw and it says i'm on a new pc and i'm invalid. >_>

---

### Post by overdrank on 2007-07-05
> **wog said:**
> Just to check.

If I move a linux hard drive to a new machine, I'm going to have to reinstall linux on that drive, right? Linux won't automagically figure out what it's new environment is and cope?

I wasn't sure if Ubuntu was quite *that* robust. :)

Hi I have moved several drives with ubuntu on them to different machines and the worst that I have had to do is reconfigure the xorg. It was a great surprise to me that day when I tried the swap and it booted right up. ;)

---

### Post by gn2 on 2007-07-05
I would be very disappointed if it didn't work.

I did exactly the same thing with Windows XP, moved the HDD from an AMD Socket A PC to a Core 2 Duo PC and it booted first time, detected new hardware and sorted itsself out with very little help other than some drivers.

---

### Post by sailor2001 on 2007-07-05
> **gn2 said:**
> I would be very disappointed if it didn't work.

I did exactly the same thing with Windows XP, moved the HDD from an AMD Socket A PC to a Core 2 Duo PC and it booted first time, detected new hardware and sorted itsself out with very little help other than some drivers.

I think it depends a lot on the machine........I tried that on a sony with no luck.....but from emachine to hp no trouble at all

---

### Post by Nekiruhs on 2007-07-05
You'd be amazed at just how robust Linux is in General. I've do this all the time. I boot Kubuntu from a Portable HD and use it at my friends house. All I ever have to do is change the xorg.conf for there driver/gfx card. Thats a pretty painless step.

---

### Post by Nikron on 2007-07-05
Probably depends on how much you enabled in the kernel. (If you still use -general, switching should be fine).  I couldn't boot of this kernel in another machine unless it had pretty much the exact same specs.

---

### Post by jvc26 on 2007-07-05
I've switched HDDs with no issues in the past.
Il

---

### Post by Yoooder on 2007-07-05
> **wog said:**
> Just to check.

If I move a linux hard drive to a new machine, I'm going to have to reinstall linux on that drive, right? Linux won't automagically figure out what it's new environment is and cope?

I wasn't sure if Ubuntu was quite *that* robust. :)

It really depends on whether or not you have recompiled your kernel for your specific machine.  If you don't know what I'm talking about, then you should be good to go.

A brief explanation:

The Linux Kernel contains the majority of drivers for a huge array of hardware (386-686/SPARC systems/Mac systems...etc).  Put simply it has drivers for the vast majority of hardware both new and old.  The default Ubuntu kernel ships with drivers to support nearly any machine it will run on--which is generally an x86 PC.  This means the LiveCD and installed distro are compatible with as many machines as possible.

If you are a true Linux geek/hacker you will probably recompile your kernel to include only the relevant drivers to your machine.  It's a common task and is covered in many Linux books/tutorials as it emphasized Linux's flexibility.

---

### Post by wog on 2007-07-06
Success! (Mad Scientist laughter) It's alive!!!

Thanks everyone. I just powered down, pulled out the drive from the old machine, plugged it into the new one, and booted up. Everything started up with absolutely no problems, aside from a little speed issue. It seems to have worked itself out after a few hours, pretty much on its own (or I've gotten used to it).

This seems phenomenal to me. Windows 98 always seemed to require a complete reformatting when doing this sort of drive swapping.

---

### Post by twiceasworn on 2007-07-06
yeah, it is really touch and go with doing something like that though.  Most of the time something is amiss after you migrate the new drive.  Like someone mentioned earlier, most of the time xorg is screwy.

edit:  I am glad you got it working though :)

---

