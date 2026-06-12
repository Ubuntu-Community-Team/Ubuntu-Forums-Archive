---
title: "Which ATI driver?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-07-23
Could someone point me to the right ATI Driver? -I have an X800 PCIe card and ATI's driver page   ( [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27) ) has 3 options: 1)ATI Driver Installer v8.26.18, 2)XFree86 4.3 v8.26.18, and 3)X.Org 6.8 v8.26.18.
I've tried DLing all of them but the first one hangs at about 20% and the other two won't even start to download.
I've never touched Linux before but I'm looking forward to learning -I'll be installing Ubuntu as soon as I get the drivers for my vid card -I've also heard that installing ATI drivers can be hard: any pointers?
Thanks very much for your time.

(My PC Specs if that helps):
      CPU Type:   Intel Pentium 4E, 3400 MHz
      Motherboard Name:   Unknown
      Motherboard Chipset:   Intel Grantsdale i915
      System Memory:   1024 MB
      BIOS Type:   AMI (09/24/04)
   
      Video Adapter:   RADEON X800 Series (256 MB)
      Monitor:   SamsungSyncMaster191N

      Audio Adapter:   Creative Audigy Platinum Sound Card

      Disk Drive:   WD2500JD
      Optical Drive:   LITE-ON DVDRW SOHW-832S
      Optical Drive:   SAMSUNG DVD-ROM SD-616E (16x/48x DVD-ROM)

---

### Post by GuitarHero on 2006-07-23
I think Automatix can install them for you....

---

### Post by catlett on 2006-07-23
[http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29](http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29) I followed the Dapper Guide when I installed my ATI drivers.
The Dapper Guide is what I use when I set up a new install. It is easy to follow (believe it or not) If you just follow it step by step and copy/paste the commands from the guide into the terminal, it can set up your system with all the basics (i.e. drivers, dvd playback, mp3 support, codecs etc.) [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by fiver22 on 2006-07-24
Thanks very much for the suggestions -I've bookmarked the links and will try out the instructions. -I'm still a bit unsure if I'll be able to pull it off as I'm *completly* new to Linux and using the command line. 
-Can't wait till the .iso finnishes downloading so I can start learning!
Thanks again.

---

### Post by djsroknrol on 2006-07-24
It depends on what you have plans for..I use the "Radeon" OSS driver but some people use the "Fglrx" driver for heavy duty eye candy...not that the "Radeon" driver won't handle _some_ eye candy..it's a matter of preference and usage...

---

### Post by Kilz on 2006-07-24
For radon express graphics. Get the 8.26.18 ati-driver-installer. [Use this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") Save yourself the problems of trying to install the 8.25.18 driver in the repositories. IMHO its the worst driver ever written for express graphics.

---

