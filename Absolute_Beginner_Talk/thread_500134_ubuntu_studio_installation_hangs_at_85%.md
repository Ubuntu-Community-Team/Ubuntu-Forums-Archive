---
title: "ubuntu studio installation hangs at 85%"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by sharathg786 on 2007-07-13
I have burned the ubuntu studio 7.04 (fiesty fawn) on a DVD, I have checked the "check cd for defects" and it showed none.... even though when i do a normal install, it hangs at 85% during which it is installing the package "brltty-x11" Plz help, what could be the problem??

---

### Post by hackle577 on 2007-07-13
How long does it hang for? Sometimes it can take a while.

Also, did you do an MD5 sum check on the ISO file before you burned it?

---

### Post by sharathg786 on 2007-07-13
I have done the md5sum and it matched correctly, I have waited for about 20 min, the cpu light does not glow nor the light on my DVD rom

---

### Post by Rocket2DMn on 2007-07-13
A lot of install/cd problems are fixed by burning the disc at a slow speed, like 4x, and using quality media (not the super-cheap stuff).  Have you tried this?

---

### Post by robertc36 on 2007-07-13
I run ubuntu studio and the install can take up to an hour.
I do not remember it hanging at 85% though.
I have however had too burn several dvds as sometimes they just do not work.
Due too inexperience have had to install several times you see.
So i currently have 3 .
yes all burned at 4x speed etc .
Just they throw up errors .
Quick wipe and then they work ????
Frustrating as hell.

---

### Post by sharathg786 on 2007-07-13
Well burning again at slow speed might not help me, coz i burned using k3b & the speed was set to "auto", it burnt at approx 1x :lolflag: (some problem with my k3b, eventhough my drive supports upto 16x) ... and the DVD i used was of decent quality....anyway..... guess i will try again waiting some more time during installation.

---

### Post by plengnom on 2007-07-16
We encountered the same problem and it persisted even though we burned new installation CD's. When connecting the box to internet and using a valid nameserver entry, the installation continued. The log showed that when (or after) the install of the brltty-x11 package, apt tries to fetch some packages from the net. When no network is found, it hangs.

Egil A. M / Kim K.

---

### Post by McTaggart on 2007-07-20
I have this happen every time I try to install. The trick is just to wait. It gets to 85% and brltty-x11, then the text changes to "Please wait..." and both the dvd drive and the hard drive seem to stop. Then I got distracted for maybe twenty minutes and it got going again.

Then it hung again at 90% and despite leaving it for nearly an hour it didn't start up again. I got through the install once, only installing the audio part. I had a different (95% sure unrelated) issue later on so I tried a re-install.

[edit]This time I timed it, doing a text install and not including any of the audio/graphics/video/plugins. It idled for about 16 miinutes at 85% and for 38 minutes at 90%. Both times it idled I'm fairly sure the dvd and hdd stopped spinning. This was on a toshiba p100 laptop with 2gb ram and 2.0ghz core 2 duo. I think the solution is a cup of coffee and a good book unfortunately.

---

### Post by scapalexis888 on 2007-07-20
I have the same exact problem, but....

If you automatically configured DHCP during the installation, you have to be continuously connected to the net for brltty-x11 to install. When I installed Feisty, I left my DSL modem on, and when it got to 85%, an internet transfer was started and I was able to completely install Feisty after it finished transfering.

Final word is to STAY CONNECTED TO THE NET!

Hope this helps!

---

### Post by zanget on 2007-09-25
Ctr+Alt+F2
killall apt-get
Ctr+Alt+F1

---

### Post by por100pre1 on 2007-09-25
> **zanget said:**
> Ctr+Alt+F2
killall apt-get
Ctr+Alt+F1

Thank you for the suggestion but it seems kind of late.

Welcome to the Forums! :)

---

