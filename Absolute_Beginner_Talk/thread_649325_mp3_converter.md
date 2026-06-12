---
title: "mp3 converter"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by sinisterman on 2007-12-24
Hey everyone. I am looking for something to comvert mp3s to something else. I have some songs I want to write to cd but k3b wont do mp3. thanks

---

### Post by Zimmer on 2007-12-24
Audacity, but you may also need  the LAME codec for handling mp3 to wav conversion.

liblame0 in the repositories.

Open the mp3 with Audacity then export to wav.

---

### Post by ayenack on 2007-12-24
Type sound converter into add remove.

---

### Post by sinisterman on 2007-12-24
I dont think sound converter handles mp3

---

### Post by sinisterman on 2007-12-24
I would also like something that can do batch conversion

---

### Post by ayenack on 2007-12-24
Yes sound converter will do mp3 and loads of others it also does batch conversions.

---

### Post by sinisterman on 2007-12-24
I tried looking in add remove but I got nothing

---

### Post by ayenack on 2007-12-24
If you look up in the top right corner of add/remove you'll see a tab that has show written next to it click it and select all available applications. If that doesn't work post back and we'll edit your apt list so you can download it..

---

### Post by sinisterman on 2007-12-24
The only thing I see in the top right corner is unsupported and proprietary software. I am on Kubuntu by the way

---

### Post by ayenack on 2007-12-24
Ok. I'm not sure if this will work on Kubuntu but you can give it a try.

Open a terminal and type this.
**sudo nano /etc/apt/sources.list** (this will open your sources.list in terminal)

Then go down the list and uncomment "#" all instances of deb. The file will look something like this if Kubuntu is anything like Ubuntu, except there'll be a lot more.

[B]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
[/B]

once you've done that type this.

**sudo apt-get update**

And try again.
BTW. To save the file in nano press "ctrl+o" on keyboad. To exit nano press "ctrl+x".

---

### Post by sinisterman on 2007-12-24
I used the synaptic package manager to find it thanks for the help

---

### Post by ayenack on 2007-12-24
:lolflag:

Cool. Strange though thought it'd show up in add/remove, does on Ubuntu.

Well I'm off to bed. Christmas tomorrow. :)

---

### Post by Achetar on 2007-12-24
```
foobar@foobarscomputer-$ sudo apt-get install sound-converter
foobar@foobarscomputer-$ sound-converter

```Can convert MP3 to OGG and others.

---

### Post by sinisterman on 2007-12-24
Sound Konverter dosent work. It will decode but when it comes to encoding it will stop. Is there some sort of plugin that will allow k3b to handle mp3 or another burner that will

---

### Post by some_guy on 2007-12-25
I would install libk3b2-mp3.  That should allow you to burn mp3s to an audio CD.

---

