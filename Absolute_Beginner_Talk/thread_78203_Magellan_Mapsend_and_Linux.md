---
title: "Magellan Mapsend and Linux???"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by ZoomZoom on 2005-10-18
I would like to be able to run my gps mapping software on Linux, (Mapsend, Fugawi, Sotmap,etc...). Would Wine or Xwine or whatever it's called work? I also need to know how to install this software, so where would I find a step by step quide on that? Is it at all possible to run my mapping software in Linux.
 I just updated to Breezy, clean install and see no problems yet.

---

### Post by stalker145 on 2007-08-25
By the power of Greyskull I resurrect this thread :D

If you're still around and wondering about MapSend, I can say that (for now) the software works... to a point.

I just purchased a Magellan eXplorist 210 and was tinkering to see if the software worked through WINE. I can move around in all the programs, but I can't seem to get the programs to "see" the GPS unit (USB-type).

Anyone have any ideas on what needs to be done next?

Thanks in advance.

---

### Post by ramjet_1953 on 2007-08-26
I apologize that this is a bit off topic, but you may want to check out this link, as it provides a mapping application that is Linux native.

[http://www.gpsdrive.de/](http://www.gpsdrive.de/)

It is available in the repositories.

[COLOR="Red"]sudo apt-get install gpsdrive[/COLOR]

I hope that it does what you are looking for.

Regards,
Roger :cool:

---

### Post by stalker145 on 2007-08-26
> **ramjet_1953 said:**
> I apologize that this is a bit off topic, but you may want to check out this link, as it provides a mapping application that is Linux native.

[http://www.gpsdrive.de/](http://www.gpsdrive.de/)

It is available in the repositories.

[COLOR="Red"]sudo apt-get install gpsdrive[/COLOR]

I hope that it does what you are looking for.

Regards,
Roger :cool:

Looks like an **outstanding** program... I'm sure that it will meet my needs and I hope that others find it useful as well.

As for the other problem I had above  ](*,)  I had the cable attached upside down. Funny, it drew power from the USB so I thought it was right... just decided to try something different.

---

### Post by Kirk_3 on 2008-01-31
Hi

I have just attempted to install Magellen MapSend.  The installation through Wine seemed to be going very smoothly.  MapSend is a two disk set, you have to put the data disk in the cd drive to run the program.  This is where I ran into a problem.  The program asks for the 2nd disk to be inserted, but it doesn't recognize the insertion of the 2nd disk.  I have not given up hope yet and if I can figure out how to fix this, I will post it.

---

### Post by seventhc on 2008-01-31
wow, it only took 2 years to get a reply...not bad :lolflag:

---

### Post by minophis on 2008-02-18
I installed Mapsend under Wine this weekend. I copied the contents of the CD's to two separate directories and ran the install from the first directory. When the install asked for the second disk I pointed it to the second directory. It worked for me.

My current problem is that Mapsend produces .rgn files which need to be converted to .imi or .img for my Explorist 600. I installed the Magellan Conversion Manager but it cannot see my GPS or the SD card when it is placed in my card reader.

Can anyone help?

I am running Gutsy on a Dell Inspiron 1520

---

