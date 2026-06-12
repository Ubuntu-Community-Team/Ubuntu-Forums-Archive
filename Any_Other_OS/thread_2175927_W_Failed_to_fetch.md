---
title: "W: Failed to fetch"
date: 2013-09-21
forum: Any Other OS
---

### Post by Tony_Winston on 2013-09-21
I have been trying to followin instructions for install MSSQL for PHP5 on Debian Linux and I am running apt-get dist-upgrade and keep getting the following message:

W: Failed to fetch [http://mirrors.service.networklayer.com/debian-security/dists/squeeze/updates/Release](http://mirrors.service.networklayer.com/debian-security/dists/squeeze/updates/Release)  Unable to find expected entry  non-freeQ/source/Sources in Meta-index file (malformed Release file?)
E: Some index files failed to download, they have been ignored, or old ones used instead.

I am a newby to linux.  my sources.list file is below.  Can someone assist?  

thx! In advance.

- Newbie


deb [http://mirrors.service.networklayer.com/debian](http://mirrors.service.networklayer.com/debian) squeeze main contrib non-free
deb-src [http://mirrors.service.networklayer.com/debian](http://mirrors.service.networklayer.com/debian) squeeze main contrib non-free
deb [http://mirrors.service.networklayer.com/debian-security](http://mirrors.service.networklayer.com/debian-security) squeeze/updates main contrib non-free
deb-src [http://mirrors.service.networklayer.com/debian-security](http://mirrors.service.networklayer.com/debian-security) squeeze/updates main contrib non-freeQ
deb [http://apt.postgresql.org/pub/repos/apt/](http://apt.postgresql.org/pub/repos/apt/) squeeze-pgdg main
deb [http://debian.ludost.net/debian/](http://debian.ludost.net/debian/) testing main contrib non-free
deb-src [http://debian.ludost.net/debian/](http://debian.ludost.net/debian/) testing main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) testing/updates main contrib

---

### Post by QIII on 2013-09-21
*Moved to **Other OS/Distro Support***

---

### Post by sanderj on 2013-09-22
Did you try to open [http://mirrors.service.networklayer.com/debian-security/dists/squeeze/updates/Release](http://mirrors.service.networklayer.com/debian-security/dists/squeeze/updates/Release) with your webbrowser? If so, you'll notice you cannot reach that URL.

Further analysis:

sander@flappie:~$ host mirrors.service.networklayer.com
mirrors.service.networklayer.com has address 10.0.77.54
sander@flappie:~$

... it's pointing to a non-public IP address, so it's garbage.

So ... how did that repo get into your repo list?

FWIW: This is a Ubuntu forum, not Debian.

---

### Post by UltimateCat on 2013-09-26
When I was running Debian this is what my souces.list looked like--


> ## Debian Squeeze sources.list 
 
## Debian security updates: 
deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free 
deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free 
 
## Debian.org: 
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) squeeze main contrib non-free 
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) squeeze main contrib non-free 
 
## Debian Official Repository Mirror squeeze: 
deb [ftp://debian.oregonstate.edu/debian/](ftp://debian.oregonstate.edu/debian/) squeeze main contrib non-free 
deb-src [ftp://debian.oregonstate.edu/debian/](ftp://debian.oregonstate.edu/debian/) squeeze main contrib non-free 
deb [ftp://debian.oregonstate.edu/debian/](ftp://debian.oregonstate.edu/debian/) squeeze-proposed-updates main contrib non-free 
deb-src [ftp://debian.oregonstate.edu/debian/](ftp://debian.oregonstate.edu/debian/) squeeze-proposed-updates main contrib non-free 
 
## Debian US mirror: 
deb [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) squeeze main contrib non-free 
deb-src [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) squeeze main contrib non-free 
 
Remember - you can always find the original sources.list on your Debian install CD.       [h=3]Source:[/h]        [http://www.linuxquestions.org/questions/linux-newbie-8/debian-squeeze-repositories-709694/](http://www.linuxquestions.org/questions/linux-newbie-8/debian-squeeze-repositories-709694/)  
         



That should help--

---

