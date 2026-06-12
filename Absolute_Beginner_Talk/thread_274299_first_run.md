---
title: "first run"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Knowle on 2006-10-09
I've been a huge WinXP user and I'd like to start trying linux distros so I figured Ubuntu would be the best for my first time. I downloaded it and burned it to a CD then tested the LiveCD out it worked great but I have no internet. I would also like to keep my copy of Windows XP on my hard drive so I could dual boot until I am confident I can use Ubuntu. So when I had booted into the LiveCD I was wondering a few things:

1. Should I use the Gnome Partition Editor(while using LiveCD) or will it be done for me when I install Ubuntu to my hard drive? How big should the partition be? 50GB or more? Once this particular partition is made would I be able to increase it later on if I needed to(without damaging what was already added to it)?

2. I connect to the internet through a wireless USB Adapter(the full name for it is "Lan-Express IEEE 802.11 USB Adapter") and I guess I would use something like a ndiswrapper to get it to work? I'm not sure how I would go about doing that.

All the help I can get would be greatly appreciated.

---

### Post by meng on 2006-10-09
1. It will be done during the install step. I would not advise pre-partitioning (i.e. partitioning before install) unless you run into problems, as my impression is that more problems are likely to arise by pre-partitioning than not.

2. ndiswrapper is a means of using Windows drivers for wireless cards (the *.inf files) in Linux.

---

### Post by timnoc1456 on 2006-10-09
I too am new! but this much Iam sure, since I've installed and re-installed Ubuntu 4-5 times. There is no need to use Gnome Partition while using Live CD, just click the the install icon on the desktop. From there on the Installer wizard or whatever (I forgot) will take over. It's much, much easier and clearer then when you install WinXp not to say of Win98. All you Windows partion will be shown as either ntfs/fat, the free space as un-allocated. If you don't want to distore your datas or the windows installed in other partition ntfs/fat never choose it; I did it once. The linux I think always needs two partition 1(one) as / (root) partition and the other as swap (partition). The other options are really self explanatory in the installation of Ubuntu 6.06, its just point and click.

Hope this helps you.

---

