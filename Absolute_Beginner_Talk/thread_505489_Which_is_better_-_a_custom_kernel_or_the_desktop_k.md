---
title: "Which is better - a custom kernel or the desktop kernel for a server configuration"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by bdk6m2007 on 2007-07-20
Sorry for the long post but there's a story to share and a request for info......

I installed ubuntu 7.04 server on an Advantech ARK 3881 small computer (I'm looking for a lightweight server for an embedded type application).  When the install completed I rebooted and got some scary IRQ 14 error message and what looked like a register dump, etc.  After some googling I discovered that Pentium M processors have a problem with the kernel config option HIGHMEM64G which is set in the standard server kernel, but not in the desktop one.

So I re-installed using ubuntu 7.04 desktop, downloaded the kernel source package, updated the server config file to **not** use HIGHMEM64G, and recompiled.  I don't just want to use the desktop version because I don't know of an easy way to strip down the desktop version to be essentially like the server version but with the different kernel (and disk space is an issue with my application so I can't really afford anything I don't really need).  I saved my new kernel to a USB stick and then re-installed regular ubuntu server.  I then rebooted using the server disk and did the "rescue a broken system" option; mounted the hard disk; installed my new kernel; rebooted and it works fine so far as I can tell.

So now I'm thinking about maintenance.  I think I just created a maintenance headache for myself - every time there's a new kernel release (that I want/need) I need to recompile the kernel......not a good thing IMO.

After taking a few days to do this it dawned on me that I could have just installed the standard desktop kernel instead of rolling my own - this would mean I can just ride out any upgrades to that using all the standard mechanisms.

So my question for the group is: which is considered better:

1) the evil of needing to recompile the kernel to upgrade it every time, or

2) using the desktop kernel with an otherwise server installation.  Will this work / be stable?  Is it just plain a bad idea?

All input welcomed.  Thanks!

---

### Post by Rocket2DMn on 2007-07-20
For lack of other, more technical responses, I'll submit my opinion.
If you think dealing with compiling the kernel is too much of a hassle, then the desktop edition should work fine.  You can always disable or uninstall a lot of the extra hooha (great technical term) that comes with the desktop edition.
It should work, should be stable, and it is not "just plain a bad idea."  You might just end up spending my time tweaking the configuration to meet your needs.

---

### Post by bdk6m2007 on 2007-07-20
> **Rocket2DMn said:**
> then the desktop edition should work fine.  You can always disable or uninstall a lot of the extra hooha (great technical term) that comes with the desktop edition.


So you're suggesting slimming down the desktop version?  What about using the server version but with the desktop kernel?  Is *that* stable?  If so I think that's the best of all worlds.

---

### Post by Rocket2DMn on 2007-07-20
I really don't know.  Theoretically it should work just fine as long as all dependencies are met, but I've never heard of somebody doing that.  If you've got nothing to lose, give it a try and tell us what happens.
There should be a way to download a specific kernel - you could specify the desktop kernel after the server edition installation.  I looked for a few minutes but haven't found out how yet.  I'll look a little more, you can do the same.

---

### Post by bdk6m2007 on 2007-07-20
Thanks for the input!

>  There should be a way to download a specific kernel

I agree there should be a way, too.  A not so quick work around is probably grabbing the kernel image .deb from apt's cache on a desktop system and then putting in on a USB stick.  Once it's on the USB stick you can mount that from a "rescue broken system" install option and put it on the "broken" system.  This should work but is very cumbersome.  A "standard" way of doing this would be greatly preferable.

Once/If I get this working I'll report results back to this thread.

---

### Post by bdk6m2007 on 2007-07-23
> **bdk6m2007 said:**
> Once/If I get this working I'll report results back to this thread.

OK so I've tried my own rebuilt server image with HIGHMEM64G disabled, linux-image-2.6.20-16-i386 and linux-image-2.6.20-16-generic and they all appear to be working.

I'm not quite sure what's a good kernel regression suite for a situation like this so only time will tell if it works completely or not but so far so good.

---

