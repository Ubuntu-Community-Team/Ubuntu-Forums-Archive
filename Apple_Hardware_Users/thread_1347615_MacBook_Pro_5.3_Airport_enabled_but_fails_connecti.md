---
title: "MacBook Pro 5.3 Airport enabled but fails connection"
date: 2009-12-06
forum: Apple Hardware Users
---

### Post by ewhite on 2009-12-06
Ok, I confess that I'm new to Mac and Ubuntu, but, I do have quite a bit of professional networking exp. so please be kind.

Environment: MacBook Pro 5.3 Dual Boot (OS X 10.6.2) /Ubuntu 9.1 Karmic. Configured with rEFIt and everything is working fine except...

Issue: Installed the Broadcom STA driver from the Ubuntu 9.1 64bit cd and it is reported as enabled and working properly but, attempting to connect to any wifi network times out and reports as disconnected. Have uninstalled the networking packages and reinstalled. System works fine in OS X but obviously no wireless support in Ubuntu is a big problem.

Any help would be much appreciated.

Thanks.

---

### Post by linuxopjemac on 2009-12-07
It should work for 32-bit according to the wiki I think
> 
Wireless (AirPort)

IconsPage/restricted.png The Broadcom driver was not installed by default on Karmic, and it was not asked to do so either. The B43 driver doesn't seem to work here on the mbp5,3, so you'll need the STA one, connect to the Network with wired then update your apt and then Jokey (System > Admin > Hardware Drivers) will display it right Driver you can Active the Broadcom STA Driver or you can install in the Synaptic or in a terminal with the command:

 sudo apt-get install bcmwl-kernel-source

If it doesn't work/show up you may need to enable the CD as an apt source (System>Admin>Software Sources), if you don't have another network connection to work with.

Then reboot the system and you're OK. 
(from [https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Wireless%20(AirPort](https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Wireless%20(AirPort)) )

---

### Post by ewhite on 2009-12-07
Ok, thanks for the suggestion. Actually its working now. I guess it always worked for connection to Wi-Fi networks but just not for a direct ad-hoc connect to an HP Wireless PhotoSmart 4700. No big deal I guess. Thats what USB is for right? 

Thanks for the help.

Perhaps I should report the Bug?

Not sure how nit picky to be.

E.;)

---

### Post by linuxopjemac on 2009-12-08
You can always report a bug. I would search through the bug list first, it might be reported earlier already.

---

