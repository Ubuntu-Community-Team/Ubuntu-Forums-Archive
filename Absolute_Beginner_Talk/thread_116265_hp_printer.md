---
title: "hp printer"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-01-12
Just installed ubuntu with gnome.....It recognizes my printer (hp deskjet 712c) however when I send to printer (test page or script) it says it has sent, but the printer doesn't recieve it. Switched to kade and it downloaded a driver  but the same thing happens....... need help...........am a newbie

---

### Post by DoorGunner on 2006-01-12
you may need to system > administration > printing 

select a local printer and add your printer.....it should default to it.


(that is if you havnt already done so....if you have disregard)

---

### Post by jorn on 2006-01-12
That reminds me of having a semilar problem.
Do you use an USB - port, and did you add the correct port when configuring?
Just a suggestion.
Regards -Jorn

---

### Post by sailor2001 on 2006-01-12
it's a serial port

---

### Post by sailor2001 on 2006-01-12
oops.. parallel port... but still doesn't work

---

### Post by Sef on 2006-01-12
Did you download the driver for it?  It's a pnm2ppa.  Get it from Linuxprinting.org.
Here is the page:  [http://linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_712C]("http://linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_712C")

Edit:  Check synaptic and see if the driver - pnm2ppa - is in the repositories.

---

### Post by sailor2001 on 2006-01-12
fixed by editing pnm2ppa file    thanks:p

---

### Post by Sef on 2006-01-13
How did you edit it to get it to work? ( If someone else has the same problem as you, then they could read your post to get their printer working.)

---

### Post by jvslice on 2006-01-14
sailor is an uncle of mine and last week, I installed Ubuntu for him, so I am answering for him with additional details.

sudo gedit  pnm2ppa.conf

found the line which was not commented out with "#" that said version with no other text and change that line to  version 712.  Note did not have to add the "c" in the printer's model line.  saved the file and all is fine now.

---

