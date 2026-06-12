---
title: "back to basics LAMP install procedure for 7.04 desktop?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by boardtc on 2007-05-19
Having come from Mandrake 9.2 I have just installed 7.04 desktop and have installed all the updates through the upgrade manager . My goals are to use it as a lamp server in my house only for some php/mysql apps and as a samba server for backups. 

I did not install the server version as that's too hardcore Linux for me. I've assigned my own password to root and enabled root logins. I've looked at a number of posts about how to install lamp now (no python needed) but nothing that's concise and precise. I have apps and databases backed up from my Mandrake install and I would love to have my home server up and running without endless hours of fiddling. I would really appreciate it if someone could explain to me simply how to do a lamp install.

Thanks a lot,

Tom.

---

### Post by bobplano on 2007-05-19
look at this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by boardtc on 2007-05-19
After I looked at that page was when I posted the question and started this thread :(

That is far from basic for newbies. Does it really have to be that complicated? Why can't the server install package be made available to install on the desktop?

---

### Post by bobplano on 2007-05-19
the basic command it (just copy and paste)
```
sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

---

### Post by boardtc on 2007-05-19
thanks! I'll try that now. I can't find a way to get to a command line form the desktop. What's the easiest way?

---

### Post by bobplano on 2007-05-19
applications>accessories>terminal
[with pictures]("http://www.psychocats.net/ubuntu/terminal")

---

### Post by boardtc on 2007-05-19
cool, thanks for that. it finished with a postfix config info screen, i  presumed it was finished. going back to that link I tried :
mysql -u root
but it said mysql is currently not installed ?
So I went back and tried to reinstall and got the postfix message, realising it was a pre install message...after trying many key combinations I found alt+enter got me to the selection config screen - I tried no configuration as I have no idea what postfix and after 30 min of trying key combinations somehow got passed this screen.....

4 years after my first and previous linux install, I am disappointed to see Linux is still has hard to work with and tends to be still for the gurus :-(

next to install samba so can get files from my wndows machine....it installed ok...following
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)
In the browsing samba shares section it says "You may have to run "smbpasswd" for each user that needs to have access to his Ubuntu home directory from Microsoft Windows.". I tried to reset the password but it said it could not connect to machine 127.0.0.1: NT_status_login_failure...anyone know what's going on?

---

### Post by tim15856 on 2007-05-22
To get files from my Windows systems, I never had to install Samba. I'm not home, so I can't tell you exactly what I did, but I think I used "connect to server". I tried clicking through going into the MS workgroup etc, but I couldn't connect. I finally manually entered the computer name and share name and it connected. If you come back to this post and need more help, I'll see what I did when I get home.

---

### Post by boardtc on 2007-05-24
@tim15856 thanks for that. i wish these steps were options in the package install, so much for this being easy :-( I've spent many hours trying to figure it out already. Well under MSHome I now see my server (Samba, Ubuntu) clicking on it brings ups a login box but it won't take the same username and password that I log into the ubuntu  box with?

---

### Post by detheridge on 2007-05-24
It sounds to me like you need to run smbpasswd [username].
You will need to specify a username and password that matches that of your windows machine to make life easier for yourself.

Don't get disheartened samba is still one of the most awkward procedures in Linux. I tend to keep copies of good smb.conf files to use as a base as the GUI utilities for it still leave a lot to be desired. Other than that have fun with Ubuntu, it was the only distro where I have found myself up and running in under an hour on a Toshiba laptop without any messing about with config files. 

It even works on my Dell Poweredge with RAID after only an hours tinkering.

Dave

---

### Post by boardtc on 2007-05-26
Samba request moved to [http://ubuntuforums.org/showthread.php?p=2729105](http://ubuntuforums.org/showthread.php?p=2729105)

---

