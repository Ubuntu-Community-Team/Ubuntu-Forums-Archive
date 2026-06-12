---
title: "Dual boot Ubuntu and OS X 10.4 (Tiger) on Intel iMac"
date: 2007-10-11
forum: Apple Intel Users
---

### Post by Mbengi Bongi on 2007-10-11
I am currently mainly using Mac OS X 10.4 on my Intel iMac, but am soon going to be doing a system reformat.

I am thinking about doing a dual boot with Ubuntu (my fave Linux distro) and Mac OS X, how do I go about this?  I know the drill with x86 machines but not Macs! 

I was a full time Ubuntu user before I got my iMac (as a present) but have got a bit rusty now! 

Please help :popcorn:

---

### Post by czechman86 on 2007-10-11
this should provide all the answers to your questions at the moment:
[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

---

### Post by Greywhind on 2007-10-11
That guide worked for my Intel iMac, which is probably an earlier revision than yours, but it should be similar.

---

### Post by cyberdork33 on 2007-10-11
In the OSX installer, create two partitions the sizes that you want, then install OSX to the first partition. Then boot the Ubuntu cd, and on the partition part, delete the second partition and then tell it to use the free space.

And don't forget to install rEFIt (in OSX)

---

### Post by ItsMitsHere on 2007-10-13
> **cyberdork33 said:**
> In the OS installer, create two partitions the sizes that you want, then install OS to the first partition. Then boot the Ubuntu cd, and on the partition part, delete the second partition and then tell it to use the free space.

And don't forget to install rEFIt (in OSX)

Thats exactly it...

For how to do it see [http://ubuntuforums.org/showthread.php?t=560644]("http://ubuntuforums.org/showthread.php?t=560644")

post back if any problems. its for macbook though but i'm sure it will work on any mac!

---

### Post by jacrider on 2007-10-17
I am about to buy one as well.  I understand I can use either the 32 bit or the 64 bit versions?  Or 64 bit only.

Thanks.

---

### Post by cyberdork33 on 2007-10-17
> **jacrider said:**
> I am about to buy one as well.  I understand I can use either the 32 bit or the 64 bit versions?  Or 64 bit only.

Thanks.
either.

---

### Post by enricesena on 2007-10-19
I have a 2nd gen MB C2D (late 2007) with OSX and rEFIt installed. I've also partioned the hard disk with a Linux and a swap partition during a Debian installation. Now I want to try Ubuntu Gutsy and reading the wiki page I didn't note anything about rEFIt. During the installation I think I should format the 2 partitions erasing all previous data and creating a new ext3 and swap filesystem. Is there a section during the installation process where you can do this? (I don't need to repartition the disk and GPT and MBR table are already syncronized).

---

### Post by cyberdork33 on 2007-10-19
> **enricesena said:**
> I have a 2nd gen MB C2D (late 2007) with OSX and rEFIt installed. I've also partioned the hard disk with a Linux and a swap partition during a Debian installation. Now I want to try Ubuntu Gutsy and reading the wiki page I didn't note anything about rEFIt. During the installation I think I should format the 2 partitions erasing all previous data and creating a new ext3 and swap filesystem. Is there a section during the installation process where you can do this? (I don't need to repartition the disk and GPT and MBR table are already syncronized).
When you get to the partitioning section, choose "manual" and you will get a list of the partitions on your drive. Select the check box for the parition you want to format (old debian partition) and make sure to use the "edit partition" button to make sure you partitions are mounting in the places you want them to. (I think it tries to mount the EFI partition by default, you don't really want it to.) Then continue with the install. You might get an error about FATs not matching, just ignore it.

---

