---
title: "How can I migrate to Wheezy?"
date: 2011-08-04
forum: Any Other OS
---

### Post by teh5abiking on 2011-08-04
Hi everyone, I just wanna know how I can upgrade to Wheezy. 

Squeeze is great and everything but I just hate the fact it uses outdated software. 

Here's the contents of my sources.list file: 

```
## Debian – Stable
deb http://ftp.us.debian.org/debian/ stable main contrib non-free
deb-src http://ftp.us.debian.org/debian/ stable main contrib non-free
## Security Updates
deb http://security.debian.org/ stable/updates main contrib non-free
deb-src http://security.debian.org/ stable/updates main contrib non-free
## Multimedia stable
deb http://www.debian-multimedia.org stable main non-free
# Backports repository
deb http://backports.debian.org/debian-backports squeeze-backports main
deb http://backports.debian.org/debian-backports squeeze-backports main contrib non-free
```

One of my friends once tried to upgrade to wheezy, but after running ```
apt-get dist-upgrade
```, he got a changelog or something and ended up being stuck or something.

Can anyone tell me how to upgrade to Wheezy painlessly? Or should I just stick with Squeeze until Wheezy goes stable.

---

### Post by XubuRoxMySox on 2011-08-04
Change the word "stable" in your sources list to "testing," then do the apt-get dist-upgrade thing.

Stable is Squeeze, Testing is "future "Wheezy," as I understand it.

---

### Post by krapp on 2011-08-04
[http://sites.google.com/site/mydebiansourceslist/](http://sites.google.com/site/mydebiansourceslist/)

Your /etc/apt/sources.list should like the one under "##Debian Testing##".

Then do

```

aptitude update
aptitude full-upgrade
```and wait.

As for to whether or not Testing is worth it, that's for you to decide if/when something breaks.

You're going to want to do

```
aptitude install apt-listbugs
```to warn you about problematic upgrades once you're Wheezy.

For me Stable + backports is enough at the moment it provides you with the latest Iceweasel and Icedove.

---

### Post by teh5abiking on 2011-08-04
this is what i get when I edited my /etc/apt/sources.list

```
root@debian:/home/shaun# aptitude update
                            
root@debian:/home/shaun# aptitude full-upgrade
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
root@debian:/home/shaun# 

```

---

### Post by krapp on 2011-08-04
Post your new sources.list.

---

### Post by teh5abiking on 2011-08-04
[SIZE=2][FONT=arial]# Testing 
#deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free
#deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main contrib non-free

# Testing Security[/FONT][/SIZE][SIZE=2][FONT=arial]
[/FONT][/SIZE][SIZE=2][FONT=arial]#deb [http://security.debian.org](http://security.debian.org) wheezy/updates main contrib non-free
#deb-src [http://security.debian.org](http://security.debian.org) wheezy/updates main contrib non-free

#Testing Proposed Updates
#deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing-proposed-updates main contrib non-free
#deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing-proposed-updates main contrib non-free[/FONT][/SIZE]

---

### Post by NightwishFan on 2011-08-05
Do not use proposed updates. They arent what you think and generally are undesireable.

Also for upgrading between Debian releases I would recommend you use apt-get and not aptitude. Though aptitude might work the Debian developers recommend using apt-get (for upgrades). It has not failed me through many dist-upgrades.

You basically only need:
```
deb http://ftp.us.debian.org/debian testing main contrib non-free
```

Then you should clear out cruft from your stable install. Uninstall any custom packages from 3rd party repositories. Just safer that way.

First run:
```
apt-get update
```

Then do this to simulate the upgrade:
```
apt-get -s dist-upgrade
```

Next download all the packages for the upgrade:
```
apt-get --download-only dist-upgrade
```

Finally you want to reboot into 'single user' or 'recovery mode'. This I find to be a safer environment for a full system upgrade. (This is why I had you download the packages ahead of time) Then run:
```
apt-get dist-upgrade
```

If you use ext4 the upgrade might take a while as ext4 has problems with certain sync and database workloads. I estimate around 30mins-1hr depending on your computer.

---

### Post by el_koraco on 2011-08-05
He doesn't have to reboot into single user mode. he can just go to tty and do a 

```
 #init 1
```

---

### Post by NightwishFan on 2011-08-05
Booting into recovery mode also avoids loading a lot of startup scripts and daemons which may or may not conflict with the upgrade.

---

### Post by el_koraco on 2011-08-05
Yeah, that's probably safer.

---

### Post by teh5abiking on 2011-08-05
Well I've successfully upgraded to Debian Wheezy, only one problem, 

My Linksys WUSB54GC v3 isn't working like it did on Squeeze. 

I'm running an older Sony VAIO laptop which doesn't come with WiFi. So I've been using a Linksys WUSB54GC v.3 for the last couple of years. I downloaded the firmware-ralink package from the Debian packages website and used dpkg to install it. I've loaded the rt2800 module but when I run ```
iwconfig
```, there's no wlan0, and when I run ```
ifconfig wlan0 up
``` It says that the interface doesn't exist. Any help here? 

I'm using my sister's netbook just to post this.

---

