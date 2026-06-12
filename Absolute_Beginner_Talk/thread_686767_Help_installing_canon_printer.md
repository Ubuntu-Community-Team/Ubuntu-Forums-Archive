---
title: "Help installing canon printer"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-02-03
I am suing this [http://accasonsoftware.blogspot.com/2007/11/install-canon-pixma-ip1600-printer-on.html]("http://accasonsoftware.blogspot.com/2007/11/install-canon-pixma-ip1600-printer-on.html")
to install my canon ip1600 and everything goes fine untill i need to install pstocanonbj.

I get an error saying this 

pstocanonbj:
 Depends: libcupsys2-gnutls10 (>=1.1.23-1) but it is not installable


Any ideas??

Thanks

---

### Post by linuxwizard on 2008-02-04
You might want to use the last post on this page to install driver > [http://ubuntuforums.org/showthread.php?t=558993](http://ubuntuforums.org/showthread.php?t=558993)

---

### Post by thedon_1 on 2008-02-04
No luck with that, it for some reason can't install cnijfilter-ip2200_2.60-2_i386.deb

---

### Post by thedon_1 on 2008-02-04
Also i can't now even select new printer, it just says not connected.

---

### Post by thedon_1 on 2008-02-04
Ok i got the driver file i was missing, but now because i tried to do what was suggested in the link, i can't add a new printer.

I go to printing, then what should be in go to server? How can i get my printer screen back to how it was?


Thanks

---

### Post by Benbow on 2008-02-04
I tried everything possible to get my Canon MP170 printing in Ubuntu but I finally had to resort to the unforgivable and try Turboprint which I eventually bought. It is not ideal as many of the benefits of the xp drivers are not available but it basically does the job. You can download a trial version which will tell you whether it works with your printer but prints a slogan on your sheet until you buy the licence.

If I could have got advice as to which HP printer would work with Ubuntu I would have scrapped the Canon and bought one but in the absence of the availability of Linux drivers from printer manufacturers the whole printer question appears to be a grey area.

I use Ubuntu most of the time now and only resort to xp for quality photographic printing. I would love to cut my ties with windows completely.

---

### Post by thedon_1 on 2008-02-04
Thanks for the reply mate, but i got it working.

I m managed to find the missing driver and downloaded and installed it.

To solve the CUPS problem, i went into synaptic and reinstalled anything to do with CUPS.

I then installed a new printer and use the HP IP2200 driver and it works.

Hope this helps someone with the same problem

---

### Post by kellemes on 2008-02-04
> **Benbow said:**
> I use Ubuntu most of the time now and only resort to xp for quality photographic printing. I would love to cut my ties with windows completely.

Yes, I know what you mean.. GNU/Linux isn't important enough for vendors to develop drivers for and the open source alternatives often don't offer all the features.

Well, next time you buy a new printer you get one that's supported by GNU/Linux
 and you're ties with Windows are cut. Must be a comforting thought at least.. ;-)

---

### Post by nodegamra on 2008-02-04
Can any one help please!
I did find driver.deb packages for canon printers on the Australian website. The only problem is that I have 64bit not i386. If anyone knows how to work or wrap drivers to 64bit Ill appreciate any help you can give!
I have a MP210

Here is the web site for any one that needs the the i386 drivers:

[http://www.canon.com.au/drivers/default.aspx](http://www.canon.com.au/drivers/default.aspx)

---

### Post by Golem XIV on 2008-02-04
It looks like there is another way of getting Canon printers to work under Linux.  [Here]("http://www.novell.com/products/linuxpackages/opensuse/ddiwrapper.html") is a package from Open SUSE 10.3 that acts as a wrapper for Windows 2000/XP prinetr drivers, so far it supports only Canon inkjets.

I haven't had the time to play with it, so I'm leaving the link as a reference.

Good luck!

---

