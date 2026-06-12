---
title: "Dual Boot issue"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-11
When I boot up and have the choice between Ubuntu and Windows, Ubuntu is listed three times.

What is up with that?  Is it on my hard drive three times?  If so, is it using up a ton of my memory?

Thanks,
Lnac

---

### Post by o_fortuna on 2007-04-11
> **awiggin said:**
> When I boot up and have the choice between Ubuntu and Windows, Ubuntu is listed three times.

What is up with that?  Is it on my hard drive three times?  If so, is it using up a ton of my memory?

Thanks,
Lnac
The three listings should all be different -- The regular Ubuntu kernel, Ubuntu kernel in "safe mode" in case you're having a problem, and Memtest86, which tests your memory modules to see if they are working or not. Either way, Ubuntu is only on your hard drive once.

Also, you may have multiple kernels installed (this happens whenever you update). You can remove old ones in synaptic -- just not the current one (it's a really bad idea to delete the kernel, for obvious reasons). Again, Ubuntu isn't installed multiple times, but you may have extra kernels installed, which will waste a pretty good amount of hard-disk space (probably like 20 megabytes).

---

### Post by awiggin on 2007-04-11
How do I remove the old kernels?  I don't want to screw everything up.  I have Ubuntu listed three times (each one is followed by a safe mode - so that's like 6 listings) *and* a memtest, so I need to delete at least two (if not 4) of these.

I opened synaptic package manager, but I didn't know what I was looking for.

Thanks for your help.

L

---

### Post by ParkingBrake on 2007-04-11
sudo gedit /boot/grub/menu.lst

You can take out all the old kernel versions that you do not use but be careful not to delete anything else that might be important.

---

### Post by IndyBob on 2007-04-11
Look at your boot screen and the latest version should be on top ( it will be a higher number like 2.6.17-11 or 2.6.17-10), write down those numbers as that is your newest kernel you want to keep.  Once those are written down, go into synaptic package manager and do a search for linux image and you should then see all your versions with a green box.  Right click on the ones you want to delete and mark them for removal.  Click on update in upper right corner of screen and then once that is complete, click on apply and bingo they are gone.  Then on your next boot you will only see the current version of the kernel, recovery mode and memory test and any additional OS you have on your disk.  You can also take them out of the menu list, but they just aren't in the boot sequence but still on your system.  I'm a noob also and have just started learning what is going on and how to change things and also freaked out when the first update was done and suddenly my grub menu was listing several versions of the kernel.  Hope this helps.  You can search this forum for almost any problem you have and get a solution/fix.  Everyone is really helpful.

---

### Post by awiggin on 2007-04-12
Thanks guys - and INdyBOb, I followed your directions.

As soon as I reboot, I am hoping there are no troubles.

Peace-

-Lance

---

### Post by IndyBob on 2007-04-12
awiggin,

I hope that worked for you.  I searched for hours in the forums to find the answer when it happened to me.

---

### Post by awiggin on 2007-04-12
IndyBob - 

Worked like a charm.  Thanks for the help.

-Awiggin

---

