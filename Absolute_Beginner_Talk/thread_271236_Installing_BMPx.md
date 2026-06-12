---
title: "Installing BMPx"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by englishmen on 2006-10-04
For 3 days now i have had my PC duel booting with XpPro and ubuntu and while the list of apps in Synaptic package manager is HUGE. I have found that a few apps i wish to have installed are out of date compared to the official sites latest stable release.

I finally figured the easiest way to install apps it so add them to the Synaptic package manager channel list, i added automatix which in turn allowed me to install a few apps i wanted as well as install the latest release of Azureus.

The problem i found is that all tho i have read numerous guides and tried to follow them to the best of my ability. I still cant manually install apps i have downloaded. The app currently in question is BMPx 0.32.0, can someone please explain to me how i install it?

I currently have bmpx-0.32.0.tar.gz on my desktop.

Thanks.

---

### Post by armiductor on 2006-10-05
EDIT: The solution can be found here:
[http://www.ubuntuforums.org/showthread.php?p=1585060#post1585060](http://www.ubuntuforums.org/showthread.php?p=1585060#post1585060)

Hi,

I tried to install 0.32 by compiling it myself. Unfortunately I wasn't able to complete ./configure because of the following error:
> checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
If someone could tell what I should do to be able to compile bmpx manually, then I could share my findings.

Greetings,

ArmiDuctor

---

### Post by Lord Illidan on 2006-10-05
> **armiductor said:**
> Hi,

I tried to install 0.32 by compiling it myself. Unfortunately I wasn't able to complete ./configure because of the following error:

If someone could tell what I should do to be able to compile bmpx manually, then I could share my findings.

Greetings,

ArmiDuctor

You need a hell of a lot of dependencies..it won't be a nice ride.

Start with sudo apt-get install build-essential. Post anyother errors you meet this time.

---

### Post by armiductor on 2006-10-05
I figured I needed to install additional software for compiling :D Thnx for that. I won't however try compiling bmpx anymore because I found a similar thread here: [http://www.ubuntuforums.org/showthread.php?p=1585060#post1585060](http://www.ubuntuforums.org/showthread.php?p=1585060#post1585060)
So why invent the wheel twice ;)

Greetings, Armi :D

---

