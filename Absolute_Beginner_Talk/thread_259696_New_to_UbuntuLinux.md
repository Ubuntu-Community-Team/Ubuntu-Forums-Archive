---
title: "New to Ubuntu/Linux"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by MacPC on 2006-09-17
Hi,

I am a absolute newbie to Ubuntu/Linux. I am hoping someone here can elp me with these questions.

I have Ubuntu set up on one of my PCs and I am trying to do the followings

1.) I want to network it to my Windows PCs, so far I can download files from my Windows PCs, but I can't make it a server, my Windows PC sees it but when I try to open the Ubuntu PC from Windows, the Windows PC asks for username and password, I typed in the correct username and password and it keeps saying "Incorrect password or unknown username." What do I need to do fix this?

2.) I read it somewhere that I need to change a few things in the /etc/Samba/smb.config file, I did that but Ubuntu says it's a read only file and I can't save it. What do I need to do to make this file writable?

3.) Also what do I need to do to get Ubuntu to share files with my Mac OSX

I will really appreciate some helps, thanks in advance.

MacPC

---

### Post by xyz on 2006-09-17
You may find answers on the Mac forum:
[http://www.ubuntuforums.org/forumdisplay.php?f=133](http://www.ubuntuforums.org/forumdisplay.php?f=133)

---

### Post by jimrz on 2006-09-17
#2 you need to use sudo
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup
sudo gedit /etc/samba/smb.conf
```
the first copies your current smb.conf to a backup (ALWAYS a good idea) and the second will allow you to write your user name/pw info to the file and save it.

---

