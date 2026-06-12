---
title: "Airport Wireless not detecting network in Linux????"
date: 2008-01-19
forum: Apple PPC Users
---

### Post by Mr. Shhh on 2008-01-19
A great hello to all and a problem I have!
I have an iBook G4 and my Airport Extreme wireless card is not detecting ANY wireless networks even though I am sitting only 8 feet away from the router.  The operating system is a fresh install of kubuntu 7.04.
To answer any future questions: yes, I am 100% sure the wireless works fine since I am also sending this from a wireless PC.  Also, I have set up Ubuntu & Kubuntu on my PC's simply by adding in the WEP key and setting it to hexadecimal.  However, this is obviously my first time setting up wireless linux on a mac ;)  Please let me know what I am doing wrong or not doing.  I really appreciate it!

---

### Post by stmiller on 2008-01-19
For that broadcom wireless card, you'll have to issue a command to fetch the firmware. The firmware is not open source so it cannot be included by default. Just do this:
```

sudo apt-get install bcm43xx-fwcutter

```

Reboot and should work fine.

---

### Post by tedir on 2008-01-19
Try using WICD instead of the usual NetworkManager..

you should also upgrade it to 1.4**

---

### Post by Mr. Shhh on 2008-01-19
I ran the sudo command that you gave me, but it said couldn't find package bcm43xx-fwcutter

---

### Post by stmiller on 2008-01-19
Go to Add/Remove Applications>Preferences and check the first four boxes to enable all software sources that you need. Then hit close and it should reload the available packages.

[[img]http://xs223.xs.to/xs223/08036/add_remove359.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs223&d=08036&f=add_remove359.png)

---

### Post by Mr. Shhh on 2008-01-19
I'm not sure how you found that box (software sources), but I'm using Kubuntu 7.04 and when I go to add/removes programs then put in my password, it doesn't take me there, it takes me to the Adept Installer which is not the same place where you were.  Please let me know how you navigated to software sources, unless you're using ubuntu or a different version of Kubuntu.

---

### Post by Mr. Shhh on 2008-01-19
Can anyone help!?

---

### Post by stmiller on 2008-01-20
Ah! Okay in Kubuntu, click the K menu, then Add/Remove Programs> then click the 'Edit Software Sources' button on the bottom left. There you can enable the top four boxes under 'Kubuntu Software' for sources.

Now you have access to lots of more software. Also check out [medibuntu,]("http://medibuntu.org/") for more software.

---

### Post by Mr. Shhh on 2008-01-20
Stmiller,
Is this the DVD edition that you're using???  Because 'Edit Software Sources'  isn't on mine.  When I click on the Kmenu > Add/Remove Programs, I have to put in my password for it to take me to the Adept Installer.  Once I'm in the Adept Installer, my only options on the left side are:
Accessibility
Development
Edutainment
Games
Graphics
Internet
Multimedia
Office
Others
Science
Settings
System
Utilities

I searched all over and didn't see anything else about editing the software sources.  It could be that theres just some miscommunication on my end.  I'm using the desktop cd version of Kubuntu 7.04 Feisty Fawn.  I hope this info helps, please let me know exactly how you found the software sources area. Thanks!

---

### Post by easychord on 2008-01-21
Hey All having the same problems as this user, try to install bcm43xx-fwcutter and get the following error message in terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be installed:

  bcm43xx-fwcutter 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.5kB of archives. After unpacking 123kB will be used.
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe bcm43xx-fwcutter 1:006-1 [27.5kB]
Fetched 27.5kB in 5s (5113B/s)          
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 110787 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_powerpc.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--12:41:47--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:41:48 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcm43xx-fwcutter (006-1) ...
--12:41:49--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:41:49 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

Any thoughts?

---

### Post by Mr. Shhh on 2008-01-22
As an update for Stmiller,
I did find that software sources area.  It isn't in the Adept installer, it's in the Adept manager.  The first four boxes are checked and accounted for.  However, my internet is still giving me problems.  Even after I downloaded and extracted the repositories that I needed.  Both wired and wireless internet is not working with my mac for Kubuntu.  I'm almost at the point of giving up.  What about that WICD??  How does that work??  Any other ideas would be great!  EVEN SUGGESTIONS FOR A DIFFERENT LINUX DISTRO ARE MOST CERTAINLY WELCOME!!!!  All I want is linux on my ppc mac and to have the wireless working!

---

### Post by stmiller on 2008-01-22
Ah, I see. The googlepages link where the broadcom firmware is down. Try searching around this forum to see if there is a workaround. This broadcom firmware applies to all broadcom based cards, so this is not PowerPC specific. There might be some other posts on this.

EDIT: It is also possible to extract the firmware from the apple driver. There is a thread on the gentoo ppc forum for how to do this.

---

### Post by Typhoon on 2008-01-23
See this page to get the firmware:

[http://www.debiantutorials.org/content/view/153/213/](http://www.debiantutorials.org/content/view/153/213/)

Cheers,
Typhoon

---

### Post by guidop on 2008-01-23
Try downloading the pre-built .deb file with firmware included from:

[http://www.speedyshare.com/214793933.html](http://www.speedyshare.com/214793933.html)

It's mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=526901](http://ubuntuforums.org/showthread.php?t=526901)

(There may also be instructions somewhere on this forum on how to copy and install the firmware from an OS X installation.)

You can run this command to see what kind of Broadcom chip you have:
```

$ lspci | grep Broadcom

```
If you install the firmware, and it works, running this command should show the available wireless networks:
```

$ sudo iwlist eth1 scanning

```
If you have an iBook with the older BCM4306 chip, you should be able to at least connect with unencrypted wireless network at this point.  For WPA, however, you may additionally have to uninstall knetworkmanager due to an endian issue on 7.04 ppc builds, and either configure WPAmanually, or try installing and using WICD:

[https://sourceforge.net/projects/wicd/](https://sourceforge.net/projects/wicd/)


If you have a later model iBook with the BCM4318 chip, you may still have problems, though it looks like things may (?) work on that model with a clean install of Gutsy, or maybe with a patched kernel:

[http://ubuntuforums.org/showthread.php?t=624389](http://ubuntuforums.org/showthread.php?t=624389)

Hope this gets you up and running.

---

### Post by stream303 on 2008-01-23
> **easychord said:**
> Hey All having the same problems as this user, try to install bcm43xx-fwcutter and get the following error message in terminal


I think you have to use synaptic or some other graphical installer.  When I tried to install it via synaptic, it immediately brought up a configuration window immediately after install.

I could be wrong, maybe the fw-cutter window prompt is hiding somewhere on your system...

---

