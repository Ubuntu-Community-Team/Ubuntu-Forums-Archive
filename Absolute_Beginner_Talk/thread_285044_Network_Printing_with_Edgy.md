---
title: "Network Printing with Edgy"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by protaginist on 2006-10-26
I have been struggling with getting my brother laser network printer working with the Beta version of Edgy for quite some time and finally stumbled across a method that worked nicely. I had been looking at all the comments with no luck. Anyway, here is what worked for me.

I downloaded the Kubuntu Live CD and booted it. From there I went to "add printer" utility and ran it. When it came to the dialog box where you can type in the URI or do a network scan I used the scan feature. With the scan for printer part of the box there is a place to enter the subnet which will be the first three parts of the router IP address. In the case of my Linksys that was 192.168.1 and then make sure the port is set to 631. With that info entered click scan and see if it finds your network printer. If it does then copy that address down exactly as shown. When you reboot into Ubuntu enter that address when prompted during the add printer utility.

The address I came up with was not even close to the format examples shown by Ubuntu add printer dialogs. In my case it was ipp://xxx.xxx.xxx.xxx:631/ipp which was why I could never get it working following the examples.

Anyway, hope this helps someone set up a network printer. If you already know the printer IP address you can try the example format above first and see if that works. Note that if you are using a Brother printer if you need to add a driver for it you will find it on the printer CD. Just use the .PPD file under the Driver/PS/PPD/(Select your language here). There should be a similar PPD file on other printer driver disks.

---

### Post by rmjb on 2006-10-26
Good tip! Great find.

- rmjb

---

