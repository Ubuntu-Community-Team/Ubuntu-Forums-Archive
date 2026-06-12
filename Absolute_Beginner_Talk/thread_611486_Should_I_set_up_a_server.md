---
title: "Should I set up a server?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by BCRailrodder on 2007-11-13
Hi,

I am in the process of upgrading a couple of desktops to 7.10 and looking through the personel files that I have collected on both machines, I have noticed a lot of duplicates in pictures and music.

My question is "is it worth it to set up a Lamp server for just a file/database server?"  Down the road I do want to look at possibly setting up a mail server as well as being able to access my files from a remote location but for now, besides trying to get my media files under control, I would like to set up a central location for email (I know that firefox/thunderbird can be accessed from both a MS and a linux partition - I don't see why I wouldn't be able to do the same thing for 2 different linux machines over a network instead).  Having a centralized location for authencation of passwords would be nice but not immedialtely necessary.

While all my machines are dual boot (I still have 1 program that I need for work that requires windows), I am only concerned with the linux side of things so samba is not a concern so I was thinking of using nfs but I do want a central location for the 3 - 4 family members data files.  To that end, I could build a new machine as a server or just get a honking large drive (>300gigs) and tie that into one of the exisitng machines.

Currently, if I want to access the other machine, I just use SSH but that is limited as I am the only once in my family who knows how to do it.

In addition to the 2 desktops, I have a laptop that I am the only user on as well as a partially disassembled 300 mhz desktop that I was thinking about turning into a print server.

Any suggestions gratefully accepted <G>.

Kent

---

### Post by Skip Da Shu on 2007-11-13
First I'm a complete LInux noob so take this in that light...

My main WinXP desktop has a mirrored pair of 320GBs on it.  Another windows box has a 160GB IDE drive as an extra drive just for backups.  So I just used [THIS]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") to set up permanent shares to those from my freshly setup Xubuntu box.  Seems to work great except for one minor but... get to that in a sec... I've tested editing files from the WinXP box and from the Linux box. All seems good so far.  The other windows machine on my lan already access folders on that drive via normal windows folder sharing.  None of my machines  are dual boot.  So for what it's worth... If I could do it anybody can.  I just did a "sudo apt-get smbfs" which I don't think is really Samba.  You probably know.

Now for my glitch.  After rebooting the Xubuntu box the share isn't there until I do "sudo mount -a".  Since I made the changes at the end of fstab I thought that was all done at boot time.  Oh well, off to run that down or add "mount -a" someplace.

---

### Post by BCRailrodder on 2007-11-13
Not to worry Skip Da Shu, I am as much of a noob as anyone :)

If I understand the link that you provided, you did set up samba so you could tie into your windows machines.  Linux to linux doesn't require samba but nfs should suffice.

My concern is more along the lines of if it is worthwhile to set up a server now when I may not need it for quite some time (if ever).

Btw, "mount -a" means - Mount  all  filesystems  (of  the given types) mentioned in fstab. 

Kent

---

### Post by BCRailrodder on 2007-11-13
bump:popcorn:

---

### Post by WebSiteGuru on 2007-11-13
I am in the similar situation as you guys.

You can setup the server edition if you like. Or you can also get an external harddrive (if you wishes and if you dont mind spending some money) preferbly with the network capability and turned it into the Data Drive for all your data. That is what I am planing to do. This way you have it centralized on your network, and you dont have to worry about upgrading and loosing data on your server.

---

### Post by BCRailrodder on 2007-11-13
> **WebSiteGuru said:**
> I am in the similar situation as you guys.

You can setup the server edition if you like. Or you can also get an external harddrive (if you wishes and if you dont mind spending some money) preferbly with the network capability and turned it into the Data Drive for all your data. That is what I am planing to do. This way you have it centralized on your network, and you dont have to worry about upgrading and loosing data on your server.

That is along the lines of what I am thinking - I don't think that it would be too hard to move everything over later when I want to commit to a server.  It is also more in line with my experience (or lack thereof  :)  )

Kent

---

### Post by WebSiteGuru on 2007-11-13
> **BCRailrodder said:**
> That is along the lines of what I am thinking - I don't think that it would be too hard to move everything over later when I want to commit to a server.  It is also more in line with my experience (or lack thereof  :)  )

Kent

It is actually easy, not hard at all.

---

### Post by yotta on 2007-11-16
i would probaly set up a server yes, and get a FTP server set up on it to. This way you can easily use FTP to get yours files from one place to another without having to build some PHP Uploader or have to come up with some way of getting it to find someway of downloading

---

### Post by BCRailrodder on 2007-11-16
> **yotta said:**
> i would probaly set up a server yes, and get a FTP server set up on it to. This way you can easily use FTP to get yours files from one place to another without having to build some PHP Uploader or have to come up with some way of getting it to find someway of downloading

What about security issues on a ftp server? I am under the impression that FTP is one of the easier ways to enter a system.

Kent

---

### Post by jaybombalous on 2007-11-16
just don't allow anonymous login and don't let access to the internet on port 21, only map it to the internal network.


edit: I am assuming u have a router/gateway for all those desktops pc's u have.

---

### Post by yotta on 2007-11-16
yep just don't allow annoymous logins.

---

### Post by newlinux on 2007-11-16
I stick with sftp over ssh for Internet file transfers. Requires a user account and password but is pretty secure, with denyhosts running and running on a nonstandard port

Like many of you, I have decided to basically setup a central share composed of external hard drives on one of my ubuntu machines that is shared to all computers via SAMBA (I have a mixed Linux/Windows/Mac/Networked dvd player environment, so NFS was not an option). I mounted all these shares to the same location on all computers, so it works well for all users. 

This machine also serves as a web server, and hosts my NXserver from remote logins over the Internet, and is a mythbackend.

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

