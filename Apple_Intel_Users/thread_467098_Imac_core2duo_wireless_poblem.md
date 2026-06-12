---
title: "Imac core2duo wireless poblem"
date: 2007-06-07
forum: Apple Intel Users
---

### Post by bimo on 2007-06-07
Hey,

I am a newbie in linux world and just installed an OS for the first time
which is ubuntu 7.04 on my mac
but i have a problem with the broadcom BCM4328 device.
I have searched on the net for 5 days and already tried many guide using ndiswrapper and bcmxx cutter and none of them works
Can anyone help me....

---

### Post by joselin on 2007-06-07
Follow [this howto]("http://forums.gentoo.org/viewtopic-t-558940.html?sid=cab6d6cae8b5cb40bc7abcbec1d22daf") i found, works like a charm.

---

### Post by bimo on 2007-06-07
thx...

---

### Post by bimo on 2007-06-07
Can you help me with this
so when i entered the command on the terminal 
it shows

bimo@bimo-desktop:/$ emerge ndiswrapper wpa_supplicant wireless-tools
bash: emerge: command not found
bimo@bimo-desktop:/$ cd /etc
bimo@bimo-desktop:/etc$ mkdir wireless
mkdir: cannot create directory `wireless': Permission denied
bimo@bimo-desktop:/etc$ cd wireless
bash: cd: wireless: No such file or directory
bimo@bimo-desktop:/etc$ wget [http://www.touslesdrivers.com/fichiers/broadcom/Broadcom_BCM43XX_4.100.15.5.zip](http://www.touslesdrivers.com/fichiers/broadcom/Broadcom_BCM43XX_4.100.15.5.zip)
--23:42:50--  [http://www.touslesdrivers.com/fichiers/broadcom/Broadcom_BCM43XX_4.100.15.5.zip](http://www.touslesdrivers.com/fichiers/broadcom/Broadcom_BCM43XX_4.100.15.5.zip)
           => `Broadcom_BCM43XX_4.100.15.5.zip'
Resolving [www.touslesdrivers.com](www.touslesdrivers.com)... 212.94.176.153
Connecting to www.touslesdrivers.com|212.94.176.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 42,172,583 (40M) [application/x-zip-compressed]
Broadcom_BCM43XX_4.100.15.5.zip: Permission denied

Cannot write to `Broadcom_BCM43XX_4.100.15.5.zip' (Permission denied).
bimo@bimo-desktop:/etc$ unzip Broadcom_BCM43XX_4.100.15.5.zip
unzip:  cannot find or open Broadcom_BCM43XX_4.100.15.5.zip, Broadcom_BCM43XX_4.100.15.5.zip.zip or Broadcom_BCM43XX_4.100.15.5.zip.ZIP.
bimo@bimo-desktop:/etc$ ndiswrapper -i bcmwl5.inf

---

### Post by joselin on 2007-06-07
Instead of this use the following:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 wpasupplicant
```and then:

Emerge is for gentoo like apt-get for ubuntu.

```

cd
mkdir wireless 
cd wireless 
wget http://www.touslesdrivers.com/fichiers/broadcom/Broadcom_BCM43XX_4.100.15.5.zip 
unzip Broadcom_BCM43XX_4.100.15.5.zip 
ndiswrapper -i bcmwl5.inf 

**[You should get no errors here] **

sudo modprobe ndiswrapper 
dmesg
```


At this point if you restart your network you must have wireless access.
```
sudo /etc/init.d/networking restart
```

---

### Post by ronocdh on 2007-06-07
I would just like to add that the permission error during **mkdir** was because the command wasn't preceded by **sudo**, which stands for "superuser do" and is basically the command that makes the system do what you want. ;)

[Funny cartoon]("http://meuk.infx.nl/sandwich.png"). :popcorn:

---

### Post by russo.mic on 2007-06-08
Ronocdh,

Great cartoon.

Russo

---

### Post by ronocdh on 2007-06-08
> **russo.mic said:**
> Ronocdh,

Great cartoon.

Russo
I'm glad you enjoyed it; I for one *really* like it. Sorry to thread hijack, but I poked around the parent directory and found [this one]("http://meuk.infx.nl/vgcats.jpg"), too. Hopefully you get a kick out of that one.

:popcorn:

---

