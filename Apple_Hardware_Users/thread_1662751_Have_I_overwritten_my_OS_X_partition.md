---
title: "Have I overwritten my OS X partition?"
date: 2011-01-08
forum: Apple Hardware Users
---

### Post by Lachlan_M on 2011-01-08
(I'm sorry if there's another thread on this.  Actually, most of the threads in the Apple Users subforum seem similar to this one, but none of them seemed quite right, so...)

I just installed Ubuntu on my MacBook.  I intended to install it alongside OS X over an existing Kubuntu partition.  I couldn't make the manual partition editor in the Ubuntu installer work for me, and the automatic installer didn't have an option to install over Kubuntu.  So I just told it to split the 18GB Kubuntu partition between Kubuntu (3GB) and Ubuntu (15GB), figuring 15GB was enough and I could just ignore the Kubuntu partition in the future.

The installer did its thing, but now I can't boot into OSX.  When I turn on the computer, rEFIt doesn't start anymore.  I've tried booting the computer while holding down the Option key, but that only ends up showing me a picture of a hard disk labeled "Windows" (i.e., Linux---Apple's hardware refers to all non-Apple operating systems as "Windows").  Clicking this disk boots into Ubuntu.

Have I inadvertently overwritten OS X?  It certainly looks that way, since Nautilus says I have 64GB of free space on my disk, which would seem to indicate that Ubuntu has taken over a lot of disk territory intended for OS X.

I'm not *that* devastated if I've overwritten OS X, because I have partial backups of my data---although I'd obviously like to get it all back if possible.  Besides, when I still used Windows I always found the periodic hard drive failures and unbreakable boot loops good for a nice fresh start.  And having only Linux on my computer might be an incentive to actually use it, unlike the last two times I installed it, when I defaulted back to OS X within an hour.

Really, the reason I want to know more about my situation is so I can decide what to do next.  If my data really is unrecoverable, then I might as well run the install CD again and tell it to reformat the entire hard drive, and do things more cleanly.

So, my two questions are:

- Have I lost all my data I had stored under OS X?
- If not, how can I get it back?

---

### Post by nevius on 2011-01-08
1. Boot your computer from your mac OS X disc. 

2. Select your native language (unless you like to make things more difficult than necessary).

3. Wait for everything to load up.

4. Open up 'Disk Utility' from the bar on the top of the screen.

5. Check to see if your HFS partition still exists.

There is probably a utility on the OS X install disc that will allow you to set the HFS partition as the startup disk; however, considering that this is the first day I am using a mac, I could probably just as justifiably say that there is a utility that uses unicorn's blood and pixie farts to magically transport your data into 'the cloud'. :)

---

### Post by Lachlan_M on 2011-01-08
Thank you; this idea worked.  The OS X install disk was unable to find an HFS+ partition or designate anything other than Ubuntu as the startup disk.

Your suggestion also gave me the idea of using the partition tool on the *Ubuntu* install disk to look at the partitions directly.  Alas, my OS X partition appears to be gone.  I now have only 3 partitions on my hard drive, and the one that was HFS+ (/dev/sda2) is now ext4.  So that settles it.

Thank you for your help. :)

---

