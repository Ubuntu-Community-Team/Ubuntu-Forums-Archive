---
title: "No Printing on Shared Windows HP Printer via Samba"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by homergreg on 2007-05-27
I am having difficulty printing on a HP PSC 1110 multifunction printer that is attached to an WinXP computer.  I can see and install it.  It shows up on CUPS just fine, and I get a report that a print job has been sent.  Then in the XP machine, the print job shows up and the printer starts waking up, then the power light starts flashing.  The queue in the XP machine says there was an error with the printer.  It works fine as a windows to windows share, there is just apparently something wrong in the way my computer is formatting the print job.  If I hook the printer directly to my ubuntu box, it works fine.  I am using the Foomatic hpijs driver.  Thanks for any help!

---

### Post by wetland on 2007-05-27
I remember doing this a while back and I needed to supply a user name and password for an account on the xp box. I set up a limited user account on xp for this purpose. Here's a [link]("http://www.linuxquestions.org/linux/answers/Hardware/Printing_from_Linux_to_an_HP_OfficeJet_5510_on_XP_Pro_via_CUPS")   to a better explanation.

---

### Post by homergreg on 2007-05-27
Thanks, I tried your suggestion, it didn't help, but I think I found the problem:  I found a thread at dsl reports that makes me think this is no easy fix.  [http://www.dslreports.com/forum/remark,17623046]("http://www.dslreports.com/forum/remark,17623046") 
It looks like if I set up ghostscript as a go between on the Windows PC that I can make it work, but I might just buy a nice wireless USB print server  and untether the printer from my wife's computer.

---

### Post by Offoffoff on 2007-06-09
Try to start printer manager through console:
```
sudo gnome-cups-manager
```
I have done settings with root-privileges.
It helps for me.
My windows-printer from my local net was install right in My Ubuntu, but authentication cannot run right, printer waits something with pause.

---

### Post by emil_p8 on 2008-03-15
Solved for me:
(briefly, in windows disable "bidirectional printing" for the shared printer):

[http://forums.techguy.org/unix-linux/414003-solved-ubuntu-printing.html](http://forums.techguy.org/unix-linux/414003-solved-ubuntu-printing.html)

---

