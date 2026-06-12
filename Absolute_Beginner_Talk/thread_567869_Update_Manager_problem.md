---
title: "Update Manager problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-05
I downloaded Compiz yesterday and after I had installed it, I was notified of existing software updates, one of which was compiz-core.  I installed everything and rebooted but was still left with one update, compiz-core, to be installed.  I've tried installing and rebooting a number of times but is still won't install.  Under the file in Update Manager, it actually tells me that I'm updating from one version to the exact same version.  If I go into Synaptic and look for this file, it tells me that I already have the newest version, so why won't it disappear from my Update Manager?

---

### Post by nowshining on 2007-10-05
what's the output of applications - terminal

sudo apt-get install -f


it will ask for YOUR password =- don't worry while typing in the password and it not showing, this is normal, just type it out as you usually do and then hit the enter key.

---

### Post by BOZG on 2007-10-05
```
stephen@stephen-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfame-0.9 libdvdcss2 libpvm3 transcode
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

And I'm not that bad that I don't know what to do when it asks for a password! :)

---

### Post by nowshining on 2007-10-05
lolz ur in the ABSOLUTE BEGINNER thread which is why i input that info. :) just in case. I'm starting to make it a habit now.

do that again and when it asks for a y/n input y and hit enter.

open up update manager  again - there will be no need to go back and do an update it will or should show up if it's still a problem if not it will not show up, was it ever greyed out by the way, u can't click on anything greyed out.

---

### Post by nowshining on 2007-10-05
then do an 

sudo apt-get autoremove

and let it remove those.

---

### Post by BOZG on 2007-10-05
It doesn't give me an option for y/n?

---

### Post by BOZG on 2007-10-05
And no, it's never been greyed out.  You can select or unselect it still but it just doesn't go away.  It will actually install but still stays in the list.

---

### Post by nowshining on 2007-10-05
oh by the way you prob. can't connect to to the update site right now it seems to be out, :) browser + update manager won't update - neither will synaptic, however I was one of the last at the tme to get A LIST of updates after that it won't download from [http://archive.ubuntu.com](http://archive.ubuntu.com) or connect to that url...

okay you did the autoremove right do the install -f command now and see what it gives, i forgot auto remove will AUTO it. :P

---

### Post by nowshining on 2007-10-05
wow now seems to back up.. :)

---

### Post by nowshining on 2007-10-05
shucks seems to be actually slow not out or out now it won't work again.. :P

---

### Post by BOZG on 2007-10-05
Alright, I'll leave it a while and I'll check back later.

---

### Post by nowshining on 2007-10-05
my next suggestion was to do the following, remove it in synaptic package manager and then re-install :) and see if that helps...

---

### Post by BOZG on 2007-10-05
I did that already.  Exact same result.

---

### Post by nowshining on 2007-10-05
have u done a reboot after the updates, if not do so (highly suggested after doing updates - :) ) as after reboots are when problems can and will occur and then re-check. after a reboot.

---

### Post by BOZG on 2007-10-05
I always do. :)

---

### Post by g2g591 on 2007-10-05
actually compiz core always needing an update is a known bug, its a problem in that repository, I can't remember where I heard this, but i remember reading that a few times. Its fixed in gutsy anyway (because compiz is in normal repositorys)

---

### Post by nowshining on 2007-10-05
> **BOZG said:**
> I always do. :)

lolz. ;)

---

### Post by BOZG on 2007-10-05
> **g2g591 said:**
> actually compiz core always needing an update is a known bug, its a problem in that repository, I can't remember where I heard this, but i remember reading that a few times. Its fixed in gutsy anyway (because compiz is in normal repositorys)

Cool, thanks.


Is there anyway to disable notifications for that update without just disabling notifications completely?

---

### Post by nowshining on 2007-10-07
yes go into synaptic package manager and then find the offending application, have it selected and go at top to packages and lock version, sorry this is the only way i know and the side-effect is that it will lock that version from updating to another version until u go back in and unlock it.

---

