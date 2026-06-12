---
title: "Starting your own website."
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by drarncruz on 2008-02-05
Hello,
I'm new to ubuntu and love it.  I currently have the 7.10 desktop version, LAMP, and Webmin installed.  I would like to start working on php/mysql websites and hosting them from home.  My question is this:  I want to develop the websites on my desktop (Windows) with using dreamweaver then upload it to my OLD hp server that was handed down to me.  I don't know how to do this.  I have networked these two computers using a linksys router but I don't know how to transfer the files from my desktop to my server which runs ubuntu 7.10 desktop version.  Any help would be appreciated.  Thanks

---

### Post by luisromangz on 2008-02-05
You could do this in several ways: using an ftp server, using an svn repository (useful for web development), etc.

---

### Post by emarkd on 2008-02-05
If you just want to transfer a few files back and forth, try [Samba]("http://help.ubuntu.com/community/SettingUpSamba").  I've never used Dreamweaver, so I may not understand what you need.

---

### Post by Nythain on 2008-02-05
many many many ways...
FTP
Samba
WinSPC
SVN
im sure there's more... i have a windows xp machine, and a linux "server" set up on my home network... i use ssh and vnc for remote administration, and Samba or WinSPC for file transfers... works out pretty well in the end

---

### Post by drarncruz on 2008-02-05
I have filezilla on my desktop (windows) and I am trying to figure out how to transfer a simple website.  I have transefered files to hosting companies before using filezilla without problems.  I Don't know how to configure it so I can upload the file onto me server which is in the same network.  I tried to directly download the website in the the apache webserver var/www/ but it tells me that I don't have the permission to write these files into that folder.  

Is Samba like filezilla?
Thanks guys for the help.

---

### Post by %hMa@?b&lt;C on 2008-02-05
filezilla is FTP program. FTP is easy in Dreamweaver (my brother has to use dreamweaver for a college class :P) it should be easy, just install ftp server program on your server.
edit: you need to have root access or chown the /var/www folder 
hope i was helpful

---

