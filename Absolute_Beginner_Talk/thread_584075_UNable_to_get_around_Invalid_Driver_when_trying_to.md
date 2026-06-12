---
title: "UNable to get around Invalid Driver when trying to set up network adapter."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Smaress on 2007-10-20
Hi...I am definitely a newbie with Linux, but have found the initial load of Xubuntu (Feisty Fawn) to my old IBM Aptiva to be a positive experience. The one area where I am having difficulty is using ndiswrapper (1.38) to install the correct driver for my Linksys WUSB11b wireless network adapter. I have read may notes through many forums, and the instrucitons I have read appear to be consistent, but when I attempt to install the driver(s) which came with the Linksys installation CD (NETUSB.INF or WUSB11v4.INF), they appear to be invalid. When I enter ndiswrapper -i NETUSB.INF I receive a response stating the driver is already installed, but when I do a ndiswrapper -l to list the installed driver, I receive a message "invalid driver!" from ndiswrapper. I have gone to the Linksys site to download the current driver and attempted to reinstall thinking the drvier from the CD isn't the latest, but I always receive the same INVALID DRIVER message. I'm really not sure what my next step should be and I would appreciate any assistance or direction to help get me past this problem. Thanks.

---

### Post by avox on 2007-10-21
This guide may help you out:  [http://ubuntuforums.org/showpost.php?p=3523552&postcount=2](http://ubuntuforums.org/showpost.php?p=3523552&postcount=2)

To get to the quick of it:

> This error usually means that there are duplicate or more than one driver installed with ndiswrapper. The easiest way to resolve this message is to do the following:

```
sudo rm -R /etc/ndiswrapper *
```

You will then have to reinstall your windows driver via.

```
sudo ndiswrapper **********.inf  <-----Substitue the appropriate name of your inf file here.
```



Hope that helps.  I know it's tough sludging through the myriad of posts here, but never give up.  Course, I can say that cause I got lucky on the first search result I clicked...   :biggrin:

---

### Post by hmlessalky on 2007-10-21
Same problem here. Using a Trendnet card. I have read every guide I could find and I keep coming up the same. Updated ndis to the latest stable release, downloaded the most current drivers, etc. It seems that maybe ndis is not copying the files to the /etc/ndiswrapper/(drivername) folder; at least there is nothing there when I look. I always get the 'couldn't open  ~drivers/(drivername): No such file or directory at /usr/sbin/ndiswrapper line 217'. But if I try to install it again, it says it is already installed. 

Help would rock, I am trying to get one step closer to giving up Win-o's after many a year.

Fingers

---

### Post by hmlessalky on 2007-10-21
Actually, I just used the above trick after a restart, and it seems to have worked. It didn't the last thousand times, but being an old win guy, I figured a restart couldn't hurt. Now to see if it actually works. Man, now I have to go back and find one of those guides!

---

