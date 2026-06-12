---
title: "[SOLVED] long list of problems installing webmin"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by thepiston on 2007-09-15
ok, total noob here, but I id manage to install 6.06 LTS LAMP with SSH.

I downloaded and tried to install webmin but i got the error that says i do not have some perls installed (libauthen and libmd5) so I tried to install them but got a 2nd error ("not available" or something), so I read the "How To" on the [webmin page]("http://www.webmin.com/deb.html") that says to alter the /etc/apt/sources.list file but even logged in as root I get "Permission Denied".  Now, this is my first night even using any form of Linux besides a LiveCD, so go easy on me...

---

### Post by bone2006 on 2007-09-17
setting up a server I'm not sure belongs in absolute beginner.  I would imagine the server section, you would get better help.  I'm running a server just recently, but I don't have webmin installed or I would attempt to give some advice, but I can only suggest posting in server section or maybe a mod will move this.

---

### Post by az on 2007-09-17
[https://help.ubuntu.com/community/WebminWithoutARootAccount](https://help.ubuntu.com/community/WebminWithoutARootAccount)

To install a deb, run

sudo dpkg -i package.deb

where "package.deb" is the name of the deb file you just downloaded.


However, webmin does not work properly anyway.  That's why it is not in the Ubuntu repos.  It used to be, but was removed.  If webmin actually started to do what it is supposed to do, it would then be put back into the repos for people to use.

---

### Post by rich.bradshaw on 2007-09-17
What's a good alternative?

---

### Post by kellemes on 2007-09-17
Howto..
[http://www.howtoforge.com/installing_webmin_ubuntu_feisty]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

I think Webmin is the best system-admin-package available for GNU/Linux. Looking for alternatives you won't find such a great collection of tools in one package.

---

### Post by rustybronco on 2007-09-17
I  re-installed centos5 on my server sunday and downloaded webmin-1.360. tar.gz, un-tar'd ??  it (in a terminal on my 7.04 desktop through PuTTY) and it worked perfect.

---

### Post by thepiston on 2007-09-17
i actually got webmin 1.360 to work just fine.  Thsi is what I had to do though:
[LIST]
[*]get the right folder to open sources.list
[*]open it and uncomment the addresses
[*]save the file
[*]install libauthen-pam-perl and libmd5-perl
[*]finally install webmin
[/LIST]

I logged into it perfectly after that.  Now I need to know how to add some sort of cPanel alternative to my server besides VHCS.

---

