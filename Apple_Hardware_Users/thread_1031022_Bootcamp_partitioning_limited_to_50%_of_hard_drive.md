---
title: "Bootcamp partitioning limited to 50% of hard drive?"
date: 2009-01-04
forum: Apple Hardware Users
---

### Post by joka. on 2009-01-04
I'm about to get a Macbook Pro 5,1 and triple boot with either XP or Vista and Ubuntu 8.10. However, I noticed that Bootcamp is limited to only partition the hard drive so 50% of it is for OS X. Is this true? or is up as much as you want but you must leave 5GB of free space for OS X? I was playing around the the MBP's in the Apple store and I wasn't totally sure. I want to make the Mac's partition as small as possible. What is the smallest partition you can make the OS X? This would be my first Mac, so I'm not too familiar with Bootcamp nor OS X.

I'm going to follow the directions listed here for Mac OS X, Vista/XP, and Ubuntu: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I also found this link: [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)
Is this to resizing the partitions AFTER they've been partitioned before? or is this for customizing how big you want your partitions to begin with?

I'm kinda confused about these few things and want to figure it out before I get such an expensive machine so anything you can tell me would be great. Thanks for all your help.

---

### Post by mkvnmtr on 2009-01-05
First I have no experience on the newer macs but I have to wonder about why you would use Bootcamp when there are open source bootloaders that will work. I believe I saw that bootcamp takes several MBs of space and the others use much less. I coould be wrong but I would recomend some research into just what is the best way to triple boot. The mac salesmen are of course tell you you can only do it with a mac product. You might also think about using the others in a virtual install. You will find there are a lot of people in this forum with a lot of experience on those machines so take your time and listen to what they have to say.

---

### Post by cyberdork33 on 2009-01-05
It is best if you do not post the same question in more than one place. It makes support very difficult.

Please refer to your original thread here:
[http://ubuntuforums.org/showthread.php?t=1030077](http://ubuntuforums.org/showthread.php?t=1030077)

> **mkvnmtr said:**
> First I have no experience on the newer macs but I have to wonder about why you would use Bootcamp when there are open source bootloaders that will work. I believe I saw that bootcamp takes several MBs of space and the others use much less. I could be wrong but I would recomend some research into just what is the best way to triple boot. The mac salesmen are of course tell you you can only do it with a mac product. You might also think about using the others in a virtual install. You will find there are a lot of people in this forum with a lot of experience on those machines so take your time and listen to what they have to say.

Just FYI, Bootcamp is preinstalled on Leopard (and is the only version of Mac OS that you can use it with now), so the space thing is not really an issue.

Also, Bootcamp is not a bootloader. it is a tool that will help partititon your drive. The "bootloader" portions of what make "Bootcamp" are in the Mac EFI firmware.

---

