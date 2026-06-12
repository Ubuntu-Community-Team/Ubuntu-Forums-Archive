---
title: "installing webmin  ??"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by jerryw617 on 2007-01-02
hi there  im trying too install webmin on a fresh install of ubuntu server .  webmin is on a dvd , i type  dpkg --install webmin_1.310_all.deb  and it says dpkg: need an action option  and gives a list of dpkg options ?     i just want the commands to install this ,  anyone ????

---

### Post by taurus on 2007-01-02
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install webmin
```

---

### Post by invalid on 2007-01-02
edit: see above

---

### Post by jerryw617 on 2007-01-04
no it didnt work 

reading package    done
building dependency tree
reading state information... done
initializing package states... done
building tag database... done
couldnt find any package whose name or description matched
webmin_1.130_all.deb
the following packages have been kept back :  w3m
0 packages upgraded, 0 newly installed, 0 to remove,and 1 not upgraded
need to get0b of archives, after unpacking 0b will be used

???????   im lost

---

### Post by taurus on 2007-01-04
Post your /etc/apt/sources.list here then?

```
cat /etc/apt/sources.list
```
Otherwise, download the latest version of webmin here...

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by chrismyers on 2007-10-13
[FONT=Arial]To install webmin on a non-gui machine:

First run:

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Then do a:

wget [http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.370_all.deb](http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.370_all.deb)

(the url was the latest version on 13th of Oct 2007)

Next do:

sudo dpkg -i webmin*

This will set up Webmin & now [FONT=monospace]y[/FONT]ou should now be able to login to Webmin at the URL [http://ipaddress:10000](http://ipaddress:10000)[/FONT]

---

