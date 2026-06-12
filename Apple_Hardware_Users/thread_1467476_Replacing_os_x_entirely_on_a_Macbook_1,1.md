---
title: "Replacing os x entirely on a Macbook 1,1"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Yarui on 2010-04-30
I have a first generation Macbook that shipped with Tiger.  I don't often use the os x partition anymore, as I installed Windows XP on a 15 gig partition back when bootcamp was still in beta and I normally use that when I'm on my laptop.  Since Tiger is rather old and the only reason I would want to upgrade to leopard is to have access to bootcamp again (they disabled access to the bootcamp application in os x, but I can still boot into windows), I have been thinking about wiping out my os x installation and using ubuntu instead.  Does anyone have any thoughts on the pros and cons of totally removing os x?  The main reason I hesitate to just jump in and do it is because if I decide to install os x again I won't be able to install bootcamp again, unless I buy leopard.  If I wipe out os x and install ubuntu, will I still be able to access windows in the same way?  Windows uses bootcamp drivers to run properly, so I have never quite been sure if it is pulling something off of the os x partition or if it is totally standalone.

---

### Post by untmdsprt on 2010-04-30
If you're wanting to also put Ubuntu on your Mac, you need to have a Mac partition to run rEFIt. Bootcamp will probably not be used anymore. Partition your drive into three parts giving each part as much space as you'll need for each OS. Install the Mac one first, install rEFIt, then proceed to the next OS. There are wonderful pages on ubuntu if you want to search for how to dual or triple boot your computer.

Make sure you back up your files first because you will be erasing the drive.

---

### Post by Yarui on 2010-04-30
Thanks for the response.  I have already backed my files up just in case I decide to wipe everything.  I don't really want to have OS X at all anymore if I don't have to.  My brother tells me he successfully installed Ubuntu as the sole operating system on a Macbook not too long ago, so I assume this is doable.  You suggested that I need to have OS X so that I can install rEFIt, but is rEFIt really necessary?  I was under the impression that it was just a nice looking boot menu for users that don't want to see the grub.

---

### Post by untmdsprt on 2010-05-02
Personally I don't see the need to wipe off OS X entirely, but since you have an old Macbook, it might be the best thing.

You have two choices then for what you want. A dual boot of Ubuntu, and Windows or a single boot of Ubuntu and then using Virtualbox ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)) to run Windows.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) - this will give you some ideas about what you need to do.

---

