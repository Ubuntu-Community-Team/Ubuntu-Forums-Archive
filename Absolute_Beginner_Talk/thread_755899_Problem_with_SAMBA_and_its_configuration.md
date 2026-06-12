---
title: "Problem with SAMBA and its configuration"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rausuar on 2008-04-15
Hello all!

I would like some help configuring SAMBA and how to share files in an internal (home) network... I also would like to know how can I fix a problem I am having with a shared printer (connected to a PC with Windows Vista), because I can't see it in Ubuntu.  Also I want to know how can I configure correctly SAMBA or Ubuntu because in the network folder it shows me some shared computers that in the moment I check them, are not turned on...

I am using Ubuntu Hardy Beta, latest updates...

Thanks...

Att.. Raul

---

### Post by superprash2003 on 2008-04-15
i have heard about some problems regarding samba on hardy.. but you could try using the samba tutorial at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by AlanRogers on 2008-04-15
I found these by using [Google ]("http://www.google.co.uk")to search for [Ubuntu Samba HowTo]("http://www.google.co.uk/search?q=ubuntu+samba+howto").
 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
 
There are others but these two links at least eminate from here.
 
The biggest stumbling block for people new to Linux or Samba appears to be users. Samba users are not Linux users; you need to configure Samba with the valid users on your network before you will be able to connect to any Samba shares. You do not need to configure those users as users on the Linux box.
 
I've posted my /etc/samba/smb.conf file on here previously in answer to a very similar question. I'd recommend searching for it and you'll gain some insight into how it all works.

---

