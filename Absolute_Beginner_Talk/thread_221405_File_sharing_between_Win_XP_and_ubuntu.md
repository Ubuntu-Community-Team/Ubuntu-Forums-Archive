---
title: "File sharing between Win XP and ubuntu"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Micik on 2006-07-23
Hi,
I recently installed ubuntu 6.06 LTS and I want to enable file sharing between Windows XP amchine and ubuntu machine.
First I was suprised that samba was not installed by default and that I coudn't install it from installation CD (only smbclient). However I have ubuntu 5.04 CD which seems to have larger package base available so I manage to install samba. I went to Administration -> Shared Folders and defined which folders I want to share. I set up static IP addresses and computers can ping each other.. Now in windows in Network Neighbourhood I see linux computer named asim-desktop server (samba, ubuntu)(Asim-desktop) since my ubuntu machine is named Asim-desktop.
Now when I try to open it and double click I get windows password dialog box named "connecting to local host". It asks me for username and password. I tried to enter "Asim-desktop" and user's password on ubuntu machine I use to log on ubuntu, I also tried root password bu no success. Please can anyone help me?
Wht password I need to enter and if there is chance to disable this password thing somwhere on ubuntu machine I guess.
Thanks

---

### Post by gerbman on 2006-07-23
Try doing [this]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2").

---

### Post by whitecrow on 2006-07-24
I have experienced at least part of what you mentioned in your post.  When I did a clean install of Dapper, I was set to configure Samba like I did in Breezy but no Samba had been installed.  I tried to install it from disk but the OS kept attempting to download it from the internet.  Because I live in the country, I have only a dialup connection and that has been fritzy lately.  I couldn't imagine that Samba wasn't on the Dapper installation disk so I was thinking I needed to reconfigure how the system was looking for software.  But if I hear you right, Samba is not on the Dapper disk.  Are you saying that I should install it from the Breezy disk?  There appears to be a bug in the Samba on my Breezy disk but I guess I could work through that again.  Did it work okay for you in the end?

Whitecrow

---

