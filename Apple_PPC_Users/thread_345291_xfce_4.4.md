---
title: "xfce 4.4"
date: 2007-01-24
forum: Apple PPC Users
---

### Post by Sheltem on 2007-01-24
Hello!

I'm new to Xubuntu and I'm just trying to install the new xfce 4.4 without much success. I downloaded the graphical installation package and run the shell:

olive@olive:~$ cd Desktop/
olive@olive:~/Desktop$ ls
Thunar-0.8.0-installer.run         xfce4-4.4.0-installer.run
Thunar-Bundle-0.8.0-installer.run  xfce-goodies-4.4.0-installer.run
olive@olive:~/Desktop$ sudo ./xfce4-4.4.0-installer.run 
sudo: ./xfce4-4.4.0-installer.run: command not found

Any ideas?:confused:

---

### Post by szegey on 2007-01-24
Did yout try a 
```

chmod +x xfce4-4.4.0-installer.run

```

---

### Post by APU on 2007-01-24
Why use the installer from the XFce site which bypasses the Ubuntu package and software managemen system?

Just install the xfce4 package (sudo apt-get install xfce4) and the goodies package (xfce4-goodies) and have fun. The lastest Ubuntu release(s) already has the XFce 4.4 release candidates available and you can expect to get  the final release pretty soon if not already!

APU

---

### Post by Sheltem on 2007-01-25
Thanks guys! I tried the two ways:

APU: if I try your method I get xfce 4.3.9 installed from the ubuntu repository:) 

szegey: almost!!:
olive@olive:~/Desktop$ sudo ./xfce4-4.4.0-installer.run 
Verifying file integrity... OK.
Extracting the installer... OK.
Checking for usable C compiler... gcc
Checking for usable C++ compiler... g++
Checking for GNU make... make
Checking for package config tool... not found, see /home/olive/.xfce4.installer-log for details
Cleaning up... OK.
olive@olive:~/Desktop$ cd /home/olive/
olive@olive:~$ ls
Desktop  Examples
olive@olive:~$ 

I can't seem to find that log file though...:confused:

---

### Post by 3rdalbum on 2007-01-25
Type:

```
nano /home/olive/.xfce4.installer-log
```

---

### Post by dpny on 2007-01-25
> **APU said:**
> Why use the installer from the XFce site which bypasses the Ubuntu package and software managemen system?

Just install the xfce4 package (sudo apt-get install xfce4) and the goodies package (xfce4-goodies) and have fun. The lastest Ubuntu release(s) already has the XFce 4.4 release candidates available and you can expect to get  the final release pretty soon if not already!

APU

Because, if you're on Dapper, you don't get the latest version.

---

### Post by APU on 2007-01-25
XFce 4.3.9xxx is just one of the Release Candidates for XFce 4.4 - Since it is actually the same Version as 4.4 (with some minor Bugs i suppose) i would think that the final 4.4 will hit the Ubuntu Repositories quite soon (it's not an upgrade to a newer version!)

Maybe this was a bit unclear in my post above ;-)

---

### Post by -Phi- on 2007-01-26
**Sheltem**: You need the package pkg-config

- Phi

---

### Post by Moulton on 2007-01-29
When upgrading from XFCE4 4.3.99 to 4.4.0, I lost my desktop background.

I think this may be due to the way the XFCE4 Desktop Settings keeps track of your preferred desktop background.  Previously, when I set the desktop background, I was obliged to specify a pathname to a specific image file.  Now I see a pathname to a custom list of images.  But that feature seems to have broken things.  I manually typed in a pathname to a specific image (instead of a pathname to a custom list), and I got my desktop back.

---

### Post by karstux on 2007-03-20
Are there any downsides to using the 4.4 installer that is provided through xfce.org? 

I'd guess that using the installer bypasses the Synaptic package manager, so is there a danger of the system getting confused when an official update is being released on the (x)ubuntu repositories?

4.4 has a nice compositing engine that doesn't seem to be in the 4.3.99 build, enabling nice effects like true transparency and window shadows... i'd really like to update to it. On the other hand, if 4.4 is going to appear on the official repositories, I might as well wait a bit...

---

### Post by grazie on 2007-03-20
Both Dapper and Edgy Xubuntu support Xfce pseudo transparency - it's just not enabled by default. Here's [a guide]("http://www50.brinkster.com/craziegrazie/XubuntuTransparency.html") to setting it up if you want to give it a try. However, real transparency is in Xfce 4.4 which is in Feisty due for release next month. However, whether PPC will get a Feisty release then still remains to be seen.

---

