---
title: "Another way to get files off of Windows"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by autocrosser on 2006-11-10
I just came across this website: [http://www.fs-driver.org/](http://www.fs-driver.org/)

He has a ext2/3 driver for Windows--this allows you to access your Linux drives in Windows--I would use this with caution, because it allows FULL read/write access without permissions--in other words--this could BORK your Ubuntu install very easily--

I have not installed this software (and most likely won't because I have no need for it;)), but I am posting this for people that want to get files from NTFS to EXT3 WHILE IN WINDOWS--this would be a easy way to resolve .deb file transfers when you have a non-working internet---

If it were me--I'd create a separate drive that is EXT3 formated to change data & not use it to work directly with your Linux partitions.....I DO NOT KNOW WHAT THIS COULD DO TO A LINUX INSTALL...your mileage may vary:rolleyes:

Edited for a clearer reason for posting---

---

### Post by aysiu on 2006-11-10
FS-Driver doesn't get files off NTFS from Ubuntu. It gets Ubuntu files off Ext3 from Windows.

---

### Post by bulldog on 2006-11-10
Thank you for your concern anyway :D 

I use it for several months now and Ubuntu is still up and running.

I have to say I don't use it often,because I use windows only in the weekends to play a game.

When I surf the net with Ubuntu it can happen I come across a handy app for windows,I download it and store it in my /home folder.

It's extremely handy when I boot into windows,I can copy that app out of the home folder to windows.

But you're right,you should use it with care,and only in your /home and not in the system folders.

---

### Post by autocrosser on 2006-11-10
I understand that aysiu--I'm just pointing out another way to transfer files without fuse--IF I were to use it, I'd be writing files from NTFS to EXT3 to use in my Ubuntu install (like music--etc). Just pointing out options for those that don't feel at home in Linux yet.......

Edit: from his FAQ sheet---
**What features are supported?**

 			[LIST]
[*]Complete *reading* and *writing* access to files and directories of volumes with the *Ext2* or *Ext3* file system.[/LIST]

---

### Post by aysiu on 2006-11-10
If you wanted to transfer files from NTFS to Ext3, you could do that in Ubuntu without any extra drivers.

---

### Post by autocrosser on 2006-11-10
Don't new people need every option they can use?

---

### Post by taurus on 2006-11-10
> **autocrosser said:**
> 
I have not installed this software (and most likely won't because I have no need for it;)), but I am posting this for people that are afraid of fuse & want to get files off of their NTFS partitions. 


I think the misunderstanding is this little paragraph here!!!  You can mount NTFS and have a read permission from it under Linux fine without installing anything extra...  That's what aysiu meant.

---

### Post by autocrosser on 2006-11-10
Thank you Taurus---

The reason I posted is when someone has a internet problem in Ubuntu & NEEDS to get .debs to work with the install-this looks to be a easy way to "make it happen"--I'll revise my first post to be clearer:(

---

### Post by taurus on 2006-11-10
Yes, you can use that program to access ext2/ext3 from Windows but you don't need anything extra to access NTFS from Ubuntu...  So, this matter is closed to me then.

---

### Post by aysiu on 2006-11-10
autocrosser, I just don't think you understand what's going on.

If you are in Ubuntu and want to get files off your NTFS partition, you just mount it correctly, and you can copy those files off of it:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

FS-Driver becomes necessary only if you're logged into Windows and need to get things off of Ubuntu's Ext3. Windows can't view Ext3 properly without the help of [http://www.fs-driver.org](http://www.fs-driver.org)

By the way, I've used FS-Driver before, and it works just fine.

---

### Post by autocrosser on 2006-11-10
I do understand--please read how I revised my post--I've talked to several people stuck in windows without operating internet in Ubuntu & i posted this as a simple way to transfer files while in windows....

---

### Post by fazillatheef on 2006-11-10
Hi i needed a little help in installing multimedia codecs and those  basic stuff in ubuntu. I dont have internet support in ubuntu due to modem problem.I am writting this message in a windows system.I have good internet connection at college but , we use windows. I checked many guides for installing multimedia codecs.But all of these use apt-get and i cant use it.Is there any alternative , by which i can download the files in windows. and install using dpkg in ubuntu 

Fazil

---

### Post by autocrosser on 2006-11-10
This is what I was talking about--There are several ways---

goto the repository & download the .deb files you need &
1. burn them to a disc
2. from Ubuntu, copy them & install via dpkg
3. from Windows, use this method to write them to your drive--then boot ubuntu & install via dpkg

you can get the addresses of the repository you are using by looking at /etc/apt/sources.list

This will give you the http location.

---

### Post by fazillatheef on 2006-11-10
how can i update the source list without connecting to the internet

---

### Post by aysiu on 2006-11-10
> **autocrosser said:**
> I do understand--please read how I revised my post--I've talked to several people stuck in windows without operating internet in Ubuntu & i posted this as a simple way to transfer files while in windows.... No, you're still not getting it.

If you have .deb files you downloaded in Windows, you can use FS-Driver to transfer them to Ubuntu while in Windows, but you'll still have to log into Ubuntu afterwards to actually install them.

This is the difference:

**Method A** (What you're proposing)
1. Download and install FS-Driver
2. Download all the .deb files you need in Windows.
3. Copy them over to Ubuntu.
4. Reboot into Ubuntu.
5. Install the .deb files

**Method B** (The normal way--without installing additional drivers)
1. Download all the .deb files you need in Windows.
2. Reboot into Ubuntu.
3. Make sure the Windows partition is mounted properly
4. Copy them over to Ubuntu
5. Install the .deb files

For that situation, there's very little advantage to installing FS-Driver. FS-Driver comes in handy when you have files that you will be modifying from both Windows *and* Ubuntu--not just files you want to copy over.

> **fazillatheef said:**
> Hi i needed a little help in installing multimedia codecs and those  basic stuff in ubuntu. I dont have internet support in ubuntu due to modem problem.I am writting this message in a windows system.I have good internet connection at college but , we use windows. I checked many guides for installing multimedia codecs.But all of these use apt-get and i cant use it.Is there any alternative , by which i can download the files in windows. and install using dpkg in ubuntu 

Fazil Your best bet is [Ubuntu Plus](https://ubuntuplus.bountysource.com/). Otherwise, you'll be stuck downloading individual .deb files and trying to track down all the necessary dependencies one by one.

---

### Post by fazillatheef on 2006-11-10
i understood the download install stuff.The problem i need to update the souce list file inorder to see the links of the codec and other nonfree codecs.because i belive they reside in other repos

---

### Post by taurus on 2006-11-10
If you don't have access to internet, you can't update!!!

---

### Post by aysiu on 2006-11-10
> **fazillatheef said:**
> i understood the download install stuff.The problem i need to update the souce list file inorder to see the links of the codec and other nonfree codecs.because i belive they reside in other repos
If you downloaded individual .deb files, you can just double-click them to install. It's too complicated to create a local repository and add that to the /etc/apt/sources.list--trust me.

---

