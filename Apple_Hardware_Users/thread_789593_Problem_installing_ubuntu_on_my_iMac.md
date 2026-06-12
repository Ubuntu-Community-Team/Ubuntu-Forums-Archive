---
title: "Problem installing ubuntu on my iMac"
date: 2008-05-10
forum: Apple Hardware Users
---

### Post by OCTOG3N on 2008-05-10
Hi. I have an iMac 20" Alu 2.4Ghz 2GB RAM, 500GB (mid 07 model) and I am trying to install Hardy 8.04 64-bit edition.

I partitioned my hard drive using Boot camp, making a 100GB "Windows" partition and a 300 or so GB Mac partition. So far so good

Then I installed Refit 0.11 using the Mac OSX installer, worked great

Then I booted from the Hardy install disc using Refit. Worked fine

I installed hardy by deleting the windows partition and making free space. Then creating a 100GB ext3 partition mounted at /, again, fine. the Ubuntu installer ran and was done. I restarted and popped out the disc.

Now, I tried to boot Ubuntu through Refit. No luck. I clicked on "Boot Linux from HD" and all I got was an error that said

No bootable device -- insert boot disk and press any key.

The OSX partition boots fine, but not the linux one. So what did I do wrong? Should I try 32 bit instead?

---

### Post by acelin on 2008-05-10
Did you have a swap partition of at least 1 GB?

---

### Post by cyberdork33 on 2008-05-10
I assume you got this fixed since you replied to the thread that has the fix already:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

