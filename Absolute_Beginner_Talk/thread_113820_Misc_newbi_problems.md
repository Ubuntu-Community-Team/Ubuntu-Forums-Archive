---
title: "Misc newbi problems"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by virtadept on 2006-01-07
Hi!
I've been running Ubuntu for about a week now. I thought I remebered some of the stuff from my early childhood but most Unix commands seems to be gone. 

FIrst of all, when I read the manual on the install CD image I could not find anywhere that I would not be able to write to NTFS partitions. Also there was plenty information how to handle the drive I was going to install Ubuntu to, but no advice what to do with my other drives. Now I'm sitting with a 1.5 Gb linux swap partion and 30Gb ext3 linux OS drive. A 200GB NTFS drive mainly consisting of a 180Gb Truecrypt file which contains all my music and other stuff Iäve collected over the years. I also have a 200GB empty harddrive which I'm not sure how to partion and format, since I want to use TrueCrypt for it and I haven't been able to correctly install truecrypt on the Ubuntu system. I also have a spare 30Gb harddrive in my bookshelf containing the Windows XP installation previously used on this computer. But I'm going to try for at least a month to get things going before I give things up. 
I don't have any linux friends so this forum is probably my only chance for support. 
I have 3 computers in my private network. Two of them will be running legitimate versions of Windows XP sp2 and the LInux machine will act as a file-server for the home network. As a ftp server for transfering files between me and my friends. A www server where  I want a simple homepage. 
So far I have worked for about 2 days to get internet going on the Ubuntuy machine since the ADSL-router DLInk 504T is not compatible with Ubuntu and cannot be used for DHCP, Gateway and DNS locator. After manually entering gateway, DNS, and using static local IP most of the internet things works. It took another day to get DDCLIENT installed. I have a dyndns domain called virtadept.mine.nu which I've been using for the windows installation. When using "Add application" I did not find any program which could to the job. So I ended up in shell trying to follow instruction posted on various homepages copying files to different folders which were in different location compared with the instructions. Also the lack of a root account made it hard to modify the files after copying them. After reading more forums I used the "VI" shell editor together with the sudo command. I've spent hours looking for help on how to use the "VI" editor. How to save files and exit. The only thing I managed to do in "VI" was to halt the current process and start a new one. I think the problem was solved using the SYnaptic Package manager but there was no installation instructions included in that package so apart from writing my username and password for the DynDNS service I had no idea what to write. OK I think that perhaps by accident I'v got DYNDNS DDCLIENT to work. And also hopefully a TeamSpeak server. 
I've downloaded the PureFtp webadmin interface but for some reason the shell command I used to download the PureFTP server didn't quite work out. Later I also found the package for pure ftp and downloaded the common files and the main pure ftp file but the web-admin doesn't work any better because of it. I guess more installations and configurations have to be done before I can use the webadmin interface.
Also I've spent a couple of days trying to get the Creative Audigy SE audio card to work. I've been to the ALSA website using some shell commands to download the latest driver but even though the boot-up is configuring some ALSA card, it is not listed in the device manager and not selectable when choosing multimedia system. 

OK. That the basic story of my life. Now to some questions. Is there a GUI program I can use to check-verify my new 200GB hard-drive and to partion and format it? Should I use some special format to be able to share it with windows computers on the network?
Does anyone have installed TrueCrypt on Ubuntu and could give me some good pointers on how to install it?
I have basic understanding of the shell. Like copying files, making directories. Where can I find information on the basic keyboard shortcuts used in the "VI" editor and similair programs?
Do anyone know where I can find information on what to do after downloading the pureftp package in order to get the service to work(the first 10 hits when searching for pure ftp in ubuntu forum gave nothing)
Generaly I think the information gived by the OS after downloading packages is missing. There should always be a nice readme files shown when downloading a new package. 
And also. If anyone happens to sit on an Audigy SE card and manages to get it to work I'm dying of curiosity on what do to!!
OK. Special thanks to the ones who had the energy to read this entire post!
Extra Kind Regards
Virtadept

---

### Post by Thunk on 2006-01-07
Regarding the mutual drive - use Gparted to format whatever partition as FAT32. It is probably your safest bet for both Ubuntu and MS to read/write.

---

