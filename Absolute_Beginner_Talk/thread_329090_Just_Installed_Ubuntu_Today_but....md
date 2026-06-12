---
title: "Just Installed Ubuntu Today but..."
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Recondaddy on 2006-12-31
Hello everyone!

It's great to be here.  I've been a slave to the other system for several years, now, but finally stepped into the light, today.

I'm excited about learning all about Ubuntu, but my experience, so far, can be summed up with one word:

Sluggish.

Now, I recognize that the problem likely resides with my machine:

1999 model Dell Dimension L550
550 MHz Pentium III
128 Mb SDRAM
20G Hard Drive
Intel 810e chipset

Yeah -- I know.

Here's my question:  I've ordered (2) 256Mb RAM modules from Crucial, so my machine will soon be maxed out with 512 Mb of RAM.

Should I wait for the RAM and see if my experience improves, or should I go ahead and install Xubuntu, instead?  After all, I'm not planning to upgrade my processor -- just increase my RAM.

Thanks for any help you can provide!

Jeremy

---

### Post by tagra123 on 2006-12-31
> **Recondaddy said:**
> Hello everyone!

It's great to be here.  I've been a slave to the other system for several years, now, but finally stepped into the light, today.

I'm excited about learning all about Ubuntu, but my experience, so far, can be summed up with one word:

Sluggish.

Now, I recognize that the problem likely resides with my machine:

1999 model Dell Dimension L550
550 MHz Pentium III
128 Mb SDRAM
20G Hard Drive
Intel 810e chipset

Yeah -- I know.

Here's my question:  I've ordered (2) 256Mb RAM modules from Crucial, so my machine will soon be maxed out with 512 Mb of RAM.

Should I wait for the RAM and see if my experience improves, or should I go ahead and install Xubuntu, instead?  After all, I'm not planning to upgrade my processor -- just increase my RAM.

Thanks for any help you can provide!

Jeremy

I've also noticed after installs it can be slow.  I have Xubuntu and ubuntu on laptops with 128MB and they seem to run well.

I don't know but I wonder If something goes on n the filesystem on a new install. On the few that seemed slow they did seem to speed up on their own.

Have you tried 

sudo apt-get update
sudo apt-get dist-upgrade

This will get the latest and greatest updates for ubuntu.

On the boot (grub) screen - Reboot and select memtest just to make sure your memory is in good shape.

Xubuntu will use less resources, but the full buntu will be more enjoyable to use for a beginner.

---

### Post by riven0 on 2006-12-31
It shouldn't be more sluggish than xp. But I suggest trying out xubuntu first:
> 
sudo apt-get install xubuntu-desktop

Then to try it: Log out >> Sessions >> Xfce >> Log back in


There should be a noticeable speed increase.

---

