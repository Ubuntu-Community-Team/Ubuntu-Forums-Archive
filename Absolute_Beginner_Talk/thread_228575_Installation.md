---
title: "Installation"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by caldwdp on 2006-08-03
At present I have several computers with two operating systems on them. Both puters have Win XP and another Linux operating system installed.
I want to install UBUNTU on both computers, and get rid of the other Linux system. Can someone tell me if I can have UBUNTU just write over the existing portion of my hard drive currently occupied by the existing Linux system and still save the Win Xp system or will UPUNTU try too partition the hard drive and install itself, leaving me with three operating systems?? I would just like to have UBUNTU just install itself in place of the existing linux system, it this possible?????  
Thanks
Dave

---

### Post by hfthomp on 2006-08-03
I'm not sure if you are actually supposed to, but I did just what you are asking last night.  In my PC I have a 250GB hard drive with all my XP stuff on it and a 40GB hard drive that I had Fedora on.  When I went through the installation I just choose to install it on the 40GB drive and Ubuntu wiped everything off of there and then installed fine.

---

### Post by ewl1217 on 2006-08-03
This is possible and easily done. Now, I'm assumnig you need nothing on the existing Linux partition. If you do then back it up before the installation. I also reccomend that you back up everything important on the hard drive.  When you get to the partitioning step of the installation, choose to do it manually. **Don't let it do automatic partitioning.** From there, you have two options:[LIST]
[*]If you are happy with the size of the Linux partition, just choose to use that as your root ( / ) partition. Make sure you format it. You can reuse your swap partition (if you have one) without formatting it.
[*]If you would like to resize the partition(s), then delete the Linux partitions. **Don't delete the Windows partition. If you want to resize the Windows partition, then defragment it in Windows before the installation.** Create your Ubuntu partition(s) in the remaining space as you see fit.[/LIST][SIZE=4]**[COLOR=Red]WARNING: DO NOT FORMAT YOUR WINDOWS PARTITION! IF YOU DO, YOU WILL LOSE ALL THE DATA ON IT![/COLOR]**[/SIZE]

---

