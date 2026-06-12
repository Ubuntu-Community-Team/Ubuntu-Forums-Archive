---
title: "building file server with ubuntu/samba"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2005-12-28
Hi:

I have a number of hard drives on Windows machines loaded with music - mp3 files. (No, they are legal.) I'd like to build a file server so that I can play the music on any of the networked PCs/notebooks I have - but am unsure if Samba/Ubuntu can do this as the other computers are running XP. I'd like to connect the mp3 hard drives to the Ubuntu machine, obviously.

Any howtos or advice is greatly appreciated. I have read several posts about mounting NTFS partitions with an Ubuntu machine - I just need something more comprehensive.

I have six hard drives altogether so am looking at connecting several as external firewire drives.

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=GMachine_24]Hi:

I have a number of hard drives on Windows machines loaded with music - mp3 files. (No, they are legal.) I'd like to build a file server so that I can play the music on any of the networked PCs/notebooks I have - but am unsure if Samba/Ubuntu can do this as the other computers are running XP. I'd like to connect the mp3 hard drives to the Ubuntu machine, obviously.

Any howtos or advice is greatly appreciated. I have read several posts about mounting NTFS partitions with an Ubuntu machine - I just need something more comprehensive.

I have six hard drives altogether so am looking at connecting several as external firewire drives.[/QUOTE]
What music player do you use?  I am not 100% sure, but if you are using amaroK, I think you should be able to give it an SMB URL for a remote file.  E.g. SMB://192.168.0.5/my_mp3s/song001.mp3

---

### Post by lleb on 2005-12-28
[QUOTE=GMachine_24]Hi:

I have a number of hard drives on Windows machines loaded with music - mp3 files. (No, they are legal.) I'd like to build a file server so that I can play the music on any of the networked PCs/notebooks I have - but am unsure if Samba/Ubuntu can do this as the other computers are running XP. I'd like to connect the mp3 hard drives to the Ubuntu machine, obviously.

Any howtos or advice is greatly appreciated. I have read several posts about mounting NTFS partitions with an Ubuntu machine - I just need something more comprehensive.

I have six hard drives altogether so am looking at connecting several as external firewire drives.[/QUOTE]


yes samba will do this very nicely.  there are several howtos on the web, but the best ones i have found are for RH.  the smb.comf file is what you need to edit in order to get the linux box setup to share to windows.

once it is up and running either open up the port on your ubunbtu box, or turn off the firewall all together (not the safest way, but will  work if you are behind a hardware firewall).  set it up, and then just map the drives in windows the way you would now in your peer to peer LAN.

---

### Post by simohell on 2005-12-28
Samba is just the thing you need. You could even easily plug in a few Macs with OSX.

Some general recommendations.
1. Get one or two new big harddrives --they will last longer, be faster and use less power.
2. Copy the stuff you have on ntfs-drives to the fileserver-disks (that shoud probably use ext3) -- you can do this via network once you have setup the server.
3. If you use external drives it might be worthwile having them use fat32 -it is probably the best supported filesystem.

For a choise of linux distribution I would recommend Debian 3.1 (Sarge). People are used to telling you that Debian is the most difficult linux and only for hardcore nerds. Well, it hasn't been so for a while now.

Sarge is basically Ubuntu without splash-screens and with more stable software (not as new versions) or actually the other way around.

In the istallation process you need to give you computers name and workgroup and you can select from a list what options you need for your system. You can choose from mailserver, fileserver, printserver, desktop, database-server etc. and multiple choises are available.

For a desktop I think Ubuntu is the best choise, but for a fileserver I always go for Debian -- and I think for a fileserver it is even more easy to install than Ubuntu.

In any case you probably need to edit your smb.conf -file. And it might be that you can mange just with the help of the notes written in the file itself. (File writing permissions for instance)

After that you need to add a user and its password with smbpasswd -command and you have a fully functional fileserver.

---

### Post by GMachine_24 on 2006-01-02
In the past I have used XMMS for mp3 playing - I think. I have not done a lot of mp3 playing on my Linux computer.

As far as using Debian/Sarge - do you think this will be better than going with Ubuntu Breezy? I have some good details on installing and configuring Samba. I have had several people tell me I should just use Breezy.

Thanks for your prompt replies and sorry it took my so long to acknowledge.

gmachine

---

### Post by lleb on 2006-01-02
[QUOTE=GMachine_24]In the past I have used XMMS for mp3 playing - I think. I have not done a lot of mp3 playing on my Linux computer.

As far as using Debian/Sarge - do you think this will be better than going with Ubuntu Breezy? I have some good details on installing and configuring Samba. I have had several people tell me I should just use Breezy.

Thanks for your prompt replies and sorry it took my so long to acknowledge.

gmachine[/QUOTE]


linux is linux.  the distro you choose for this project does not matter.  setting up samba is the same on every distro i have used.  install it, then configure the conf.  end of sotry.  ubuntu is just debian with a lot of the "headache" taken out of the learning curve.  will i switch my game box over to *buntu... no time soon.  will i some day, who knows.  i am comfortable with debian, but that is not the only distro i use.

i own 1 iMAC, i have debian testing and debian unstable on 2 different systems, i have CentOS 4 running on 2 other workstations one being a laptop, and edubuntu running on an other.  the reason i moved the 2nd workstation to CentOS was because it handles NFS way better then debian did.  it does not hang as much, it connects and disconnects much cleaner and does not lock up the system with the LAN or server goes down for what ever reason.

if you were running a pure linux setup and were running NFS, i would sujest going 100% with either RH line (including FC) or SuSe as they seem to handle NFS better then the other distros i have worked with.

also learning about automount was a big help.

---

### Post by GMachine_24 on 2006-01-07
Hi - thanks to everyone for your thoughtful and helpful replies. I have RH 9 and Ubuntu to choose from at this point - I am gathering information on OpenBSD as I want to build a box using that. But that's somewhere down the road. At present all I want to do is make sure I have a good backup system going before I spend a lot of time configuring/learning/using .....

So..... thanks again.

GMachine

---

