---
title: "[SOLVED] Help setting up wireless router connection"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by xprefugee on 2008-01-18
I just set up ubuntu on another hard drive.  Totally new to ubuntu.  When I put my lLnksys cd in it does not load.  The setup wizard appears but all it shows are the contents of the disk and no interface.  I poked at a few of the files that might run something and they won't open.

How do I get the cd open in a usable fashion?  Or, is there another way to connect to my router?
It is a Linksys wireless G Broadband model WRT54G.

The wireless connection is operational with  my xp drive.


Thanks!

---

### Post by smurphy_it on 2008-01-18
You shouldn't need the CD.  Not much on those CDs other than manuals and the like.  It is also most likely a windows based CD, so any executables won't run anyways, as linux is quite different.

You should be able to connect to your router via it's IP address.  Connect a wired cat5 network cable from your laptop to your router, and try connecting to the default IP address.  Probably 192.168.1.1 unless you changed it to something else.

Then just put in your username and password to connect to the router.   Probably administrator for the username and password is usually something easy like password or admin or left blank.

If you have a linksys router using a linux based firmware like openwrt or dd-wrt, then the username and password will be different.

---

### Post by mkwerner on 2008-01-18
Hi,
Your linksys cd is useless in Ubuntu - the setup wizard is made for Windows.  

Have you previously setup your router?  If so, do you recall your wireless settings, such as SSID and WEP/WPA (if you have that setup)?  

Access to wireless networks is usually handled through Networkmanager, which is at the bottom right of your screen - think taskbar for windows - just right-click on it and setup your wireless parameters.

HTH,
M.

---

### Post by xprefugee on 2008-01-18
Thanks for your help folks, I'll start working on it.

---

