---
title: "Virtual machine"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by pks_loss on 2007-11-02
I run ubuntu 6.06, and need a free VM program to run windows on my ubuntu box. Can anyone suggest a program for me to use?

---

### Post by divague on 2007-11-02
virtualbox
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by stalker145 on 2007-11-02
+1 for VirtualBox
```
sudo aptitude install virtualbox-ose
```

---

### Post by vash5556 on 2007-11-02
+ anotther 1 for VirtualBox

---

### Post by shearn89 on 2007-11-02
yep, Virtualbox. I think VMware used to be the favourite, but it lost support or something...
Anyway, +1 for VB.

---

### Post by Steve1961 on 2007-11-02
Virtualbox again here :)

---

### Post by pks_loss on 2007-11-02
You guys are awesome, thanks so much.

---

### Post by HermanAB on 2007-11-02
It depends on which version of Windows you want to run and bear in mind that you can only install ONE kind of VM system:
Windows 2003, only works on VMware
Windows XP works on VMware and VirtualBox/Qemu

'Hope that helps!

Herman

---

### Post by mdpalow on 2007-11-02
I used VMware and Windows XP runs beautifully in it.

Great tutorial found here for downloading it and installing it:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

Why haven't you upgraded to 7.10?

Good luck..

P.S. I installed VMware from the tutorial in about 10 minutes or less; pretty simple if you follow the instructions step by step...

---

### Post by pks_loss on 2007-11-02
> **mdpalow said:**
> I used VMware and Windows XP runs beautifully in it.

Great tutorial found here for downloading it and installing it:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

Why haven't you upgraded to 7.10?

Good luck..

P.S. I installed VMware from the tutorial in about 10 minutes or less; pretty simple if you follow the instructions step by step...

 oh ok, thanks... I'm thinking about upgrading to 7.10, how much better is it? is it worth it?

---

### Post by pks_loss on 2007-11-02
I'm installing VMware server right now, we'll see how everything goes eh?

---

### Post by mdpalow on 2007-11-03
I can't tell you how much better 7.10 is than other versions 'cause this is my first time using Ubuntu/Linux. However, you are at least two versions behind I would think and that's not good for driver updates and all. I tried 7.04 and it didn't allow me to use wireless on my laptop, but 7.10 worked like a champ out of the box, so just a good example of why you should upgrade. 

Sure, I see some people having problems when they upgrade - but generally speaking, upgrades are a good thing.

Haven't seen you reply in two hours about your VMware install. Hope it went OK. If you have difficulty with the install, just remember to use ALL the defaults that are shown in the brackets " [ ] " when you don't know what to put. When it shows you directories to install, just go with the defaults except for that one where it asks you where you want to put vmware. I put mine - like in the tutorial - /home/myname/vmware.

If you're having any other difficulties, just tell me what you're not getting and I'll reply with instructions.

---

### Post by pks_loss on 2007-11-03
VMware install went flawlessly... all I'm having a problem with now is the usual firefox, flash, and other plugin issue.


  Do I need to reformat to install 7.10?


  It would be really nice if linux could come with everything preinstalled, mp3, flash, java... all that business. One day I'm going to figure out how to compile my own version, and after that... I'm going to upload it to my FTP and share.

---

### Post by dyrer on 2007-11-03
I have a printer Canon i865 and scanner 4400F, will they work with Ubuntu 7.10 and Virtualbox?
I want to install Windows XP SP2
I have tested once virtualbox and the maximum memory for Graphics card is 128MB, can I use more memory for games?
How about performance

---

### Post by getmeoutofhere on 2007-11-03
Personally I wouldn't upgrade to 7.10.  Many people have had problems with it, just doesn't seem to be worth the risk.  In my opinion, if what you've got works, stick with.  I briefly tried to upgrade to 7.10 (clean install) and I went back to 7.04.  I couldn't get Virtualbox to work on 7.10, but works very well with 7.04.

---

### Post by jfluhmann on 2007-11-03
> **pks_loss said:**
> Do I need to reformat to install 7.10?

No, but I would assume you've stayed on 6.06 for the Long Term Support.  I'd say burn a copy of 7.10 and boot up to it, play around with it, and see if it's worth it to you.  You may prefer to stay at 6.06.

I'm using VMware, as well.  I've considered trying VirtualBox, but there are some steps to go through to convert my current XP VM.  I went with VMware since we use Server and ESX at work.

---

### Post by pks_loss on 2007-11-03
I did choose 6.06 for long term support.  I'm still having a few problems with my ubuntu box though.

---

### Post by wata on 2007-12-25
> **dyrer said:**
> I have a printer Canon i865 and scanner 4400F, will they work with Ubuntu 7.10 and Virtualbox?
I want to install Windows XP SP2
I have tested once virtualbox and the maximum memory for Graphics card is 128MB, can I use more memory for games?
How about performance

I have managed to get my Canon 4400F scanner working under Ubuntu 7.10 and Virtualbox 1.4 (I could not get it to work with 1.5.0 or 1.5.2).  You can get the older Virtualbox install from here [_Virtualbox Old Builds_]("http://www.virtualbox.org/wiki/Download_Old_Builds").  Don't forget to edit /etc/init.d/mountdevsubfs.sh (uncomment the USB lines) and enable USB support in the Virtualbox.

I can't comment on the performance for gaming, but the few applications I have used there is a noticeable performance hit (to be expected in a virtual machine).

Has anyone managed to get the 4400F working under 1.5.x Virtualbox?  Or even better under wine?  Or still better has anyone cobbled together native support for this scanner?

---

