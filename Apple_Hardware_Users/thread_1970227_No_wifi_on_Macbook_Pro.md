---
title: "No wifi on Macbook Pro?"
date: 2012-04-30
forum: Apple Hardware Users
---

### Post by Zukaro on 2012-04-30
I've just installed Ubuntu 12.04 on my Macbook Pro 13-inch (late 2011).  How do I get the wireless working?  It says "Missing firmware" under what I'd normally click to use the wifi.  Also, are there any other drivers I'll need to download?  So far it looks as if everything is working fine (other than my wifi).

---

### Post by Zukaro on 2012-05-01
I'm not sure which drivers to download or where to download them from; could someone help?  I've looked around on Google for awhile and haven't found anything.

---

### Post by TBABill on 2012-05-01
Can you open a terminal and type in ```
lspci | Network
``` and paste the output back here? Probably Broadcom, but not sure which.

---

### Post by subehsharma on 2012-05-01
I used the following steps to get it working on my MBP:

There is no official support yet in Ubuntu 11.10, but you can get it working with the following repository:


sudo add-apt-repository ppa:mpodroid/mactel
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
Then install the linux-backports-modules-cw-3.2-oneiric-generic or, if you have the pae kernel installed, the linux-backports-modules-cw-3.2-oneiric-generic-pae package.

Edit the /etc/modprobe.d/blacklist.conf and add the line:


blacklist ndiswrapper
Create or edit the file /etc/pm/config.d/modules and make sure the wireless modules (b43 and bcma) are blacklisted:


SUSPEND_MODULES="b43 bcma"
Reboot and the wireless should work.

[https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless)

---

### Post by Zukaro on 2012-05-06
> **TBABill said:**
> Can you open a terminal and type in ```
lspci | Network
``` and paste the output back here? Probably Broadcom, but not sure which.

This is what comes up under network after doing the lspci command.
```

03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
```

---

### Post by Zukaro on 2012-05-07
Does anyone know where I could get the drivers for this?

---

### Post by Hatsune Miku on 2012-05-07
> **Zukaro said:**
> Does anyone know where I could get the drivers for this?

Plug your computer into your router with ethernet
Go into the Ubuntu dash and look up Drivers
click on "Additional drivers" let it load
Select the one that says broadcom and on it and install
reboot and u have wifi

---

### Post by Zukaro on 2012-05-08
> **Hatsune Miku said:**
> Plug your computer into your router with ethernet
Go into the Ubuntu dash and look up Drivers
click on "Additional drivers" let it load
Select the one that says broadcom and on it and install
reboot and u have wifi

When I go to additional drivers after it loads it says "No proprietary drivers are in use on this system." (and I am connected to the Internet through Ethernet).

---

### Post by rgogunskiy on 2012-05-08
Have you tried:

```
sudo add-apt-repository ppa:mpodroid/mactel
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer

and after that reboot your MacBook Pro.
```
?

I have 13-inch 8.1 MacBook Pro with the same WiFi card as yours and this steps helped.

---

### Post by Zukaro on 2012-05-08
I just found this guide and followed it.  Everything is working fine now.


guide:
[https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric)

---

### Post by hectordelaf on 2012-05-14
> **Zukaro said:**
> I just found this guide and followed it.  Everything is working fine now.


guide:
[https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric)


i feel really stupid but i don't get the guide :S the part of the wireless connection, i am new in this and i have a macbook pro with ubuntu 12.04 i think its the same problem that yours hope u can help me a little.

thanks

---

### Post by hectordelaf on 2012-05-14
hector@hector-MacBookPro:~$ sudo add-apt-repository ppa:mpodroid/mactel
You are about to add the following PPA to your system:
 Packages to run Ubuntu on mactel
 More info: [https://launchpad.net/~mpodroid/+archive/mactel](https://launchpad.net/~mpodroid/+archive/mactel)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.pNfjNsVAks --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A8AC8A37E3F3F2692C3F97796900DEBE3AAA6035
gpg: requesting key 3AAA6035 from hkp server keyserver.ubuntu.com
gpg: key 3AAA6035: "Launchpad PPA for Marco Pozzato" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


but then i dont know how to do this things: (PLEASE TELL ME HOW)

Then install the  linux-backports-modules-cw-3.2-oneiric-generic or, if you have the pae  kernel installed, the linux-backports-modules-cw-3.2-oneiric-generic-pae  package. 
Edit the /etc/modprobe.d/blacklist.conf and add the line: 

blacklist ndiswrapperCreate or edit the file /etc/pm/config.d/modules and make sure the wireless modules (b43 and bcma) are blacklisted: 

SUSPEND_MODULES="b43 bcma"Reboot and the wireless should work.

---

### Post by yibbidy on 2012-05-15
Hi Hector,

You shouldn't have to do those things with the latest kernel as far as I know.  I just upgraded my MacbookPro8.1 from 11.04 to 11.10 to 12.04.  I did not have wireless setup in those earlier versions so this should be valid.  All you should have to do is type:

> sudo add-apt-repository ppa:mpodroid/mactel
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer

I did not even have to reboot, it all started working.

Before you do this perhaps you should make sure that you have the latest updates through a wired ethernet connection first.

Shaun

---

### Post by sgnemo on 2012-08-01
Hi
I just downloaded the new Ubuntu 12.x and did an online (wired) install on my 2009 Macbook Pro Unibody. The wireless is working fine

thanks

---

