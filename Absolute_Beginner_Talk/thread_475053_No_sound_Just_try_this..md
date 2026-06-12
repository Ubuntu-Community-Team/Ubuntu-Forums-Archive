---
title: "No sound? Just try this."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-06-15
```
sudo apt-get update && sudo aptitude dist-upgrade
```


This worked for me, maybe it'll work for you!

---

### Post by ronbrooks on 2007-06-15
I tried it but it didn't help.  I can't even get my sound card on board to be seen. I keep tring things on the threads but nothing is working.

---

### Post by byen on 2007-06-15
The above mentioned command is used to update your sources and upgrade your software. May be in your case, the update fixed a bug or a package that was effecting your sound card.

PS. Can you tell us the make/model of your sound card? may be someone who has a similar card may find relief.

---

### Post by ccfjeff on 2007-06-15
There's also a section in the Ubuntu documentation in debugging sound problems:
[URL="https://help.ubuntu.com/community/DebuggingSoundProblems"]
https://help.ubuntu.com/community/DebuggingSoundProblems[/URL]

also a Wiki with a troubleshooting guide for Audio (scroll down a little):

[http://ubuntu.sun.ac.za/wiki/index.php/Hardware#Audio](http://ubuntu.sun.ac.za/wiki/index.php/Hardware#Audio)

---

### Post by ronbrooks on 2007-06-15
My sound card is VIA VT8237 This card is an on board card and the system can not find it.  I get a red X over the volume control. I have reinstalled alas and down loaded the Gstreamer plugins.  and the system still can't find the card.  It was working a few weeks ago. before the Kernnel change.

---

### Post by ccfjeff on 2007-06-15
> **ronbrooks said:**
> My sound card is VIA VT8237 This card is an on board card and the system can not find it.  I get a red X over the volume control. I have reinstalled alas and down loaded the Gstreamer plugins.  and the system still can't find the card.  It was working a few weeks ago. before the Kernnel change.


Alsa has a [sound card matrix]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main") .  The closest match under [Via]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main") seems to be the VT8237A.  That has a [details]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-hda-intel") page that might be of some help.

BTW, Alsa did have an update June 11.  Don't know if that was incorporated into the Ubunu distro yet. 

Here is Alsa's [Changelog between 1.0.14 and 1.0.14a releases]("http://www.alsa-project.org/changes/v1-0-14--v1-0-14a.txt")

---

### Post by systemintheglitch on 2007-06-21
I DONT GET IT!! Now it DOESN'T work again!!
:(

I will try running that update command to see if it works.

---

