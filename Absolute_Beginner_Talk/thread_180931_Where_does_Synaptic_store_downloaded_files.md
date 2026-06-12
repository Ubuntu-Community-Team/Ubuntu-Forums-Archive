---
title: "Where does Synaptic store downloaded files"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-23
Where does synaptic store the files that it downloads? The reasons I ask is, one for backing up these files, two being able to reinstall them in case of not being able to redownload them or to write them on disc and give to a friend without a Internet connection.

---

### Post by tkjacobsen on 2006-05-23
/var/cache/apt/archive

---

### Post by RudolfMDLT on 2006-05-23
Thank you! :)

---

### Post by Koech on 2006-05-23
Actually it's /var/cache/apt/archives. But you'll be ok I guess.

---

### Post by Daremo on 2006-05-23
[QUOTE=Koech]Actually it's /var/cache/apt/archives. But you'll be ok I guess.[/QUOTE]
Excellent question... I have another:
Is it safe to delete any or all of the cached files as this folder can get rather large over time?

---

### Post by aysiu on 2006-05-23
[QUOTE=Daremo]Excellent question... I have another:
Is it safe to delete any or all of the cached files as this folder can get rather large over time?[/QUOTE] Yes, it's perfectly safe.

---

### Post by Drakkor on 2006-06-22
I downloaded directvnc and now I can't find it ??

---

### Post by bruce89 on 2006-06-22
[QUOTE=Drakkor]I downloaded directvnc and now I can't find it ??[/QUOTE]
How did you download it?  Also there is already a VNC client at Applications>Internet>Terminal Server Client.
If you want to accept VNC connections go to System>Preferences>Remote Desktop.

---

### Post by Drakkor on 2006-06-22
Synaptic, though I found the file in /var/cache/apts/archives and installed it again, but it's not under the Internet apps.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Drakkor]Synaptic, though I found the file in /var/cache/apts/archives and installed it again, but it's not under the Internet apps.[/QUOTE]
You should just install it again from Synaptic then.

---

### Post by Drakkor on 2006-06-22
I did that the first time, but still can't find it !!

---

### Post by bruce89 on 2006-06-22
Are universe and multiverse enabled?  If not then go here to enable them - [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by Drakkor on 2006-06-22
Already done, I downloaded it and installed with Synaptic.

---

### Post by bruce89 on 2006-06-22
What's the output of ```
sudo apt-cache directvnc
```?

---

### Post by Drakkor on 2006-06-22
Here's what I have:

---

### Post by Drakkor on 2006-06-22
drakkor@drakkor:~$ sudo apt-cache directvnc
Password:
E: Invalid operation directvnc
drakkor@drakkor:~$

---

### Post by Brunellus on 2006-06-22
$sudo apt-cache search directvnc

---

### Post by Drakkor on 2006-06-22
drakkor@drakkor:~$ sudo apt-cache search directvnc
directvnc - VNC client using the framebuffer as display
drakkor@drakkor:~$

No big deal, I already have xvncviewer....just wanted to try a different client.

---

### Post by bruce89 on 2006-06-22
Sorry, this command will work```
sudo apt-cache policy directvnc
```
By the looks of things, you have it installed though.  Mabye it doesn't have a menu item, try pressing ALT+F2, then putting "directvnc" into the box.

---

### Post by Drakkor on 2006-06-22
drakkor@drakkor:~$ sudo apt-cache policy directvnc
Password:
directvnc:
  Installed: 0.7.5-7.1
  Candidate: 0.7.5-7.1
  Version table:
 *** 0.7.5-7.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
        100 /var/lib/dpkg/status
drakkor@drakkor:~$
Yeah, I tried Alt/F2 no dice,  I give up,lol   But Thanks for trying to help !
Cheers

---

