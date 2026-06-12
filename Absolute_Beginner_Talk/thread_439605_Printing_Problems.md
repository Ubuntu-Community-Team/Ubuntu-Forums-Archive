---
title: "Printing Problems"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-10
Hey there, I loaded up my printer in Ubuntu through the System -> printer setup and it reads it and tells it to print but when it does print it doesn't put anything on the paper. No ink, no lettering, no nothing on the paper. But the printer responds and goes through all the motions of it all. I can reboot into windows and print just fine. What could I be doing wrong or what can I do to fix this??  I have a HP PSC 1410 All in ONe Printer/SCanner/Copier that i've had no troubles with at all. Any advice or help is greatly appreciated! THanks!!! :)

---

### Post by brennydoogles on 2007-05-10
> **Tumpster said:**
> Hey there, I loaded up my printer in Ubuntu through the System -> printer setup and it reads it and tells it to print but when it does print it doesn't put anything on the paper. No ink, no lettering, no nothing on the paper. But the printer responds and goes through all the motions of it all. I can reboot into windows and print just fine. What could I be doing wrong or what can I do to fix this??  I have a HP PSC 1410 All in ONe Printer/SCanner/Copier that i've had no troubles with at all. Any advice or help is greatly appreciated! THanks!!! :)

I am having a very similar problem with a canon printer. Any help?

---

### Post by GranpaDan on 2007-05-10
> **brennydoogles said:**
> I am having a very similar problem with a canon printer. Any help?

What kind of Canon printer do you have ?

---

### Post by Tumpster on 2007-05-10
Hey, I need help tooo!! :)

---

### Post by Repent on 2007-05-10
I use TurboPrint to run my Cannon i960 printer, it was the only way to get it to run the way it ran in Linux.  [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by Tumpster on 2007-05-10
I could really use some help! I don't have a cannon i have an hp psc 1410!

---

### Post by GranpaDan on 2007-05-10
I'm sure this won't help in every case, but I had a problem with trying to get my Canon i560s printer to work, and I found in a thread that if I used the BJC-7000 driver in the printer set-up, it worked just great; and this was successful for me. Therefore, if you have a hard time finding your exact printer driver, there may be a compatable that will work. Searching the forum may help find where someone has solved your particular printer setup.

Good Luck !

---

### Post by benanzo on 2007-05-10
According to the Ubuntu Printer Wiki ([https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)) your printer (the HP PSC 1410) is fully supported for both printing and scanning with the hpijs driver.  Apparently Ubuntu will recognize it as the PSC 1400 but it will function normally.  I would check to make sure that you are in fact using the hpijs driver by right-clicking the printer >>Properties.  Then select the Driver tab.

Manufacturer: HP
Model: PSC 1400
Driver: hpijs

then Close, or you can try to print a test page if these settings are different than what you had before.

---

### Post by Tumpster on 2007-05-10
Thats what I have but it still prints a blank page. IT moves back and forth like it's printing but nothing is put on the paper!

---

### Post by Tumpster on 2007-05-10
Awesome, i just loaded up the latest drivers and it still prints nothing but sounds and makes like it does!! :) Anyone want to be the one to own all with my printer?

---

### Post by spur on 2007-05-10
I have had similar probs with my hp7660. I installed it again, effectivly having two of the same. It now works fine. I just made the one that works the default. I think it is something to do with it having more than one function and therefore being detected as more than one device and the nonprinting device being the one activated when you try to print.

---

### Post by Tumpster on 2007-05-10
No,that didn't work either. Still blank pages! Anything else I can try?

---

### Post by spur on 2007-05-10
At this point I would start pulling my hair out, then I would uninstall the printer, unplug it from the computer. Reboot as this will tell the system you really dont have a printer attached.
Then shut down, turn off, plug printer in, turn on, boot up and then check your hardware info and find out what it is recognised as. Then install it as what it is recognised as, and run the 'test page' thingy on the configure dialogue.
This is a bit of a long way around and generally the reboot step is not required in linux but I have found it a quick way to ensure no snags.

---

### Post by Tumpster on 2007-05-10
NO, that didn't work either. I appreciate the help so far, anyone have anything else I could try. I am NOW pulling my hair out!

---

### Post by ramjet_1953 on 2007-05-11
Check if you have[COLOR="Blue"] python-qt3[/COLOR] installed, by doing a search in Synaptic for it.

If it's not installed, install it.

Then remove the current printer installation.

Now, in a terminal type this in:

[COLOR="Red"]sudo hp-setup
[/COLOR]
Hopefully, this will do the trick and the printer will be installed properly.

Also when [COLOR="Blue"]hp-toolbox[/COLOR] is run there are all of the maintenance options for head alignment, head cleaning and ink level monitoring.

Regards,
Roger :cool:

---

### Post by Tumpster on 2007-05-11
craig@craig-desktop:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.7.4a)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Done.
craig@craig-desktop:~$

---

### Post by dstew on 2007-05-11
This last error is in /etc/X11/xorg.conf. Others have found that it is due to lines in that file that pertain to "wacom" devices, meaning stylus-type inputs. The "wacom" device lines can be commented out. Perhaps it has something to do with your printing problem, but it might not. Anyway, if some installation put the "wacom" lines in your xorg.conf, there might be other system problems that affect printing.
Here is the "wacom" thread:[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)
It might be helpful to post your xorg.conf file listing to the forum.

---

### Post by lich 6222 on 2007-05-11
> **benanzo said:**
> According to the Ubuntu Printer Wiki ([https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)) your printer (the HP PSC 1410) is fully supported for both printing and scanning with the hpijs driver.  Apparently Ubuntu will recognize it as the PSC 1400 but it will function normally.  I would check to make sure that you are in fact using the hpijs driver by right-clicking the printer >>Properties.  Then select the Driver tab.

Manufacturer: HP
Model: PSC 1400
Driver: hpijs

then Close, or you can try to print a test page if these settings are different than what you had before.

Thank you !
i have a HP deskjet D1360
it is still in pacakage
from HP site it seem it work only with win 9* and win 2000
i dint found it on your link

Question 
 1. will it work with  unbuntu 6.10
2. any information on  scanjet 4300C?
eli

---

### Post by benanzo on 2007-05-11
The D1360 isn't listed on the Ubuntu Printer Wiki, but that's just because no one who has it has entered it.  However, the D1320 is listed as working *Perfectly*.  I would assume that given HP's track-record of fantastic Linux printing support, the D1360 will be at least as well supported.  It should work fine with Ubuntu 6.10.  However, there is a new hpijs driver version included in Ubuntu 7.04 if the old one doesn't work.

[http://www.linuxprinting.org/printer_list.cgi?make=HP](http://www.linuxprinting.org/printer_list.cgi?make=HP)
A really good place to search and ask is the OpenPrinting.org forum.
[http://forums.openprinting.org/list.php?20](http://forums.openprinting.org/list.php?20)

here is a post that discusses a very technical problem with grayscale printing (which looks to be solved) but you can discern from the conversation that the D1360 is in fact supported and working normally. [http://forums.freestandards.org/read.php?20,1649](http://forums.freestandards.org/read.php?20,1649)

This is part of LinuxPrinting.org which is now sponsored by the Linux Foundation, a consortium of large companies including IBM, Intel, HP, etc. to promote the use of Linux and provide proper backing of Free Standards..ie, printer drivers.  This is why Intel hardware works so well with Linux.  And why HP printers work so well..

---

### Post by Tumpster on 2007-05-11
I now have a working, printing, printer! :) Much respect and love to those of you who helped me!! :)

---

### Post by Tumpster on 2007-05-24
I'm printing blank pages again!! ARGGHHH!!

---

