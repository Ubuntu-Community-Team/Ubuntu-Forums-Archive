---
title: "OpenSuse 12.3"
date: 2013-04-27
forum: Any Other OS
---

### Post by lukapez on 2013-04-27
i'm a total linux noob, so i'll post my question here, even though i feel it is kinda stupid.
i currently have ubuntu 12.04 and i'd like to install opensuse 12.3. and remove ubuntu. can i do that with saving my data (music, videos, pictures..) and how?

---

### Post by pissedoffdude on 2013-04-28
Yeah, not a problem.  I'm assuming you don't have an external hard drive, as that would be the easiest solution.  So another way to go about it is to figure out the size of the amount of data you want to keep.  Afterwards, you can boot into a live usb/cd, and resize your current Ubuntu drive with gparted.  

If gparted is not on the Ubuntu livecd, install it after you boot it.  Open it, right click on your ubuntu drive, then go to resize. Take off a bit more than you originally calculated, and you'll see see unallocated space.  Format that unallocated space as ext4.  Then boot back into Ubuntu (or do it from the livecd), and copy your data do that ext4 partition you just created. 

Then just install OpenSuse but be sure you don't overwrite the data partition.  Then, if you want really want to re-do everything so that you only have one or two (for the swap) partitions, you can copy your data to the OpenSuse partition and then boot a livecd and use gparted to expand your OpenSuse partition.  

Good luck!

---

### Post by iamkuriouspurpleoranj on 2013-04-28
If you set up a separate /home partition, you should be ok. The main thing would be to ensure the /home partition is simply reused and not formatted. Sadly, openSUSE's installer is a bit (tempera)mental, so it's probably best not to try and wing it as a new user. Try and transfer everything first to a USB or a cloud platform such as Dropbox or UbuntuOne. You'll be much happier that way.

If you didn't set up a separate /home partition, transfer everything to a USB or to the cloud.

Or just give up on this crazy openSUSE idea. The distro's always greener on the other side, you know.

---

