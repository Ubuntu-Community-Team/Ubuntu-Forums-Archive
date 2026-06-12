---
title: "I fudged up"
date: 2010-10-07
forum: Apple Hardware Users
---

### Post by thomastheengine on 2010-10-07
I want to triple boot an iMac with OS X 10.4, OSX10.6, and Ubuntu. I've done this before and haven't had any problems but this time I made a mistake. Typically I start out by throwing in the Mac OSX 10.4 installation disk, create 3 partitions, and install it to the first one. Once installed I boot into the operating system, download and install the rEFIt bootloader. And that's where i made my mistake - I got overanxious and skipped the rEFIt step and went right ahead and installed Ubuntu.

So now GRUB loads up at boot and since it doesn't have support for bluetooth keyboards, and because I don't have any other keyboard at the moment, I'm forced to boot into Ubuntu. 

I've been dinking around with this for a couple of hours now and have managed to edit GRUB to default boot into OSX, but the screen resolution is messed up and won't let me go higher than 1152x864.

So I decided I'd be better of just starting all over again by reformatting, repartitioning and reinstalling OSX. 

But, and here's the ultimate problem I face, the OSX installation disc won't load at startup.

Does anyone have any suggestions?

---

### Post by jwhendy on 2010-10-07
Do you ever get to a point where you see the gray screen with the Apple logo? If so, you should be able to hold the option key during boot and see a list of bootable devices. I'd try that. If you are going through grub, boot OSX and hold option as soon as you press Enter to boot OS X. Keep holding it and hopefully some images of hard drives and the CD will pop up for you to choose.

---

### Post by jwhendy on 2010-10-07
Crap -- no keyboard. Just re-read that. No idea, then.

---

### Post by cgroza on 2010-10-07
Start over I guess.

---

