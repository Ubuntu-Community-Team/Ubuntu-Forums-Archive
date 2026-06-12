---
title: "Can't get G3 Blue &amp; White Mac to boot after install"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by kitpierce on 2006-06-29
I beat my head against a wall trying to install Kubuntu 5.10 with no success (both with partitioning a separate /home partition and without - [see this post for background]("http://www.ubuntuforums.org/showthread.php?t=183413")) I was still unable to get YaBoot to work. I finally gave up and decided to wait until 6.06LTS was released. Earlier this week, my ShipIt CDs arrived in the mail - so the story continues.

I tried to use the CDs to install a 6.06, but since the Mac evidently doesn't have enough memory, it kept dropping me into a terminal prompt instead of loading the live CD. So I downloaded the alternate CD, and that installation progressed as normal through the entire process. Upon reboot, I again got the unbootable Mac folder/Question mark in the center of the screen. On a whim I decided to use the SUSE10 installation discs, because I noticed they have an option to boot the installed system. To my shock, using the SUSE CD as a sort of "boot-disk" worked like a charm. I am able to then access the Ubuntu GDM and log in like normal. The down side is, I still don't have a working YaBoot and I would like to not have to keep using a SUSE CD to boot Ubuntu - since the process takes about 5 minutes and requires much hand holding by the user.

Since SUSE boots Ubuntu, I know the installation worked and it HAS to be a problem with the boot loader. If SUSE Yaboot works, why doesn't Ubuntu's? I tried using Synaptic to uninstall yaboot (and anything that was installed with Yaboot in the description) and then reinstalling, but that didn't make any difference. Is there a way to copy Yaboot from the SUSE disc to the hard drive? If so please give *very detailed* directions and I will try that. Or can someone point me to a working Yaboot for a blue and white G3 and give some direction as to how to install it locally? I am sooooo close I can taste it, and would very much like to figure out what's going on. Thanks a ton!

PS: I do have the ability to Gedit the yaboot.conf file if that helps any...

---

