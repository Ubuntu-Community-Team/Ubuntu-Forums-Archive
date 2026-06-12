---
title: "OkiPage 14ex on Windows XP Share, of course it doesn't work..."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by sYs^ on 2006-04-17
Hi,

I've got an OkiPage 14ex printer shared on a Windows XP Prof. SP2, I followed this howto: [https://wiki.ubuntu.com/WindowsXPPrinter](https://wiki.ubuntu.com/WindowsXPPrinter) and added "successfully" the printer. After that everything seemed to be O.K.:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=8419&stc=1&d=1145275135[/IMG]

But after that, if I want to print something, nothing happens, it writes: **Pending: printer-stopped** and nothing more.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=8420&stc=1&d=1145275227[/IMG]

Any ideas?
Thank you in anticipation!

---

### Post by sYs^ on 2006-04-18
Anybody?

---

### Post by jethro10 on 2006-04-18
It may not be much help but I now get this** Pending: printer-stopped** with a HP printer.
When I installed it and used Samba to connect it worked fine, one day it packed in and I re-installed.
I'm sure HP released some printer driver stuff for linux and it does not seem to install properly now.
My point is that I believe my problem is an incorrect driver -Mine definatley failed with this CUPS driver thing 
Also Is the OKI a windows only GDI printer? if so will this not be problematic? Dont these offload some processing to the windows PC - if so will the Linux driver replace these windows parts.

No solutions only more questions.
J

---

### Post by sYs^ on 2006-04-18
Well, it worked already on Linux too, but it was pathetically slow and in the last days it didn't print anything, so that's why I decided to plug it to a Windows machine, at least it prints there normaly. 
But unfortunately I don't know well printers, moreover I hate them. :p
So, I don't know if my printer is a Windows only GDI printer.

Thanks for your answer at least somebody wrote something .:D

---

### Post by jethro10 on 2006-04-18
Yes, i'm totally lost why an otherwise good install stopped working.
I'm on Dapper as well and thought it might be the upgrades.
Hoping the full release may fix it.

Jeff

---

### Post by sYs^ on 2006-04-18
I hope too, perhaps we should file this bug or check if it's already reported.

---

### Post by sYs^ on 2006-05-27
Yesterday I reinstalled my whole Dapper to the new RC-1 and it's working now :p

---

