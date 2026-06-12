---
title: "Still Stuck!!"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-13
Hi everyone,

I have been having a good look around for help on this problem and I'm no further forward.  So far I have installed ndiswrapper and used that to envelop my D-link drivers *.inf and *.sys.  Using the command to see if these drivers had installed correctly, I still see 'invalid drivers'.  The problem seems to be getting Ubuntu to recognise the USB dongle device plugged into the back of my computer.  I think that once I have got over this hurdle, internet connection will be in reach.  Any ideas please :confused:

---

### Post by Stealth on 2006-03-13
Brand of the actual device would be nice ;)

---

### Post by Norfolk 'n' Good on 2006-03-13
Hi,

The device I'm using is a Wireless ADSL Router (DSL-904). Hope that helps.  I have hunted around the Wiki pages and others for it, but it does not appear to be listed.

Regards

Mark

---

### Post by chuckyp on 2006-03-13
No he meant the brand and model of your usb dongle you are trying to connect to the wireless router with.

Also with the ndiswrapper you need to use the inf and sys they suggest on their site for your particular card.  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)  

If you go to the install section of their wiki and click on the "list" it will give you a download link for the proper drivers.

---

### Post by Norfolk 'n' Good on 2006-03-13
You know, it didn't occur to me to look at the lable on the back of the dongle.  I had been taking my information from the packaging it came in!

Anyway, here goes... model no. DWL-G122.  There are more numbers, but i'm gonna have to get down to spec-savers before I can read them :D

---

### Post by Stealth on 2006-03-17
Yup, it definitely looks possible to install, according to this section in the [NDIS]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D") wiki there are 2 versions of it, one with Prism drivers, and another with some RaLink? Check out the instructions there...

---

