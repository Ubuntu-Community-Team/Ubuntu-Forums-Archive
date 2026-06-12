---
title: "Installing Mailwasher PRO with Wine?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2007-06-09
I am using Ubuntu 6.0.6 with the latest verion of Wine.
I want to install Mailwasher PRO from my Windows partition.
It has to be the Windows version as I already have a license key which will not work in the Linux version.

I can run the .exe in Ubuntu but I cannot get it to install.
All the commands that I have tried come up with 'file not found'.

There are two copies of Mailwasher PRO on my Windows partition, one installed, one not.

There are a couple of other programs that I would like to install from Windows but have the same problem.

Any help would be appreciated.

---

### Post by bodhi.zazen on 2007-06-09
Wine is not always so easy to use.

Search for how-to's on the wine site, like this :

[http://appdb.winehq.org/appview.php?iAppId=1095](http://appdb.winehq.org/appview.php?iAppId=1095)

Also see here :

[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

It may be easier to dual boot or use something like VMWare or VirtualBox

---

### Post by pilgrim-online on 2007-06-09
Hi B.Z,

Thanks for the reply and the links but most of it is over my head.

---

### Post by kyphi on 2007-07-16
I run Mailwasher Pro 5.3 in Ubuntu with CrossOver Linux without any problems whatsoever.  It just did not work in WINE, which is odd since both Wine and CrossOver Linux come from the same address.

---

### Post by expatCM on 2007-07-16
I use Mailwasher 5.2 (Windows version) without any problem at all.

To install I copied the .exe to the Desktop and then right clicked the file and selected "Run With" and entered Wine.  It then ran the Windows installer ........

---

### Post by kyphi on 2007-07-16
> There are a couple of other programs that I would like to install from Windows but have the same problem.

Try CrossOver Linux.

WINE and CrossOver Linux are at the same address.

---

### Post by pilgrim-online on 2007-07-16
**kyphi**,

Never heard of CrossOver Linux, when I get the time I'll have a look. Thanks.

**expatCM**,

I tried that, it opened Mailwasher but never installed it.

---

### Post by expatCM on 2007-07-16
sorry ... I am not quite clear .... You said 
> I tried that, it opened Mailwasher but never installed it.

I was wondering how you know it was never installed? Did you reboot after installing (since Wine sometimes does not immediately show newly installed programs in the Applications / Wine / Programs menu).  If you saw the program window was open on your system then I suspect it is installed.  

If you type 
```
whereis mailwasher.exe
```
at the command prompt, what happens?

---

### Post by pilgrim-online on 2007-07-16
Hi,

I concluded that it never installed because after rebooting the only trace of it I could find was the .exe on the Desktop.
I never tried the command prompt you mentioned because my understanding of Linux does not go that far.
If you are right and it did install then I will try the code next time I boot into Ubuntu and let you know.

---

