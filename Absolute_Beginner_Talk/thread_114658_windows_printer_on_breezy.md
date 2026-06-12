---
title: "windows printer on breezy"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by hobbes_opus on 2006-01-09
Trying to access a shared printer on a windows computer (SMB) from Ubuntu, one that used to work with the Hedgehog, but doesn't with Breezy.   I've tried tons of trial and error, to no avail so far.

Any ideas?

---

### Post by Terry of Astoria on 2006-01-09
Is the SMB client installed?
Are the settings correct on the Windows machine?
Any more information on your problem?
Error messages?

---

### Post by hobbes_opus on 2006-01-09
[QUOTE=Terry of Astoria]Is the SMB client installed?
Are the settings correct on the Windows machine?
Any more information on your problem?
Error messages?[/QUOTE]

Terry, I'll answer your questions to the best of my ability:

First, thank you all for helping in the Ubuntu Forums, this is my first post. I'm helping my son to learn Linux through Ubuntu, but we're stuck on printing. The worst part of this that we first installed Hoary Hedgehog and then the printer worked fine with a little diddling on host naming,  but now we have installed Breezy Badger and can't get anything to happen on the printer.

We have a shared printer on a Windows ME machine also on our LAN. Adding a printer in Ubuntu Breezy Badger found it fine, installed the recommended driver, but nothing prints - action seems to go into sockland. No error message.  I tried playing with the host and printer naming structures, and here is one of the ever-changing error messages from Status in Printer Properties:

Ready: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR: Connection failed with error NT_STATUS_UNSUCCESSFUL

Frankly, the error messages seem to vary as I try to re-set the connection settings, but not by much. Here are the current connection settings:

Driver: pnm2ppa
Network Printer
Windows Printer SMB
Host: [blank]
Printer: /MSHOME/FAMILY COMPUTER/HP712C
User: [blank]
Password: [blank]

Although no password is set on the WinME computer, and this may not be important, I notice that when we close the properties, some long password [*****************] is reinserted by Samba (sometimes).

Any thoughts? We've done trial and error for hours to no avail...I do notice on Ubuntu forums this appears to be a common occurence, and I did read many but did not see a solution.

Thanks for responding!
Bob

---

