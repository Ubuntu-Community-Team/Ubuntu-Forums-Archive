---
title: "Printer Suddenly Won't"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-06-29
:( Suddenly, my Laserjet 2200 won't print. 

I opened an email from the Hamilton County Park District, and attempted to print a web page from a link there; but the printer won't respond. I fiddled with clicking on this and that, and it printed a page; so i know it's now hardware. The CUPS icon on the toolbar shows that the last job I attempted is still processing. If I try to delete it, I get a message that says: "There was an error during the CUPS operation; 'client-error-not-possible'. " 

I also noted that I have not one, but two "printing"  icons in my system administration panel. Might this have something to do with it? If so, how do I eliminate one?

Thanks in advance.

---

### Post by seetho on 2007-06-29
How are you connected to your printer?  (Network, USB, etc...)

Does it not print anything else, like a simple text file?

Will it print a test page?

Are you able to configure your printer by System->Administration->Printing...?

---

### Post by sailor2001 on 2007-06-29
probably need to ctrl/alt+backspace to reboot into a new session

---

### Post by wmichaelb on 2007-06-30
Seetho:
- It's connected via a USB port. It is in fact the only USB port that I'm using at the moment, so there should be no conflicts. 
As of this morning, after rebooting...
- It prints a test page from the button on the printer front panel;
- It prints a test page from gedit
- It prints the web page that it wouldn't yesterday
- It will NOT print an image from Eye of Gnome. The dialog box indicating that the file is being prepared opens and then closes, the LED on the printer blinks, indicating that the printer is processing something...but then nothing happens, and the printer continues to blink for 10-20 minutes (or until I get bored and recycle the printer power). 

Phase of the moon? Wolfbane pollen concentration? Windows disease?

---

### Post by seetho on 2007-07-01
It's probably bugs somewhere.  I have the same experience printing from some apps (I forget which ones) sometimes.  It says it is preparing to print but then you wait forever and nothing happens.  It's not the printer I think.  I experienced it o both my Canon IP4000 connected via USB and Samsung CLX-3160N connected on LAN.

---

### Post by bobhawkes on 2007-07-08
I have the same problem (?) with my Canon ip4000. Does anyone have a fix?

It will always print one document. The second sometimes fails to print. After that the printer is not available as an option when printing. Turn the machine off (restart doesn't work) and restart a while later and the missing document prints, even without logging in. It looks as if the output gets stuck in the print queue.

Bob

---

### Post by eddieb on 2007-07-10
Hi , Same here. Epson C70, prints ok for several prints then refuses to print. I have to reboot the computer and then the printer prints the job without being told too. The only thing I have noticed is the printer is normally VERY quiet, but before it refuses to print it gives off a very loud screech, immiediately after printing the last sheet.
I have recently changed from 64 bit to 32 bit and never had this prob with the 64 bit Ubuntu.
Also the print quality on the 32 bit  varies quite a lot. Never on the 64 bit.

---

### Post by mozgreen on 2007-10-30
Clean install Gusty (amd64) last week and all was very well 'till Epson Stylus DX6050 (scanner/copier/printer) with usb connection would suddenly not print and document print status 'stopped.'  Printed good photos and OpenOffice work  the day before.  Message when trying to cancel job:
"There was an error during the CUPS operation: 'client-error-not-possible'."
In [http://localhost:631/printers/](http://localhost:631/printers/) I clicked 'start printer.'  Nothing.   But the same button has changed to 'stop printer.'  CUPS software looks quite nifty.  Unfortunately the system is effectively useless for my needs.  HELP!
:confused:

Moz    Linux nooobie

See also:
[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/137984](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/137984)

---

### Post by nuclearj on 2008-06-19
Okay so this worked for me, I just turned the printer off and then back on again.  Well see if it happens again.

---

