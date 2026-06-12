---
title: "I need some help (absolute noob!)"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Wotcher on 2007-05-24
Hi! This is the first time I've been able to connect to the internet with my computer that has Ubuntu installed on it. Now, I'm getting a message saying that there are upgrades that I need to install, specifically 254 of them! I'm running *Dapper Drake*, so I guess my version is a little outdated.

I would like to upgrade to the latest version of Ubuntu. Do I need to install all those upgrades before I upgrade Ubuntu? I think I should also mention that I have no idea how to upgrade the operating system as well.

Please, if someone could help me, I would really appreciate it. If you like to converse with me through email or IM and help me that way, just send me a PM. Thanks :-)

---

### Post by mojo123 on 2007-05-24
well, you can burn a fiesty cd and just do a clean install from that

---

### Post by Terl on 2007-05-24
Probably best if you could download the newest version and do a clean install.  As it is now, you would have to upgrade to edgy then upgrade to feisty and it is not as clean as just doing a direct install of feisty.  That would be my recommendation.

---

### Post by HereInOz on 2007-05-24
You have 3 choices:

1. Install the updates and continue using Dapper - not what you want to do.

2. Upgrade your system to Edgy (6.10) then to Feisty (7.04)

3. Download the iso for Feisty, burn it to a CD and then install it.

Option 3 is probably the best bet, but if you have all your data in the home folder on the same partition as your system, and you format that partition, you will lose all that data.

If you want to do option 2, all you need to do is to open a terminal, and enter:

gksu "update-manager -c"

then your password, and the update manager will then offer you the upgrade to Edgy.  Do that, and then upgrade to Feisty, and you will be there.  

If you download the CD for Feisty, I am not sure if Dapper will allow you to upgrade directly to Feisty using the CD - I have never done it - but it is worth a try.  I would prefer a clean install if you use the CD, but that is personal preference.  

Also I am not sure of the outcome if you install Feisty over the top of Dapper without formatting the partition.  My feeling is that it is not a good idea, but hopefully someone else will have done this and will know more.

What ever you do, backup your data first, in case things go wrong.

---

### Post by Wotcher on 2007-05-24
Hi guys, Thank you for responding so fast!

Ok, so, just to let y'all guys know, Ubuntu is sharing the hard drive with my Windows XP OS. So if I do a clean install, it will only affect the partition where I want it to go, right?

I've only ever installed Ubuntu on my computer once, How would I go about doing a clean install of a higher version? Is it the same way as installing it for the first time on a brand new and empty partition, or is there anything special you have to do like letting the thing know you want it to clean install?

Thanks you guys, I really do appreciate all your help.

[Edit]:
In response to HereInOz: I don't have any special data on my Ubuntu home folder. I am worried about the fact that Ubuntu is installed on a partition of my hard drive and that it's being shared with Windows XP.

---

### Post by Wotcher on 2007-05-25
I'm still interested in knowing how to perform a clean install, and it will not bother my other partition with Windows XP.

> **Terl said:**
> Probably best if you could download the newest version and do a clean install.  As it is now, you would have to upgrade to edgy then upgrade to feisty and it is not as clean as just doing a direct install of feisty.  That would be my recommendation.

---

### Post by init1 on 2007-05-25
In any form of Ubuntu installation, you should be able to select which partition you wish to edit. Make sure you install to the ext3 partition (dark blue in gparted) and not ntfs (dark green in gparted).
Personally, I never upgrade. If it works, I use it. If, however, the OS is unstable (Ubuntu is one of the most stable I have ever used (I have tried about 75)) I may try another release.
You could just backup everything you want to keep (on a separate partition, maybe?) and install from the new disk. But, if you are happy with your release, you could probably do fine with what you have.

---

