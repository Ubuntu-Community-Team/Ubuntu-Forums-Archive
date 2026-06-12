---
title: "VPN and Networks"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by kf4mat on 2007-12-23
Okay, before anyone says not another question on something that has been answered a thousand times. I have been looking through the archives here and elsewhere; also I have been at the bookstore pouring over Ubuntu books but I still have questions.

1.) What is the purpose of a VPN? 

It was my impression that you used one when you had a Linux box and wanted to "network" with a Windoze box. However it appears that I may be misunderstanding something. Unless I have just been reading the beginners stuff it seems to me that its only purpose in life is to allow one to try out Linux without having to install it or partition the hard drive. If that is the case why bother with the hassle and just use a live CD.

I ask this because I have a program I need to use that unfortunately will not operate under Ubuntu 7.04 even with the use of WINE.  When my hard drive exploded a few months ago I installed a new one and because I hadn't made a backup was told by Toshiba it would cost me $75 for a recovery disk. I told them where to put their disk and did a 100% install of Linux and am not looking back. Funny thing is they did send me an XP recovery disk at no charge.

So if you have followed along this far maybe you can help me out. I'm not a real hacker/geek and am nervous about trying to use gparted on this machine (laptop), mostly as I have no idea what I'm doing. Also if I did partition the drive can you use a recovery disk to install XP into it or do you have to have the OEM disks that the idiots in Redmond seem to think you shouldn't get with your PC purchase? Everything I have read about dual booting assumes you already have XP installed and want to include Linux, but I want to go the other way. Is this possible?

Finally, anyone here have in luck in getting Feisty Fawn to be able to network with a Vista machine? I would love to be able to use my printer again......


Tom

---

### Post by wigglydiggly on 2007-12-23
VPN stands for virtual private network.  Its used to connect two computers over the internet.  For example connecting computer 1 at work to computer 2 at home securly through an encrypted tunnel.  It sound like you want to run windows on your linux machine.  You can use a program availible in the repositories called virtualbox.  It creates a virtual machine that you can install additional operating systems on.  After you install virtualbox you can install windows/linux.  Beware that performace will be slower compared to if it was running nativily on the hardware.  Most new computers are more than powerful and any slow down if negliable.  hope this help and gets you looking in the right direction.

---

### Post by kf4mat on 2007-12-23
> **wigglydiggly said:**
>  It sound like you want to run windows on your linux machine.  You can use a program availible in the repositories called virtualbox.

Well I may be wrong but I believe I read that in order to create a virtual box you had to have the OEM disks and that a recovery disk would not work. In my further poking around I have found some info on networking Ubuntu to a Vista system but for that I think I might need to try and figure out how to use Samba. I wish this was easy or that I was smarter.......

---

### Post by wigglydiggly on 2007-12-23
Samba is installed by default I believe.  Under Places>Network>Windows Network you should be able to see any shared folders.  I believe Samba defaults to WORKGROUP if yours is different you can change it by editing /etc/samba/smb.conf.  The file is well commented and there are lots of howto's for samba.

I'm not sure about using a recovery disk with virtual box you are probably right.

---

### Post by kf4mat on 2007-12-24
Thanks for the info, I looked under network places and see an icon for windows network it has nothing in it however. It's a slow tedious process browsing through all the archives looking for the info you need. There are a lot of dead ends out there.

Tom

---

### Post by Znort_Ubern00b on 2007-12-24
[Fairly easy to follow guide for samba]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

try that .

---

### Post by rkd on 2007-12-24
This approach might seem a little drastic, but have you thought about backing up your data files from the Ubuntu installation, then using the restore CD to reinstall Windows onto the computer, then install Ubuntu to dual boot with Windows, then restore your data files that you backed up at the beginning?

It does seem like a lot of work, but you probably already know how to do all the steps.

---

### Post by kf4mat on 2007-12-24
> **rkd said:**
> This approach might seem a little drastic, but have you thought about backing up your data files from the Ubuntu installation, then using the restore CD to reinstall Windows onto the computer, then install Ubuntu to dual boot with Windows, then restore your data files that you backed up at the beginning?

Actually I had given it some thought, I was just not going to mention it as I figured someone would laugh at my work around. It's probably what I am going to have to do...

---

### Post by rkd on 2007-12-24
oops, wrong thread

---

