---
title: "sudo dpkg-reconfigure xserver-xorg, intel is not on the list"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-07-19
I'm getting an error about the x server when I boot up ubuntu studio, so I typed

```
 sudo dpkg-reconfigure xserver-xorg 
```

to configure, but intel is not listed on the driver list, which one do I click?  (I think I have an Intel GMA 950)

---

### Post by Sandlst on 2007-07-19
Try using the i810 driver, it should work.  Is there a proprietary driver for intel?  I always thought their drivers were all freely available.

---

### Post by Krosis on 2007-07-19
You could install the Intel driver.

```

sudo apt-get install xserver-xorg-video-intel

```

---

### Post by Ludford on 2007-07-19
Does that require an internet connection

---

### Post by Krosis on 2007-07-19
> **Ludford said:**
> Does that require an internet connection

I don't believe so, as it does not seem to be getting anything from an outside source.

EDIT:  Then again, I may be wrong.  I'd say go with Rocket2DMn, s/he seems to know more about what's going on.

---

### Post by Rocket2DMn on 2007-07-19
> **Ludford said:**
> Does that require an internet connection

Yes, I think so, it would download from the repositories.

---

### Post by Ludford on 2007-07-19
I just tried it and it said it was unavailable, and I did plug my internet cable into it.

---

### Post by Krosis on 2007-07-19
> **Rocket2DMn said:**
> Yes, I think so, it would download from the repositories.

You are correct, you do need an Internet Connection.

Sorry for the false information.

---

### Post by Rocket2DMn on 2007-07-19
If that computer doesn't have internet, you could download the deb package and bring it to the computer on a flash drive.  You will need to change your /etc/X11/xorg.conf file after you install -
    Driver "i810" (or whatever else is here) needs to be
    Driver "intel"
you can first make a backup then edit by running 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```
If your xserver fails after you restart, you can restore your backup: 
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

EDIT: You may need to enable the restricted repositories to download it.  You can "uncomment" them in your sources.list file by removing the # in front of the 3 lines or so with "restricted" in them near the top:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Krosis on 2007-07-19
> **Ludford said:**
> I just tried it and it said it was unavailable, and I did plug my internet cable into it.

Just tried it.

```

tim@tim-laptop:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp5 fftw3 mysql-common libmysqlclient15off ruby1.8 ruby libtunepimp5
  libifp4 libpq5 libruby1.8 libofa0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-i810
The following NEW packages will be installed:
  xserver-xorg-video-intel
0 upgraded, 1 newly installed, 1 to remove and 5 not upgraded.
Need to get 188kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Just make sure you type everything correctly.

```

sudo apt-get install xserver-xorg-video-intel

```

---

### Post by Ludford on 2007-07-19
... this is getting very complex, I was hoping for a pain free install.

EDIT: also I still cannot get the install drivers command to work, I think it may be because I haven't told the computer how to get on the internet yet

---

