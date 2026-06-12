---
title: "Can't boot - Intel Mac Mini Dual Boot"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by Nikolai D. on 2008-05-26
Hi all.

Just installed Ubuntu 8.04 using this how to:
[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Ubuntu_Feisty_On_Intel_Mac_Mini_Quick-Start_Guide?highlight=%28mac%29%7C%28mini%29](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Ubuntu_Feisty_On_Intel_Mac_Mini_Quick-Start_Guide?highlight=%28mac%29%7C%28mini%29)
(Delited windows partition, and told installer to use free space, so it desides swap size.)

So when i boot up i press alt, and only Mac HD appears.
(once, something like a half a year ago, i had already successfully installed using this how to, but now no success.)

So i've downloaded rEFIt and before installing it i've runned Partition Inspector, and heres what he gave me:



*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    144850983  Mac OS X HFS+
 3      144850984    155696687  Basic Data
 4      155696688    156301454  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    156301487  ee  EFI Protective

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 144850984:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 155696688:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap



Any help appreciated.
Havev a nice day!
Nikolai

---

### Post by cyberdork33 on 2008-05-26
what options do you see in rEFIt?

This may be helpful:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by stueng on 2008-05-27
I suggest reading 

[http://www.lostpeg.co.uk/content/view/29/71/]("http://www.lostpeg.co.uk/content/view/29/71/")

and then (the important bit)

[http://www.lostpeg.co.uk/content/view/33/75/]("http://www.lostpeg.co.uk/content/view/33/75/")

---

### Post by Nikolai D. on 2008-05-27
Hi guy's. Thanks for fast reply's. Have not so much time right now to read all the information from the links. Just got quick look at them. And from what i saw i see that i fall under this category:
"If you do not mind having to hold down the option (alt) key when booting your Mac and don't care that the standard EFI boot calls believe your Linux partition is Windows and you do not need or want to triple boot your Mac then you do not need REFIT".

So as it was asked already did i installed refit or not? No, i haven't installed it yet. Just runned the Partition Inspector from rEFIt package. The info that it gave me i've posted already. I hope manage to boot it like that. Without rEFIt.

So that's it. I hope ill get some spare time in the weekends or so. To read some more info.


p.s. Usually i was pretty sure it would work. The installation i mean. Because  some half a year ago had already done it. And it was a successful install. I was usually planning from start to use Ubuntu on mac mini. Bought it only for hardware. But then when i've tried OSX with all those open source ports. Liked it pretty much. But now there are some guys with whom i am studying an IT-support. Who i advice to use Ubuntu. And when they ask what do u use? I'm like OSX.. Don't make a lot of sense. Off course i tell them, doesn't matter for me OSX or Ubuntu, if i only don't have to use Windoze. But still gotta use Ubuntu, to learn it more. And be able to share the os and experience in using it. :)

So any way.

Have a nice day!
Nikolai

---

### Post by cyberdork33 on 2008-05-27
> **Nikolai D. said:**
> "If you do not mind having to hold down the option (alt) key when booting your Mac and don't care that the standard EFI boot calls believe your Linux partition is Windows and you do not need or want to triple boot your Mac then you do not need REFIT".

So as it was asked already did i installed refit or not? No, i haven't installed it yet. Just runned the Partition Inspector from rEFIt package. The info that it gave me i've posted already. I hope manage to boot it like that. Without rEFIt.That is true, but because of a bug in the Hardy installer, you might need to sync the partitions with rEFIt's partition tool, and/or reinstall grub as mentioned in the link I posted. Once you have that fixed, you can delete rEFIt if you desire.

---

### Post by Nikolai D. on 2008-06-05
Hi all, and thank you for information, and reply's.

Ok. Today i stayed home. And didn't go to both school's (day and evening). Can't even walk, stand up right usually. All the day stayed in the bed. But now in the evening decided to move a little bit. In the borders of possible. So any way..

Installed rEFIt. Synced partitions with rEFIt partition tool. Now i get to choose between OSX and GN U. But when i boot i get an error. If i remember it good it's "Cant find bootable device", or something like that. Haven't read info from your link yet. But just wanted to let you know, where it is already now.

C Ya :)

Be well.
Nikolai

---

### Post by Nikolai D. on 2008-06-06
Hi guys.

Okey. I've got Ubuntu booting by reinstalling grub. And then deleted refit and now everything working as i wanted. Thank you very much man.:)

Have a nice day.
Nikolai

---

