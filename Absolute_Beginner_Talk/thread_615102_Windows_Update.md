---
title: "Windows Update"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Chris Riley on 2007-11-16
Hi, Excuse me asking questions about MS Windows in this forum, but the problem seems to be related to my Gutsy 64 bit installation.

I am running an AMD64 with 2 hard disks. One has my Windows environment installed on it, formatted NTFS, the other is my Ubuntu drive, formatted accordingly. I have the Windows disk with 2 partitions, so effectively have 3 drives, C, D, and E.

When I run Windows Update (for XP Pro), the installations fail, with the message that there is an error on the E drive. I can only presume that Windows Update wants to see all my drives as NTFS (or FAT).

Does anybody know of a way to make Windows Update ignore my E Drive?

Answers on a postcard, please. . . .

Help would be much appreciated, I'm getting frustrated. Thanks.

---

### Post by arkara on 2007-11-16
can you give us your exact partition table??

---

### Post by Chris Riley on 2007-11-16
Yeah, C drive is 30G NTFS, D drive is 220GB NTFS, E drive is 160GB Linux Ext 3

---

### Post by oilchangeguy on 2007-11-16
> **Chris Riley said:**
> Hi, Excuse me asking questions about MS Windows in this forum, but the problem seems to be related to my Gutsy 64 bit installation.

I am running an AMD64 with 2 hard disks. One has my Windows environment installed on it, formatted NTFS, the other is my Ubuntu drive, formatted accordingly. I have the Windows disk with 2 partitions, so effectively have 3 drives, C, D, and E.

When I run Windows Update (for XP Pro), the installations fail, with the message that there is an error on the E drive. I can only presume that Windows Update wants to see all my drives as NTFS (or FAT).

Does anybody know of a way to make Windows Update ignore my E Drive?

Answers on a postcard, please. . . .

Help would be much appreciated, I'm getting frustrated. Thanks.

you're gonna need to provide the error message word for word. windows does not care about your other partitions. as long as it's happy with the windows partition, that's all that matters.

---

### Post by Chris Riley on 2007-11-17
I may be misleading you here, it is actually updates for Microsoft Office that are failing.

The message that Microsoft Update returns is:

Error 1327. Invalid Drive: E:\

I wonder whether MS is trying to put the installation files onto the E Drive?

---

### Post by por100pre1 on 2007-11-17
Please read [this]("http://blogs.geekdojo.net/andy/archive/2004/01/19/665.aspx"). Do yourself a favor, install [OpenOffice.org]("http://download.openoffice.org/2.3.0/index.html"); even if you don't set it as your default document handler it can be useful someday. :)

---

### Post by Chris Riley on 2007-11-18
Thanks for all the responses; I've cured the problem. It seems that when MS Office installs itself, it puts a recovery copy in a location chosen by the installer. I chose the E drive as I only had Windows installed then. Every time an update is performed, the installer looks at this recovery file as a reference.

I had to reconfigure the installer.

By the way, I already have OpenOffice installed. The only reason I still use MS Office is because Lexmark refuse to provide drivers for my printer.

Chris

---

### Post by ronmarley1 on 2007-11-18
> **Chris Riley said:**
> 
By the way, I already have OpenOffice installed. The only reason I still use MS Office is because Lexmark refuse to provide drivers for my printer.

Chris

I'm sure you've probably tried in vain to install your printer, but have you looked at [http://www.linux-foundation.org/en/OpenPrinting?](http://www.linux-foundation.org/en/OpenPrinting?)  There's quite a list of Lexmark printers listed.
Sorry if you have tried this route.

---

