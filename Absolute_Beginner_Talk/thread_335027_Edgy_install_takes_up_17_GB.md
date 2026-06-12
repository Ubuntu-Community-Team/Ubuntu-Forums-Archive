---
title: "Edgy install takes up 17 GB ?????"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by gwilson on 2007-01-09
I tend to divide my drives into partitions about 20 GB in size and play with various installs and operating systems. Usually, Ubuntu takes up a relatively small amount of space and grows as I add programs and play around.  After only a few days, however, I noticed that my recent Edgy install is taking up just under 18 GB of space. Wow!

I did a search for "large" files over 3000 kb (3 MB) and came up with hardly anything at all in this partition. I did attempt to copy a DVD the other day, and thought there might be a lot of junk in some sort of TMP directory, or something. I found some of this and deleted it as well as some ISO files I had on the drive, but I'm still over 17 GB.

Any suggestions about where and how "junk" could be hiding on my partition and how to find it? Since large files didn't turn up, is it possible that there are a million "little" files hidden away somewhere? Where might they be? I did notice that the last OpenOffice update seemed to take forever to download and install. Generally, however, I don't have all that much extra stuff installed on my system, and what there is was all done through Synaptic.

Any suggestions????

---

### Post by taurus on 2007-01-09
Have you look in /root/.Trash directory to make sure there is nothing in your trash bin?  And perhaps a reboot would clean out your /tmp directory.

---

### Post by gwilson on 2007-01-09
Thanks, Taurus.  Found a temporary user that I'd thought I had fully deleted. That user had a .trash folder with about 5000 files in it. Things look better, now.

---

### Post by taurus on 2007-01-09
That's why it's good to every now and then empty the trash bins!  :mrgreen:

---

