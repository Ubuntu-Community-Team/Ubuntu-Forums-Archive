---
title: "Can i format an external drive to HFS+ in Ubuntu?"
date: 2012-02-09
forum: Apple Hardware Users
---

### Post by Macfunky on 2012-02-09
I have an external hard drive that i am giving to my girlfriends father, who is a mac user. It had Windows on it previously so it will be formatted to NTFS. As he is just a user and doesn't have a clue about how to format it, i want to do it for him and have it set up, ready to plug in and use. Will i have to format it to HFS+ or is there any other format that mac can read/write to? And if i need to format it to HFS+ how do i do this in Ubuntu? Thanks in advance :)

---

### Post by coffeecat on 2012-02-10
In theory in can be done in Ubuntu, but with limitations. You would use Gparted and you would need to install the package hfsprogs and possibly hfsutils as well, but I believe only hfsprogs is needed for hfs+. You would then need to create a GUID partition table (GPT) from the Device menu in Gparted before creating your hfs+ partition. If the Mac the drive is to be used with is a pre-Intel PPC Mac, then this needs to be an Apple Partition Table ("mac" in Gparted).

Even after all this the filesystem you create with Gparted will be the non-journalled version of hfs+, which is not as robust as the journalled version that the MacOS Disk Utility will create by default.

I have a better idea. :) Why not use your girlfriend's father's Mac to re-format the drive? Would it be possible for you to do that if you are not sure he would not be able to do it himself? The MacOS Disk Utility is very easy to find your way around in. Do you need help with that?

---

