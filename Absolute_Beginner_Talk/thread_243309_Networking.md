---
title: "Networking"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Magnus150 on 2006-08-24
Hello, new Ubuntu user here (just finally got my wifi belkin card workin, yay!) and I have a bit of a conundrum on my hands. I currently live with my family and they use a windows network, mainly using my second harddrive. I have a large harddrive in my box and they use it as a depository for random stuff such as movies. We use the network to share out this drive and allow everyone to read and write to it. But since i've been using Ubuntu, they haven't been able to read or write to it as I am not a part of the windows network unless I am logged in (which is becoming less and less of the time). I was wondering if there was a way to share out this partition with the Windows network while being able to run Ubuntu. I have the partition mounted, as I read off of it, but they are unable to. Is there an application or a script to be able to share it out with my network that all run Windows? Thanks for the assistance!

P.S.
Anyone know a way to get my Radeon 9200 working? Right now I am running off of an IGP that came with my Dell Dimension 2350 (yes crap I know, but I have to live with it for another half a year). I had to turn off my Radeon to get Ubuntu to even boot up. I think it's because whenever I have the Radeon set, it still tries to load up my IGP. A blacklist perhaps?

Thanks!

---

### Post by eternalsword on 2006-08-24
Well, there's two things you can consider.  first is setting up a samba share, I was never able to get this to work.  the second is setting up an ftp server that gives access to that drive.  there should be some guides around these forums.

---

### Post by jimrz on 2006-08-24
1- for your network use Samba (available through Synaptic)...check the wiki and search these forums for help with getting it configured. There are lots of postings on this subject.

2- again search these forums for "9200". I'm sure there are others using that card and you can see what issues they have had and the results the got correcting them. I have an ATI 9600 mobile 128MB  in my laptop but cannot offer any advice since it has always worked "out of the box" in ubuntu, except for not getting hardware acceleration.

---

### Post by mssever on 2006-08-24
One you install the Samba server, configure it by editing /etc/samba/smb.conf.

You have to add a section for each share. For example, I have the following at the bottom of my smb.conf:
```
[DesktopHome]
path = /home/scott
available = yes
browseable = yes
public = no
writable = yes

[MP3]
path = /home/mp3
comment = MP3 Folder
available = yes
browseable = yes
public = yes
writable = yes

[ExternalHD]
path = /usbdrive
comment = External USB Hard Drive
available = yes
browseable = yes
public = no
writable = yes
```

Apply changes with ```
sudo /etc/init.d/samba restart
```

Setup passwords usig smbpasswd (type man smbpaswd for help).

---

