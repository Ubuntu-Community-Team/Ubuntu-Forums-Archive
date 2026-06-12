---
title: "Networking a printer - Xerox Phaser 6120???"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by mickfitz on 2007-11-20
Hello ... I'm new to Ubuntu, but very impressed so far.

I have a printer Xerox Phaser 6120 that is already networked into my home xp network. My next task is to get the Ubuntu box using it.

There is Linux drivers on the installation CD.

That's the end of my 'knowledge' :)

Is there a 'how to' out there that may help or is some kind soul patient enough to help?

TIA Mick

---

### Post by PointyWombat on 2007-11-20
Try System->Admin->Printing->New Printer.

Select your brand and model (or closest), and that should be it.

---

### Post by halitech on 2007-11-21
As pointy says, use the steps to get into adding it. You should get an option to select an actual PPD file, just browse to the CD the same as if you were installing a windows driver so you can get the right model.

Now, you say it is "networked", do you mean it is connected to a windows box with a USB cable and shared out or is it on an ethernet connection direct to a router?

---

### Post by carstanje on 2007-11-21
I also use a 6120 for over a year now. Works perfect with ubuntu via the Network.

I remember the installation was pretty smoothly, and the driver works actually better than windows for duplex printing. I even suppose when installing ubuntu will find the printer itself.

I think this printer will be in de default list of CUPS (printing system), otherwise let me know and I will probably find the ppd file.

Good luck!

---

### Post by lns on 2007-12-17
For anyone who wants to download the Xerox PPD file directly from their site:

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=52053&EULA=5&prodID=6120&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=]("http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=52053&EULA=5&prodID=6120&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=")

And for the record, I wasn't able to get the Gutsy-default PPD to work correctly, in 2 separate installs... I haven't tested the downloaded PPD yet, but I assume it will be a bit better (the Gutsy default rendered a 2-page testpage - one with "oX" on it, and another with weird upper-ascii "ink blots" according to the onsite tech).

***EDIT***
I verified the newly downloaded PPD works - I used the "not '-open' " PPD (there were 2 in the tarfile under the 'english' subdirectory).

Just dropped it in /etc/cups/ppd (copied it as the original PPD name) and did a 'sudo /etc/init.d/cupsys restart'. Worked great.

---

