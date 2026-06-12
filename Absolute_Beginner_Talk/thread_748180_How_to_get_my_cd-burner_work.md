---
title: "How to get my cd-burner work"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by kleinshagua on 2008-04-07
Hello,
is there someone able to help me get my burner working. System is ubuntu 7.04. The drive can read data cd´s, but if I try to burn, brasero aks for a disk, I put one in, close the tray, the green light goes on, that´s it. The light never flashes, brasero freeses. The same with k3b.
I replaced the compl. cd-rom-drive allready with another ide drive.

---

### Post by StOoZ on 2008-04-07
what's the burner type?

---

### Post by phidia on 2008-04-07
You can use the command line/CLI to burn from with the cdrecord command.
For more specfics do man cdrecord or look [here]("http://wiki.linuxquestions.org/wiki/Burning_a_CDROM_from_an_ISO_file").
Even though you probably don't want to burn from CLI all the time using cdrecord may give you useful error reporting.

---

### Post by kleinshagua on 2008-04-07
Thank you for your answer,
and to your question: it´s a Sony CRX0811

---

### Post by kleinshagua on 2008-04-07
phidia,
thank you for the link. 
In places: computer: is my cd-burner Sony CD-RW CRX0811, Connection ATA
WHY and HOW do I get this:  cdrecord -scanbus can not open scsi driver. CD-RW is hdc, DVD is hdb.

---

### Post by phidia on 2008-04-07
What version of ubuntu are you running, and what happens if you put a blank disc in the burner? If you are not seeing a desktop icon of the blank disc and you are using a recent version of ubuntu then perhaps the drive is not working correctly?

---

### Post by kleinshagua on 2008-04-08
Hi phidia,
my system is an upgrade to 7.04 from 6.10. Kernel is 2.6.20-16 generic. If I put in a blank cd, no icon on the desktop. With a KNOPPIX cd, the icon pops up and it opens with a browser.

---

