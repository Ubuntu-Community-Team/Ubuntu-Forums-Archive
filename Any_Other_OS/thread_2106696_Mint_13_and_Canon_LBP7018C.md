---
title: "Mint 13 and Canon LBP7018C"
date: 2013-01-19
forum: Any Other OS
---

### Post by Buovjaga on 2013-01-19
Helping out my neighbor here..
I first followed this advice, modifying it accordingly:
[http://phpraxis.wordpress.com/2012/07/08/install-canon-mf4350-cups-printer-drivers-in-64-bit-ubuntu-linux/](http://phpraxis.wordpress.com/2012/07/08/install-canon-mf4350-cups-printer-drivers-in-64-bit-ubuntu-linux/)
I generated .debs with alien from the Canon 64-bit RPMs. An important question: are the ones by Michael Gruz somehow better (the ones called cndrvcups-common_2.20-1ubuntu4_amd64.deb and cndrvcups-capt_2.20-1ubuntu3_amd64.deb)? Does the version number 2.20 refer to an older version in comparison with the current Canon 2.40?

Anyway, printing didn't work, even though the jobs completed fine, with Unknown user displayed in the print queue.

Then I found this great and detailed tutorial: [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)
So I proceeded to remove the ia32-libs I had installed while following the previous tutorial and installed the 11.10 package instead and locked it (and also the ia32-libs-multiarch just in case).

I completed the French tuto and I still couldn't get any actual printing going on. Then I started wondering about the peripheral URI and tried the USB location instead of ccp://localhost:59787 (it can be changed easily in the admin web interface). I think there might have been some ccp error displayed in the admin interface print queue view that prompted me to try this. I successfully got captstatusui running and could manipulate the printer, adjust the sleep setting and make it calibrate itself - still no actual printing!

So the main things I'm wondering about now are the possible importance of the Michael Gruz .debs and ccp://localhost:59787.

---

### Post by Buovjaga on 2013-01-20
I removed the packages created with alien and installed the Gruz .debs closely following the instructions in the French tuto.  Now when I do captstatusui -P LBP7018C it shows Printer Error and Check the DevicePath of /etc/ccpd.conf, even though the path is ok.
When I print a test page from the CUPS web interface, the job gets this note: *"ccp send_data error, exit"*. The user is anonymous.
I have Connection: ccp://localhost:59787

The command sudo /usr/sbin/ccpdadmin
shows:
> 
CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path   : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP7018C  : ccp           : //localhost:59787     : /dev/usb/lp0  :Then if in the CUPS web admin I modify the printer and select the radio button Canon LBP7010C/7018C (Canon LBP7010C/7018C), I see Connection: usb://Canon/LBP7010C/7018C?serial=0000A2C3JExe in [http://localhost:631/printers/LBP7018C](http://localhost:631/printers/LBP7018C)

Now captstatusui doesn't launch and says ** captstatusui Socket Error ***
Jobs complete without actually printing.

When I do sudo service ccpd status
I get:
/usr/sbin/ccpd: 2036 2034 2032 2031 2029 2028 2025 2022 2019 2015 2014 2007 2004 2003 2001 2000 1999 1998 1987 1985 1984 1982 1976 1971 1970 1962 1954 1952 1951 1950 1949 1948 1947 1946 1945 1943 1942 1938 1937 1933 1932 1926 1925 1914 1910 1907 1906 1900 1899 1893 1892 1889 1888 1887 1885 1884 1883 1881 1879 1878 1877 1873 1872 1871 1865 1864 1862 1861 1859 1857 1854 1850 1844 1836 1822 1816 1813 1809 1808 1807 1800 1799 1788 1787 1785 1781 1779 1778 1776 1774 1768 1767 1763 1762 1761 1760 1759 1758 1756 1755 1752 1751 1750 1749 1745 1744 1740 1739 1735 1734 1732 1731 1730 1728 1727 1726 1724 1723 1722 1721 1720 1718 1717 1716 1714 1712 1710 1709 1707 1704 1702 1701 1700 1699 1697 1695 1694 1690 1688 1687 1682 1681 1677 1637 1577 1558 1551 1549 1547 1546 1545 1544 1541 1540 1539 1538 1537 1535 1534 1533 1532 1531 1530 1529 1527 1526 1525 1524 1523 1521 1520 1518 1517 1514 1512 1511 1509 1508 1505 1504 1502 1501 1500 1499 1497 1496 1495 1494 1491 1490 1487 1470 1469 1455 1453 1441 1440 1438 1437 1435 1425 1412 1411 1394 1393 1370 1341 1320 1283 1206 1202 1188

If I do lsusb, I get:
Bus 001 Device 002: ID 04a9:271c Canon, Inc.

---

### Post by Buovjaga on 2013-01-20
Ah, now I realized the 2.20 drivers I tried in my second message don't even support LBP7018C..

edit: I went back to the 2.40 drivers and now I'm at a quite healthy situation: I have Connection: ccp://localhost:59787 and yet the captstatusui works and says ready to print. The jobs still don't lead to printing. I get these notes in the jobs:
[I]"Can't connect to CCPD: Connection refused"
[/I]
Once a printing action lead to the printer activating, but it didn't print anything despite a 30 sec rumbling.
I even allowed the IP address of this machine in **/etc/cups/cupsd.conf**

---

### Post by pdc on 2013-01-21
I see from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

that the capt driver is at 2.50 [COLOR="SeaGreen"]Linux_CAPT_PrinterDriver_V250_uk_EN.tar.gz
[/COLOR]


sadly, sometimes good is better than *better*:

and sometimes [COLOR="Blue"]OK[/COLOR] is much better than *better* ..

*better* is having a 64bit system ... that sounds great..with a printer that doesn't work ...........

[COLOR="Blue"]OK[/COLOR] is having a 32bit system.. that doesn't sound half as impressive as 64bit ..with a printer than works ............

---

### Post by Buovjaga on 2013-01-21
> **pdc said:**
> I see from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

that the capt driver is at 2.50 [COLOR=SeaGreen]Linux_CAPT_PrinterDriver_V250_uk_EN.tar.gz
[/COLOR]


sadly, sometimes good is better than *better*:

and sometimes [COLOR=Blue]OK[/COLOR] is much better than *better* ..

*better* is having a 64bit system ... that sounds great..with a printer that doesn't work ...........

[COLOR=Blue]OK[/COLOR] is having a 32bit system.. that doesn't sound half as impressive as 64bit ..with a printer than works ............

Yep, I should have installed a 32-bit system for my neighbor in the first place. I will test on a laptop with 32-bit in a couple of days and report here.

It's funny that Australia and Asia offer that version 2.5 :) I just got tipped about it today elsewhere. Didn't work, though! But I will surely use the 2.5 32-bit .deb in the next test.

---

### Post by pdc on 2013-01-21
> It's funny that Australia and Asia offer that version 2.5

I guess Canon is an Asian company originally ........ and Australia and NZ are innovative places!!

all best wishes with your 32bit install:

I see you used the > ccp://localhost:59787 from here

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

I think that saves all the fifo directory stuff:

I have the 2.40 driver installed; I see there is the 7018CCAPTK.ppd in that; in /usr/share/cups/model/

so when one registers the printer

> sudo /usr/sbin/lpadmin -p LBP7018C -m CNCUPSLBP7018CCAPTK.ppd -v ccp://localhost:59787 -E

.....the 2.40 release has what is needed ......

I think Sivella in post #4 here

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

gives a great description of how to get an LBP working: I prefer the ccp://localhost:59787 -E though that you used

---

### Post by Buovjaga on 2013-01-21
> **pdc said:**
> I guess Canon is an Asian company originally ........ and Australia and NZ are innovative places!!

all best wishes with your 32bit install:

I see you used the  from here

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

I think that saves all the fifo directory stuff:

I have the 2.40 driver installed; I see there is the 7018CCAPTK.ppd in that; in /usr/share/cups/model/

so when one registers the printer



.....the 2.40 release has what is needed ......

I think Sivella in post #4 here

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

gives a great description of how to get an LBP working: I prefer the ccp://localhost:59787 -E though that you used

Sivella aka murex put together that lovely French tuto in my first post. So he has moved to the ccp://localhost:59787 -E method since that forum post.

---

### Post by Sivella on 2013-01-24
Hello Buovjaga,

Your printer is not supported by the v2.20 Canon driver.
You must use the.v2.50. Here it is :
[http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)

If you are running a 32 bits version you can install the 32bit .deb (v2.50) provided by Canon.
Then install you printer :
[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

If you are running a 64bits version, you could compile from the Canon sources :
[http://doc.ubuntu-fr.org/imprimante_canon_capt2](http://doc.ubuntu-fr.org/imprimante_canon_capt2)

Then install you printer.
Good luck.

(hope you are enough comfortable with french ;) )

---

### Post by Buovjaga on 2013-01-24
> **Sivella said:**
> Hello Buovjaga,

Your printer is not supported by the v2.20 Canon driver.
You must use the.v2.50. Here it is :
[http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)

If you are running a 32 bits version you can install the 32bit .deb (v2.50) provided by Canon.
Then install you printer :
[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

If you are running a 64bits version, you could compile from the Canon sources :
[http://doc.ubuntu-fr.org/imprimante_canon_capt2](http://doc.ubuntu-fr.org/imprimante_canon_capt2)

Then install you printer.
Good luck.

(hope you are enough comfortable with french ;) )

Yes, I'm comfortable with French, I have read your tutos intensively in the past week. Now I got it working on my laptop with Mint 14 32-bits, so I will reinstall my neighbor's system with Mint 14 KDE 32-bit. It was funny that even the 32-bit system didn't work immediately, but finally after some service restarts and reboots I also restarted the printer itself and then it started to print!

So the bottom line is: do not try LBP7018C on a 64-bit system that uses .debs for package management! Would be interesting to hear some experiences with the 64-bit RPMs, though.

---

### Post by howefield on 2013-01-24
Thread moved to the "Other OS/Distro Talk" forum.

---

