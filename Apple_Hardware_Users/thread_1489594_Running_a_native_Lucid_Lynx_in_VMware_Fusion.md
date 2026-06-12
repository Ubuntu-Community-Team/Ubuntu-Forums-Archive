---
title: "Running a native Lucid Lynx in VMware Fusion"
date: 2010-05-21
forum: Apple Hardware Users
---

### Post by Excentrik on 2010-05-21
Hi everyone

I've been trying to get this to work but it seems impossible.
So, I'll recap what I want and what I've done to have it

Until a month ago, I had the following setup on my MacBook Pro 13'' mid 2009:
partition 1 - EFI partition
partition 2 - Win7
partition 3- NTFS data partition
partition 4- Ubutu Karmic Koala
partition 5- OSX Snow Leopard

Everything was working perfectly. Using ReFit I could boot Win/Linux/OSX without any problems.
In OSX, using VMware Fusion, I could boot also from the Windows and Linux partitions (I know it's not officially supported, but it's possible).

After the release of Lucid, I wanted to upgrade to a fresh start, so I cleaned installed Lucid on the linux partition.
With the native boot, everything went ok. Lucid booted properly.

Then I proceeded to see if VMware still worked, but alas, it seems that grub2 can't detect the same linux partition that it detected before, giving a message of no partition found and "ls" under the grub recovery console gives just a "(hd0.0)".

I then tried to install Lucid directly from VMware to that partition and this did work out. So I could boot Lucid from the VMware under OSX.
But this results in the same error message when trying to boot natively :(

So, what I wanted to ask is if there's anyone experiencing the same problems, or has any info on what the problem might be and how to solve it, or even if I have the right partition setup for what I want.

Thanks in advance

P.S. If you need any more info, let me know

---

