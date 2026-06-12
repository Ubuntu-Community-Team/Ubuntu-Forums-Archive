---
title: "Help! Updated and everything died!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-18
Hi, I seem to have a serious problem. I have been using Ubuntu for a short while now and enjoying it very much, even going so far as to consider moving permanently, however, today something happened which has made me rethink, and I am now back in Windows 2000 and in need of help.

First my setup, which is a little odd:
Ubuntu is on the second hard disk, second partition (hdf2).
The main boot partition is Windows 2000 and I use a linux.lnx file to boot Ubuntu (Or GAG).

Generally after an update I would reboot and recreate the linux.lnx file and load from that file.

Today I updated and rebooted as usual but this time Ubuntu refuses to boot, giving me the following rather cryptic error:

```
.15img2EBDA is big; Kernel setup stack overlaps LILO second stage
```

I have a copy of the LiveCD (Not the alternative one) and can boot from this. I tried to re-install LILO but that failed with some equally cryptic message about RAID arrays, of which I have none.

BTW: I'm using LILO and not GRUB because GRUB had problems with my setup and was unable to install itself on hdf2 correctly. This meant that while I could boot from the GAG boot disk I couldn't use a linux.lnx file.

I did try to use GRUB from the LiveCD but that failed as usual.

Please help. I'm totally lost and have no idea what to do next. From the LiveCD I can see and mount my Ubuntu installation but I don't know enough to know if there is anything I can do to it to make it work again.

All the best

Jax

---

### Post by linuxnewbie946 on 2006-07-18
Sounds like you need a updated kernel

---

### Post by Jax Kovak on 2006-07-18
Right. And that means what, and, more to the point, how do I do/get such a thing?

---

### Post by Jax Kovak on 2006-07-18
Well now. Having been pretty despondent and more than a little upset that an OS could just fall over like this I started hunting about.

On this forum there were three other threads with an identical problem to mine and, like me, they seem to have very little activity and what they did get was of no help whatsoever.

However, one of the threads held the answer.

MrCheese found his own cure and it worked for me as well:
[http://www.ubuntuforums.org/showthread.php?t=72237]("http://www.ubuntuforums.org/showthread.php?t=72237")

> fixed it - booted install cd in rescue mode (type "rescue" at lilo prompt), mount all partitions, run "grub-install /dev/hda" (my system is on a laptop, single hdd) replace with the correct device!

I didn't understand that too well but with some experimentation I got it, and, just by way of explanation, this is what I did.

I tried to start Ubuntu as normal but when I got to the usual screen where I could select a kernel or a memory check I elected to enter some kernel options. On LILO this meant pressing TAB.

This dropped me back to a command line which already contained the command to start the currently selected kernel and was waiting for me to add some options.

I typed "rescue" and pressed return and incredibly Ubuntu just booted. Once on the desktop I used liloconfig and everything worked just fine.

A reboot later and everything seems to be just fine except for my faith in Ubuntu as a valid replacement for Windows! Ill still be using it, but Windows will now remain my workhorse while Ubuntu will stay as a hobby horse with a view that one day in the distant future it might be resilient enough to take over.

Right now I cant possibly trust an OS that will simply go belly up like that, for no apparent reason, and in all my years of using Windows Iv never experienced anything like it!

However, it has been a happy end, so thanks MrCheese!

Jax

---

