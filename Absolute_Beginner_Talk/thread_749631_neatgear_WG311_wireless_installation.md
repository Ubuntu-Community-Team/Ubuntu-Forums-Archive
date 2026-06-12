---
title: "neatgear WG311 wireless installation"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by tadcan on 2008-04-08
Sorry to start another wireless thread, but I need some one on one help.

I have a Netgear WG311v3 wireless adapter. 7.10 is installed, but I cant get online.

The network manager cant see my wireless device.

I have looked in the restricted driver and just see a driver for my graphics card.

I typed 

```
 iwconfi
```

and got the message 

lo          no wireless.... 

etho     no wirless.....

what should do next

---

### Post by yoma819 on 2008-04-08
go to the terminal and type
```

lspci

```
assuming it is a pci card
then post the output
if it is a usb dongle
type
```

lsusb

```

---

### Post by tadcan on 2008-04-08
```
tadcan@Quad:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) 
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) 
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) 
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02) 
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2) 
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) 
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
05:00.0 Multimedia audio controller: Creative Labs SB X-Fi 
05:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) 
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
tadcan@Quad:~$
```


I noticed these two, I presume they are relevant 

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 

05:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) 
```

---

### Post by yoma819 on 2008-04-09
right it is the wireless one we are interested in
dont ask me why but trust me and take out the wireless pci and put it in a different pci slot!
then follow this guide to the letter and it will work.
you will need internet access i.e. plug your lan in!
--Yoma
[https://help.ubuntu.com/community/WifiDocs/Device/%20TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28Wifi%20Docs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/%20TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28Wifi%20Docs%2FDevice%29)
:):)

---

### Post by tadcan on 2008-04-11
I am following the link above. 

I am at step 5. I have copied the ndswrapper to my home folder. The next step 

> Using tar extract the archived driver and change directories into the build area

I typed in the code listed below on that page changing the version number the one d/l. But I got this.

```
tadcan@Quad:~$ tar xvzf ndiswrapper-1.52.tar.gz  
tar: ndiswrapper-1.52.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

Dont know if its relevant, but at stage 3 I got this error for the build install

```
tadcan@Quad:~$ apt-get install build-essential 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
tadcan@Quad:~$ 
```

What am I doing wrong?

---

### Post by C!pheR on 2008-04-13
> 
Code:

tadcan@Quad:~$ apt-get install build-essential 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
tadcan@Quad:~$

What am I doing wrong?

The error message suggests that you don't have permission to open the file, I'd try using sudo:

```
sudo apt-get install build-essential
```

---

### Post by yoma819 on 2008-04-13
yes confirm that you need to prefix system commands in the terminal with sudo

---

### Post by C!pheR on 2008-04-14
I actually ended up doing this installation for my dad's computer last night. I used the link above. 

Your problem at stage 5 is that you haven't downloaded the wireless driver. You can get the Windows driver at [http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz]("http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz") (provided you're installing the WG311v3, different revisions may require different drivers). You will need to use the driver name (WG311v3.INF) instead of the one quoted in the link (Mrv8000c.INF) as you are installing a WG311 and not a TEW-421PC.

As it happens your problem at stage 3 is not relevant to your problem at stage 5 but it is worth doing, as posted above use "sudo apt-get install build-essential".

---

### Post by tadcan on 2008-04-14
So still at stage 5. Will have to read instruction slowly to figure out what to do. Learning the whole .tar extraction process.

---

### Post by FAJALOU on 2008-04-14
Hopefully you have this all working.  If you find that ndiswrapper isn't working, then you could also try wicd.  Im using WG311v3 with WICD and it's working better than ndiswrapper did.

---

### Post by tadcan on 2008-04-14
I have confirmed the install of ndiswrapper

Have d/l good_WG311v3-driver.tgz 

Its on the desktop and can move it to home folder. How do I create a new directory.

FAJALOU, I seem to be doing ok so far, just the newbie stuff is stopping me so far. What is WICD?

---

### Post by FAJALOU on 2008-04-14
WICD is basically like nidswrapper but is better configured etc.  Sometimes it works better than ndiswrapper, but i would advise that you should dl the packages for ndiswrapper to your computer before installing wicd just in case it doesn't work :tongue:  .   The site for it is:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Normally to create a new directory you can just make a new folder in the place that you want it.

---

### Post by tadcan on 2008-04-15
This probably going to be slow going. 

So I made a folder in home and called it good_WG311v3-driver

I then ran cabextract, unshield and unzip in the terminal. Unzip is installed.

Next it tells me to run ```
user@ubuntu:~/ndiswrapper-1.29$ cd ~
```

However ~$ could not be removed from the terminal so it became this

```
tadcan@Quad:~$ ~/ndiswrapper-1.52$ cd ~
```

The response was 

```
bash: /home/tadcan/ndiswrapper-1.52$: No such file or directory
```

I also tried 
```
tadcan@Quad:~$ cd good_WG311v3-driver
```

but got 

```
bash: cd: good_WG311v3-driver: No such file or directory
```

Since its a .tgz file will unzip work?

---

### Post by FAJALOU on 2008-04-15
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

Try that site, follow it to the tee and it should work perfectly.  Even if ndiswrapper doesn't work correctly, we can worry about that later, right now just follow that and it should work, did for me and we're running the same thing.  As always, report back.. Thanks.

---

### Post by tadcan on 2008-04-17
I followed the instructions on that page without a problem.

However I still cant get online with a lan connection. 

I went into network settings 

Under DNS servers is an I.P address for netgear 

Under search domains is the name of my broadband provider.

When I try to add the above two a line comes up asking me to 'Type Address' 

I have a WEP password enabled.

Almost there, whats next?

---

### Post by FAJALOU on 2008-04-17
You can't get online with a lan connection?  Aren't you trying for a wlan connection?

Any ways, what you want to do now is go to System>Administration>Network
Do you see a wireless connection that says not enabled?  If so click on it and fill out the correct information.  We're almost there, report back as always.

---

### Post by tadcan on 2008-04-17
Not sure of the differance between wlan and lan. I have a wlan link from my wireless modem to the wireless router. So I presumed the cable from the wireless router to my PC was lan. But hey could be wrong.

I have enable wireless in network connections. When I press on the two monitors I can choose wired connection or manual configuration. 

When I press on wired connection the two little monitors become moving a circle. But then I plug out the cable I loose the internet. 

In manual configuration I can put in info, just not sure what to enter. Like I said above under DNS it sees my provider and I get an IP address. When I click on add I am asked to type address. Don't know what to type in.

---

### Post by tek640 on 2008-05-19
I have the same errors when i try to install the same card.This guide works on ubuntu 8.04 x86 64 bit?

---

### Post by tadcan on 2008-06-08
I am having another go at fixing the wireless. I have turned off the password from the router. 7.10 is still not detecting the network. 

When I go into Network settings- DNS. I can see (DNS servers) 192.168.1.1 which is the I.P version of calling home? Search Domains I see my Broadband provider. 

So why is it seeing my provider but not the network.

---

### Post by FAJALOU on 2008-06-08
I had this problem too, even in 8.04, what I did is I figured out what the downstairs ip address was and then plugged that in (ie smb://192.168.1.101/users), and I could see the downstairs computer.  If you know that you are looking for, lets say your personal file, then it would prolly be in something like smb://192.168.1.101/users/<other computer login>/     Hope this helps.  Keep us informed.

---

### Post by tadcan on 2008-06-09
I am clueless when it comes to this end of computers. I Normally annoy my friends who work in tech support!

What is smb?

---

### Post by FAJALOU on 2008-06-09
smb is samba, which is what you use for windows sharing. especially on a network.  to install it, go into terminal and type:  sudo apt-get install samba

that should install it.

---

### Post by tadcan on 2008-06-12
I have installed samba. Had a look at the website. I tried this. You'll have to give me the dummies guide, cos I have no clue.

```
tadcan@Quad:~$ smb://192.168.1.101/users/<tadcan>/
bash: tadcan: No such file or directory
```

---

### Post by FAJALOU on 2008-06-12
no worries tadcan you're doing great. try this:

smb://192.168.1.101/users/tadcan/

I think that that will work, and as always report back with results.

---

### Post by tadcan on 2008-06-13
Got this

```
tadcan@Quad:~$ smb://192.168.1.101/users/tadcan/
bash: smb://192.168.1.101/users/tadcan/: No such file or directory
```

So where is samba installed, I expected to see it in Applications - internet. Is samba a program you launch or runs in the background.

---

### Post by FAJALOU on 2008-06-13
[http://ubuntuforums.org/showthread.php?p=5176342#post5176342](http://ubuntuforums.org/showthread.php?p=5176342#post5176342)

See this, may help.  Read through especially the last page, it's helpful

---

