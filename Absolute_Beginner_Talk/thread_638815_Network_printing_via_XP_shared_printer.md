---
title: "Network printing via XP shared printer"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Mikjoba on 2007-12-12
I have a XP machine (Compaq Evo) that is always on and which is mainly used as a file server for my D-Link media hub, it also has a HP1200 laser attached via USB which is shared out and which can easily be accessed and printed to from other Windows machines on the home network, I have recently installed Xubuntu on an old laptop (HP Omnibook) with no major problems at all, I am, after some Samba configuration and the installation of pyNeighborhood able to browse the network and access files in both directions, I am even able to see and mount print$ (printer drivers) on the Evo but I have not been able to figure out how to get this working from the laptop, downloaded a program called xprinterconf which didn't help then tried installing the printer using CUPS ( browser based configuration [http://localhost:631](http://localhost:631)) this accepted my configuration input and added the printer but nothing happened when I tried a test print, so the question is, is this possible ? and if so what am I doing wrong?
I should add that I am quite new to Xubuntu, (installed three days ago) and I don't mind using the terminal if I am well guided but prefer to do things via the GUI if possible ( which should be the case with a modern OS like Xubuntu!)
Thankful for any help.

---

### Post by dstew on 2007-12-12
Yes, you should be able to do this. I am not at my Xubuntu computer right now, so I am trying to remember. One thing, you have to use the correct name for your shared printer in the CUPS setup dialog. Since it is using Samba to connect, the printer will need a name like smb://XP_computer/printer1. Of course, you will substitute your own computer server and printer names. The other thing I found troubling was that there were two HP listings for drivers. Only one works. I think one was "Hewlitt-Packard" and the other was "HP". I believe it was the "HP" list that worked.

---

### Post by chrismine on 2007-12-12
I found if you use the Windows Pc's IP adress and the shared printer name it works.

Hope it helps.

---

### Post by Mikjoba on 2007-12-12
OK! thanks "dstew" your solution worked perfectly when I used the CUPS browser based configuration tool (nice tool when you know what it's doing!), I misunderstood originally the part about "Windows printer and SAMBA" thought that this was for that breed of printers that would only work with Windows.

---

### Post by Mikjoba on 2007-12-13
An update, I may have found a little bug, tested the solution and as noted earlier all seemed to be well with the printer reacting directly, then I tested some applications:
AbiWord = ok
Gnumeric = ok
Gimp = ok (although I had to do a small configuration of something called Gutenprint).
Gedit = ok
I then tested Mousepad (v0.2.12) which started an application called Xfprint, when I tried to print, this showed the correct printer in the print to box, but when I clicked on print it locked up, nothing happened on the printer and I was unable to close the application, (had to use xkill on it!) I was also unable to close Mousepad even when the close dialogue came up, so I had to xkill this as well.
I should add that when Xfprint starts it is showing the correct printer but the rest is grayed out (paper size, portrait landscape etc.)
This is no big deal, it's just that in Windows I tend to use Notepad for quick and dirty jotting and expected mousepad to be the equivalent in Xubuntu.
Thoughts anybody?

Mike

---

