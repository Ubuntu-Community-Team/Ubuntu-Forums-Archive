---
title: "Linksys WUSB11 Ver. 2.5 Driver Install"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by jdeluca on 2007-05-01
This is where I am stuck.

jdeluca@UbuntuOS:~$ **[COLOR="Red"]sudo apt-get install linux-wlan-ng[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  linux-wlan-ng-doc
The following NEW packages will be installed:
  linux-wlan-ng
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/122kB of archives.
After unpacking 569kB of additional disk space will be used.
Selecting previously deselected package linux-wlan-ng.
(Reading database ... 93322 files and directories currently installed.)
Unpacking linux-wlan-ng (from .../linux-wlan-ng_0.2.6+svn20061108-2ubuntu1_i386.deb) ...
Setting up linux-wlan-ng (0.2.6+svn20061108-2ubuntu1) ...

jdeluca@UbuntuOS:~$ **[COLOR="Red"]modprobe prism2_usb prism2_doreset=1[/COLOR]**
jdeluca@UbuntuOS:~$**[COLOR="Red"] wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable[/COLOR]**
wlanctl-ng: **Operation not permitted**
jdeluca@UbuntuOS:~$**[COLOR="Red"] sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable[/COLOR]**
message=lnxreq_ifstate
  ifstate=enable
  **resultcode=implementation_failure**


What do I do next?  It looks like I'm doing something wrong after the modprobe line.  Thanks for the help!

---

### Post by jdeluca on 2007-05-02
Can someone please help me out with this?  I'd like to get my desktop PC out of my living room and solving this wireless issue will obviously go a long way in making that a reality.  I'm starting to stress out the Misses.  Thanks!

---

### Post by stooker on 2007-05-06
I think I've got exactly the same problem, I'm online through a wire connection, but I like to get connected throught my Linksys Wireless-B USB Networking Adapter. Model no. WUSB11.

Ofcourse I got the windows drivers for this but I need it to work under Kubuntu 6.06. I got the feeling that Kubuntu doesn't even 'feel' that I connected it already.

Anybody help us out plz..

---

### Post by chriscross93 on 2008-01-06
I ma in the same boat.  Would love to get away from winxp, but until my wifi adapter works I can't.  I have a linksys WUSB11 network adapter.  Any help is greatly appreciated

---

