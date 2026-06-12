---
title: "Taking the plunge for good....."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by cypher_666 on 2007-02-11
hi there.

i switched to kubuntu a short time ago and fell in love, i kept a small windows partition as i didnt have the time due to work to sit and fiddle with my wireless which is unresponsive in kubuntu atm and my ipod wasnt being recognised in amarok.

well i fixed the problem with my ipod and am (hopefully) on the way to fixing my wireless, so my questions is.

how do i go about deleting my obselete windows partition and growing my linux one to use the available space? ive searched on here but cant seem to find anyone whos had problems doing the same.

i have a 20 gig Hd on my laptop, 4 for windows and the rest is linux/swap

thanks in advance for all the help i know i will recieve :)

cheers

---

### Post by seshomaru samma on 2007-02-11
what i would do is :
download gpatred
```
sudo apt-get install gparted
```
use it to format your windows partition as ext3
then mount the partition (instructions [here]("http://www.psychocats.net/ubuntu/mountlinux")) 

i guess you could use gparted to erase the windows partition and expand your linux partition to include the old windows one. i never tried that though...

i would ,however ,wait until i'm 100% sure that i can do everything i want with ubuntu till i get rid of windows.

---

### Post by cypher_666 on 2007-02-11
ill give that a try in a bit, thanks

---

### Post by PurplePenguin on 2007-02-11
Back up any important stuff before playing around with partitions.  I've never lost anything, but it can happen.  I've seen a couple guys on this forum that have lost years of important info because they accidently clicked "format" on the wrong partition during Ubuntu setup. :)

If you do change partitions around, remember that you might have some problems booting into linux afterwards (if your linux partition changes).  You might need to go in with a live disc and manually edit your fstab so it points to the right partitions.  You should be able to keep things as they are, just format your windows partition (I'd stick with ext3), and use it for storage.  This should keep all the partition names the same (and you should be able to boot into linux without playing around with the fstab at all, although you'll want to modify it so you can automatically mount the new storage partition).

The other thing you can do is just format your windows drive and install a different linux distro.  That's what I did... now I've got Ubuntu Dapper and Edgy (which I use 99% of the time), plus PCLinuxOS (also a nice distro) and Sabayon (eye candy that puts Vista to shame, but not yet stable enough for daily use, in my opinion).   When I get bored of a distro, I just format it and replace it with another, always keeping Edgy in its partition for daily use.

---

### Post by cypher_666 on 2007-02-12
well i finally did it and all appears to be well, i have a couple of questions to ask but they can be done in another post, thanks for the help people

---

