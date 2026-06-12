---
title: "Partitioning Problems"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by knot133 on 2008-04-09
I have been trying to install Ubuntu to my hard drive and I keep getting an error message that says "No root file system defined. Please correct this from the partitioning menu"  whenever I thought I was finished manually partitioning my hard drive.  I did some research and it seems that I need a small volume that is supposed to be the swap volume and a larger volume to which I actually install Ubuntu.  The thing I am sketchy about is when I am editing the second, larger volume I need to designate a root.  Do I just type a "/" and then whatever the root volume device name is or do I need to type something else.  I tried it the first way but it did not work.

Do I need to create the swap file first?  At the bottom of the window it suggests that the swap file needs to be at least 215 MB.  I'm not really familiar with swap volumes or Linux at all so I'm not real sure what I am doing.

The drive is a 320 GB SATA Western Digital hard drive.  The first volume is 152 GB and has a trial version of Windows Vista Business Edition that I need for one of my classes.  The second volume is only a GB big that I had to create for the already mentioned class(it's not important and I can delete it if need be).   The third volume is a 10 GB and is what I have been trying to install Ubuntu on.

Does Ubuntu do well with dual booting?  The drive I use mostly has Windows XP on it(for those keeping score,  I'm trying to triple boot across two hard drives).  Thanks

---

### Post by joshrobinson on 2008-04-09
ubuntu does great dual booting

youll want to take your 10gb partition, and edit the size of it
now if you have 1gb of ram, make it 8gb, if you have 512mb or ram, make it 9gb
(so take 2x your ram off of the 10gb)

now with the resized partition, format as ext3 with mount point as /
now with the small amount of free space, select new, and set it as swap under the filesystem type
it needs no mount point

and that should do it

---

