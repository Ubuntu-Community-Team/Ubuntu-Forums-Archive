---
title: "Installation options"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by canadianwriterman on 2005-09-21
This posting is a bit vague, but I'm sure someone here knows what I mean, so here goes.

When I installed Ubuntu, one of the windows offers various option, such as taking over a whole hard drive, setting up a partition, etc. Two of the options (here's the vague part, because I didn't write it down) say something like "take over a hard drive" and then a similar one that says "take over a hard drive with XXX," the "XXX" being three letters. There is no explanation during the install of what the difference is between these two options.

Can anyone enlighten me, in case I need to reinstall and can select a better option than I did (I selected plain, old "take over a whole hard drive.")

Thanks a million.

---

### Post by SilentCacophony on 2005-09-21
Sounds like the partition setup to me. You have to be careful there if you have any partitions on the drive that you want to keep.

The way I handle it is to use my favorite partitioner (Ranish PM in my case) to set up the main and swap partitions beforehand, then select the *Manually setup partitions* option during the install, telling it to mount the main one as root (/) and the swap one as swap. If you already have a usable swap, it'll usually select that automatically.

---

### Post by canadianwriterman on 2005-09-21
Thanks for your reply!

No, this is a drive that I want to take over completely, so there would not be any existing partitions left on the drive after the install... only the partitions that Ubuntu would create.

What I'm referring to is two install options: one to take over the hard drive, and the other to take over the hard drive "with XXX," I just can't recall what the three letters were, but I think there was a letter "V" in there somewhere. Unfortunately, I can't find any documentation that details the installation process.

---

### Post by SilentCacophony on 2005-09-21
Well, I'm not sure what that would be. Where I was referring to would be the first **[COLOR=Red][!!] Partition disks[/COLOR]** requester from the install.

There is a page with some screenshots of a typical install [here](http://mrbass.org/linux/ubuntu/install/), which should look similar to what yours did (would look different in some setups.) Does that jog your memory at all?

---

### Post by aragorn2909 on 2005-09-21
[QUOTE=canadianwriterman]..."take over a hard drive with XXX," the "XXX" being three letters. There is no explanation during the install of what the difference is between these two options....[/QUOTE]

I think those 3 letters you are referring to are LVM=Logical Volume Management

---

### Post by aragorn2909 on 2005-09-21
This [site](http://tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html) gives an excellent explanation as to what LVM is and why you might use it.

---

### Post by az on 2005-09-21
1.  The default for the new version of the installer (breezy) is to find a partition that has enough room on it to split and to offer to split it for you.  This makes the whole process a *lot* easier, especially to people  who are afraid of making a mistake.

2.  Better help pages for the installer would be a terrific feature request for the doc team.  Would you check bugzilla to see if someone already has asked?

---

### Post by canadianwriterman on 2005-09-21
Thank you, all. Yes, it was LVM that I was referring to. I'll check out the Web site for the advice on LVM and bugzilla for a request for better install documentation that explains LVM as an option.

---

