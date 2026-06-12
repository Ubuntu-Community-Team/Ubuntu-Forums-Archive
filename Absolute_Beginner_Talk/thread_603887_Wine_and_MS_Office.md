---
title: "Wine and MS Office"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-11-05
Hi, a couple of questions on wine and whether it's right for me.

I use MS Office at work. I'ld like to be able to access and modify the work files remotely from home on Ubuntu. I believe wine will let me use MS office programs, but does it save changes as NTFS or in the linux format? For example if I access a Word file on the server at work from my PC running Ubuntu can I save changes in NTFS on the server?

Also, what's the story with licences/legality? I can't imagine MS doing things out of the goodness of their hearts.

---

### Post by carlosjuero on 2007-11-05
> **Padraig1 said:**
> Hi, a couple of questions on wine and whether it's right for me.

I use MS Office at work. I'ld like to be able to access and modify the work files remotely from home on Ubuntu. I believe wine will let me use MS office programs, but does it save changes as NTFS or in the linux format? For example if I access a Word file on the server at work from my PC running Ubuntu can I save changes in NTFS on the server?

Also, what's the story with licences/legality? I can't imagine MS doing things out of the goodness of their hearts.
Well, I think you have file formats confused with disk formats - 2 different kettles of fish :)

Ubuntu can read and write NTFS file systems, and you can read and write Office files to any supported file system.

Depending on the version of office, you can run it in WINE (as long as you have a valid license, MS can't really say anything).. you can also use OpenOffice if you wish - OpenOffice supports MS Office formats (even Office 2005 .docx formats).

---

### Post by Padraig1 on 2007-11-05
Thanks for the reply.

I didn't realise Ubuntu could write NTFS files. 
And I also didn't realise that open office supports MS office formats. 

So now, from what I can see I don't need Wine and should have no problem writing to the work server.

Thanks for your help.

---

### Post by Randomwkh on 2007-11-05
thought i may aswell post in here instead of a new topic-
open office can save as word + excel formats but can it save as Access format... 

argh why dont schools use linux xD.

---

### Post by carlosjuero on 2007-11-05
> **Randomwkh said:**
> thought i may aswell post in here instead of a new topic-
open office can save as word + excel formats but can it save as Access format... 

argh why dont schools use linux xD.
Access is problematical I think :/ - I don't think that OpenOffice's DB program can use Access Database Files. If you have access to a copy of MS Access you can install it through WINE, hmm... I feel a google coming up :)

---

### Post by LinuxGuy1234 on 2007-11-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Randomwkh said:**
> thought i may aswell post in here instead of a new topic-
open office can save as word + excel formats but can it save as Access format... 

argh why dont schools use linux xD.

I think it can :)

BTW, schools use Windoze because M$ products are popular... I prefer open source. I use Ubuntu Dapper myself. It's also bad. I am giving a link to the bug that mean that many PCs must have Ubuntu.

---

### Post by LowSky on 2007-11-05
open MS access in OOo base

supposedly you can?

heres what google turned up
[http://www.google.com/search?hl=en&q=MS+access+and+Openoffice](http://www.google.com/search?hl=en&q=MS+access+and+Openoffice)

---

### Post by carlosjuero on 2007-11-05
> **LowSky said:**
> open MS access in OOo base

supposedly you can?

heres what google turned up
[http://www.google.com/search?hl=en&q=MS+access+and+Openoffice](http://www.google.com/search?hl=en&q=MS+access+and+Openoffice)
Ah ok, yep that will work. My google searches were using the wrong keywords (google-fu is bad today)

---

