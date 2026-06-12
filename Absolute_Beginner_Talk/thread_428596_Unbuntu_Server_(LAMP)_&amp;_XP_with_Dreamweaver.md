---
title: "Unbuntu Server (LAMP) &amp; XP with Dreamweaver"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by bigfatdummy on 2007-04-30
I am just building up a new webserver at my office. I installed 7.04 server and selected the lamp option. I set the static ip and the install appears to be working great. (I can view the apache page from another computer by using the ip) The office is on a w 2003 domain and all but this new server are MS systems. The computer I develop on is xp pro and I use a mixture of macromedia and adobe products. (now all one company) Changing my system it linux is not an option at this time. I want to be able to develop on my xp system and put the files to the new server. I have used apache before with dreamweaver and I am struggling with the command line interface in 7.04. Some have suggested installing FTP on the server and uploading that way. Is that necessary for uploading to a server on the same network? Any help would be greatly appreciated

---

### Post by Bachstelze on 2007-04-30
If there is no file transfer protocol up and running, I wonder how you could transfer files...

---

### Post by bigfatdummy on 2007-04-30
um, share the folder and upload it via local network??

---

### Post by Bachstelze on 2007-04-30
What The-OS-That-Should-Not-Be-Named calls "folder sharing" is in fact Samba, which is a file transfer protocol among many others. You coul use it but I personnally find if awfully unreliable compared to FTP for example.

---

### Post by stump138 on 2007-04-30
I always use ftp to webservers, regardless of their location. I even do this on the network I run which includes Netware, LAMP, and Windows servers.  

Always using a FTP client always means I don;t have to worry about the constraints that can be placed on network shares.  Especially in mixed environments

---

### Post by walesmd on 2007-04-30
I'd go the FTP route as well - it will offer you the ability to chmod files without having to remote into the box.

Otherwise you will need to create a shared folder on the Ubuntu server (which will have to be FAT32, so your Windows machine can utilize it). Not sure how the permission would act in that respect...

---

### Post by bigfatdummy on 2007-04-30
Thanks everyone. 

Ok, will work on getting the FTP up and running

---

