---
title: "Lost XP in dual boot"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by xyeovillian on 2006-08-30
I have just installed Ubuntu 6.06 on start up I have the 4 options beginning with Ubuntu which loads OK then the last option Windows XP after the XP logo I get the blue screen 
Stop: cOOOO2a (Fatal system error)
The session Manager initialization system process terminated unexpectedly with
The system has been shut down.

I think that I put the wrong option as my WinXP shows on the ubuntu desktop.hda 1 Windows is there anyway that I can get it to dual boot?

I can't get my pci ADSL modem configured either if I could would be quite happy to just use ubuntu.

Finnaly is there anyway around having to log in with username & password as its only me using the PC.

---

### Post by mejy on 2006-08-30
> **xyeovillian said:**
> I have just installed Ubuntu 6.06 on start up I have the 4 options beginning with Ubuntu which loads OK then the last option Windows XP after the XP logo I get the blue screen 
Stop: cOOOO2a (Fatal system error)
The session Manager initialization system process terminated unexpectedly with
The system has been shut down.

I think that I put the wrong option as my WinXP shows on the ubuntu desktop.hda 1 Windows is there anyway that I can get it to dual boot?

I can't get my pci ADSL modem configured either if I could would be quite happy to just use ubuntu.

Finnaly is there anyway around having to log in with username & password as its only me using the PC.

First, can you copy and paste to here the file you get from

```
gedit /boot/grub/menu.lst
```

I'm not to sure why you would be getting errors only when you reached XP, since all does grub is pass things through to the Windows boot loader which runs before the boot splash (with the flag and running dots...).  If it got past the windows boot loader, I'd expect everything to be fine.

As for your pci ADSL modem, what is the name and company that made it?

To log in without typing your username and password, go to system->administration->login window, select the Security tab at the top, check Enable Automatic Loign and select the user name from the drop down list below.

---

### Post by mejy on 2006-08-30
Although the timing may seem suspicious, according to the following two sources it seems to be nothing to do with the installation of Ubuntu:

[http://reviews.cnet.com/5208-6142-0.html?forumID=5&threadID=56210&messageID=669518](http://reviews.cnet.com/5208-6142-0.html?forumID=5&threadID=56210&messageID=669518)
[http://www.experts-exchange.com/Operating_Systems/WinXP/Q_20790028.html](http://www.experts-exchange.com/Operating_Systems/WinXP/Q_20790028.html)

---

### Post by TFX360 on 2006-08-30
Better to open a terminal and do


```
sudo nano /boot/grub/menu.lst
```


Copy and paste the info here.


If gedit works there is something wrong because a normal user shouldn't have access to this file. Or am I wrong?

---

### Post by TFX360 on 2006-08-30
> **mejy said:**
> Although the timing may seem suspicious, according to the following two sources it seems to be nothing to do with the installation of Ubuntu:

[http://reviews.cnet.com/5208-6142-0.html?forumID=5&threadID=56210&messageID=669518](http://reviews.cnet.com/5208-6142-0.html?forumID=5&threadID=56210&messageID=669518)
[http://www.experts-exchange.com/Operating_Systems/WinXP/Q_20790028.html](http://www.experts-exchange.com/Operating_Systems/WinXP/Q_20790028.html)

Interesting....

---

### Post by FuriousLettuce on 2006-08-30
EDIT: According to the above sources, the following is unlikely to have any effect on your windows installation.

To get windows to work, try the following: 

```
cd /boot/grub
sudo cp menu.lst menu.lst.bak && nano menu.lst
```

Find the section about the Windows option, and add this at the bottom of the section:

```
chainloader +1
```

Next, press CTRL+x to exit, press 'y' to save it and then press enter. Next, reboot, and see if it works. If it doesn't, or there is a problem, boot into linux and do:

```
cd /boot/grub
sudo mv menu.lst.bak menu.lst
```

to restore your original config file.

---

### Post by xyeovillian on 2006-08-30
Thanks guys my modem is = [http://www.dse.co.nz/cgi-bin/dse.storefront/44f56cb7026a5a8c273fc0a87f990748/Product/View/XH1137](http://www.dse.co.nz/cgi-bin/dse.storefront/44f56cb7026a5a8c273fc0a87f990748/Product/View/XH1137)

As regards entering codes how do I do that ?  I should have got a white stick with this linux.  Please explain as I would like to get   this sorted thanks for your patience.  will have a try tomorrow as its 10.50pm here and I'm off to bed!

---

### Post by xyeovillian on 2006-08-31
I have reloaded XP and its a lot quicker now, the only problem now is I can't install ubuntu it goes as far as the language setup then freezes, and I have abort the installation. Is it anything to do with the bios?

---

### Post by TFX360 on 2006-08-31
> **xyeovillian said:**
> I have reloaded XP and its a lot quicker now, the only problem now is I can't install ubuntu it goes as far as the language setup then freezes, and I have abort the installation. Is it anything to do with the bios?

Have you tried the Safe Graphics mode at startup!?

---

### Post by xyeovillian on 2006-08-31
TFX I have tried in safe graphic and it just freezes on a black screen, seems funny as it loaded OK before reformatting XP

---

### Post by xyeovillian on 2006-09-01
It doesn't seem to recognize my cdrom drive I downloaded the windows downloader tried that and it came up a message couldn't recognize my cdrom drive  1

---

### Post by xyeovillian on 2006-09-02
bump

---

### Post by TFX360 on 2006-09-02
I see that you have a problem with a cdrom drive, but I can't find the context why. What are you doing and when isn't it working?

---

### Post by xyeovillian on 2006-09-02
TFX Thanks for the reply I get as far as the install it gets to languages then just freezes mouse will move spasmodically, sorry to confuse but I think the CDrom is working OK as I have loaded programs from cd to windows XP.  Yes just had another look the CD is purring away stuck on languages been trying to load for 30 minutes so far

---

