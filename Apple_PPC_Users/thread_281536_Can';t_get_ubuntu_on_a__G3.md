---
title: "Can';t get ubuntu on a  G3"
date: 2006-10-21
forum: Apple PPC Users
---

### Post by kb0oqz on 2006-10-21
Hi I am a newb to Ubuntu and to apple. I have tried everything I can but can't get Ubuntu on my IMAC G3 front slot loading. This machine is a 400 NHZ, 256 megs or ram and a 40 gig HD. It just keeps blanking out with no picture. I can hear the music from start up but nothing on the screen. I have downloaded and tried to put every Ubuntu including 5.10. I don't know what to do for it. Could someone help? I am about to give up on it.

---

### Post by markd1216 on 2006-10-21
This is a common G3 problem.  I did a search when I had the same problem starting my 600 MHz iMac and found this from a poster who deserves the credit. Worked for me.  Mark

The LiveCD does not write the correct display settings for the iMac  
G3 into xorg.conf. You will need to fix manually. (If you're not  
familiar with the command prompt, be aware that commands are case- 
sensitive. Type carefully!)

After booting is complete:
ctrl-option-F1 (should give you a command prompt, may take a couple  
of tries) type: sudo nano /etc/X11/xorg.conf (return)
Make your edits:
In the monitors section modify "HorizSync" to 60-60 and "VertRefresh"  
to 75-117
In the modules section disable DRI by putting a hash mark (#) at the  
beginning   of the line containing "load DRI"
ctrl-O (return) to write edited file
ctrl-X to exit nano back to command line
type: sudo killall -HUP gdm (return) to restart

---

### Post by thayne on 2006-10-24
I couldnt get the regular Ubuntu to install on my G3 ibook either, but Xubuntu installed no problem :) [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Gimlet on 2006-10-24
> **thayne said:**
> I couldnt get the regular Ubuntu to install on my G3 ibook either, but Xubuntu installed no problem :) [http://www.xubuntu.org/](http://www.xubuntu.org/)

I can't get my G3 to boot from the cd no matter what I do anyone out there got a solution. I am new to Macs as far as I understand this is a G3 power PC with 233 procceser and 320 megs ram. I have tried holding the c key down during boot. I have also set the box to boot from cd in the control panel and still no go I have tried both ubuntu and xubuntu 6.10

---

### Post by eddieboyinla on 2006-10-24
When You Startup The G3, Make Sure That The Cd Is In The Drive, Push The Button On The Side Of The Computer (that Looks Like An Arrow Pointing Left 9 It Is Next To The Usb Female Plugs ), Then Push And Hold The Little Butto Next To (to The Right) And Hold It Until You See A Screen That Shows A Hadrdrive And It Will Scan Your Cd-rom To See If It Contains A Valid Image To Boot From, Still Wait Until The (time-piece) Changes To A Standard Coursor (arrow, Simple Click The Cd-rom Drive Box, And Continue, It Helps If Your Hardware Clock Is Correctly Set
----any Q's Feel Free To Ask, Later And Good Luck.

---

### Post by eddieboyinla on 2006-10-24
Ubantu Oly Requires 133 Mz And At Least 192 Mb Of Ram, For A Seemless Install, Later

---

### Post by gubu on 2006-10-26
hello - this is my first post, so be kind.

I write this from a blue&white imac G3 running kubuntu 6.06.  It is a summer 2000, 400 Mhz, slot loading

I too had trouble with the install using a "regular" ppc iso.  However, I was able to get up and running by installing the [B]alternate ppc.iso
[/B]
give that a try.  you can find it at most mirrors.

NOTE:  It appears Edgy will not run on a G3?  I am not sure of this and have found no help or info about it, but it is the evening of the release of Edgy!

Does anybody have info about this?  The support page seemed to indicae only G4 and G5 support.

yours in Linux,  gg

Moobie - Medium grade Noobie

---

