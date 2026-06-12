---
title: "Ubuntu 6.06 With External HD"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by RaigyCar on 2006-06-02
I'm new to Ubuntu, last week i downloaded the Live CD of version 5.10 and liked the operating system.

Last night i downloaded 6.06 and think it's even better.

I wish to install 6.06 on an external HD i have.  It will be used with my HP ZV6100 laptop.

I looked at the steps to install Ubuntu last night from the live cd.  I have a couple of questions. 

When it comes to the part of the installation when it asks me where i wish to install ubuntu, and select my external hard drive, it will install.

So when it installs on the external hard drive and i boot up my laptop (when the external HD is plugged in) will it ask me if i wish to boot Windows or Ubuntu??

And if i boot my laptop without my external HD plugged in Windows will boot normally?

Plus it is safe installing Ubuntu on an external HD, i don't want my windows to mess up.....

Another thing was that i have wireless on my HP ZV6100 laptop, is it easy enough to configure wireless through ubuntu.

Sorry if i have ranted on a bit.

Replies appreciated :)

---

### Post by jorn on 2006-06-02
During installation you will be asked where to install grub. The default is Master boot record (MBR) on the first drive (hda). This is a small app. that gives you choises what os to boot. So:

On startup it will ask you what os to boot.
If the external is unconnected you can choose to boot mswindows
Whether it is save otr not depends on what you mean.
Wireless I don't know anything about

---

### Post by bruenig on 2006-06-02
> So when it installs on the external hard drive and i boot up my laptop (when the external HD is plugged in) will it ask me if i wish to boot Windows or Ubuntu??

Make sure you install the grub boot loader to the master boot record. If you are using the normal 6.06 installer, it does this automatically. If this is done it will ask you upon boot up whether or not to choose ubuntu or windows.

> And if i boot my laptop without my external HD plugged in Windows will boot normally?

If you do as I said before and have grub on the master boot record, you will still have to go through grub but I believe (not sure because I have never removed the second drive) windows will be the only listed operating system and will likely be booted into automatically. If not, you may have to choose windows in the list but that will be simple.

---

