---
title: "Broadcom"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by LouisChappell on 2008-01-21
Hi, I've tried every single method to successfully install my broadcom 43xx wireless card. it's a  Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03).
i just don't seem to be able to get it working. must be missing something, it's a very fresh install. any ideas?

---

### Post by fatality_uk on 2008-01-21
Any chance you can tell us what you have tried? nDiswrapper for instance etc? Give us a few more details and im sure help will come.

Cheers

---

### Post by CJ56 on 2008-01-21
I got a similar Broadcom card working on an elderly Dell laptop by 

- Letting the restricted drivers manager install a bit of software first
- Getting Wi-fi Radar (I know it's not the latest thing, but it worked) off the Synaptic package manager
- Opening up Wi-fi Radar under Internet in the Applications menu
- Choosing Auto whenever I could in the drop-down menus
- Giving it a moment to connect...

Have you had no luck with this routine...?

---

### Post by LouisChappell on 2008-01-21
@CJ56, i have tried with no luck but thanks for your offering.
@fatality_uk i have tried the following;
> [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28WifiDocs%2FDriver%29)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28WifiDocs%2FDriver%29)
and a good few others which i can't remember

on the feisty one i got to the stage where the wireless light was on and it could see the networks but souldn't connnect to my linksys router, with the WEP, not tried turning the WEP off though.

on the last one i listed it said 6) If the Status has changed to In use, then you are successful.
i did get this message but it wouldn't connect, does that mean it's my router?

thanks very much for the quick replies,

---

### Post by LouisChappell on 2008-01-22
do i need to edit anything in the routers settings?

---

### Post by LouisChappell on 2008-01-25
bump

---

### Post by LouisChappell on 2008-01-30
sorry to bring this up again, does anyone have any idea at all or where i could find out?

---

### Post by ctswhole on 2008-01-30
I had the Broadcom 4311 in my laptop, and I followed the guide [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)") and it worked perfectly for me.  I don't know if it will work perfectly on yours, but if you used the proper Windows driver for your card along with the other steps here, it may work out for you.

---

### Post by jleaker01z on 2008-01-30
I just got a BCM4318 working...it didnt work correctly (slow speed) with the restricted driver manager even tho it does recognize it.  I basically followed one of the guides for the BCM4311's (was actually a guide for Edgy) The steps were:

1.  Blacklist bcm43xx (This prevents Ubuntu from loading the Ubuntu driver)
2.  Downloaded the Windows drivers (.exe file), installed under Wine (on another pc, got errors tho), browsed to the C: drive under /home/uname/.wine, found the install folder, and found the .sys and .inf files  (If you have the driver cd you should be able to get the .sys and .inf files from that)
3.  Installed ndiswrapper-utils (used other PC to make a CD with the .deb files from packages.ubuntu.com as well as the .sys and .inf files as no wired connection...if you can download via wired networking obviously thats what you do)  
4.  Installed the windows driver via ndiswrapper (sudo ndiswrapper -i /path/to/bcmwl5.inf)  Then entered "sudo ndiswrapper -m" (Dunno what that actually does...)
5. Used 'sudo gedit /etc/module' and added 'ndiswrapper' to the end of the list.  (Modules is the file that tells Ubuntu what to load at startup)
6.  Entered "sudo modprobe ndiswrapper"
7.  Reboot.

Voila...perfect working order.  Even WPA works great!

---

### Post by LouisChappell on 2008-02-03
cheers for the help, ctswhole i tried that before and it didn't work, found out it was something to do with the router, it really didn't like the laptop for some reason, i tested it on my uni's one and that didn't work either, thus i thought it was the laptop, but after a fresh install and returning the router to default it worked. cheers.

---

