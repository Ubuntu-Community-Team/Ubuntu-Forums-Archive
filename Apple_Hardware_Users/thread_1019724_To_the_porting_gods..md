---
title: "To the porting gods."
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by pgflmac on 2008-12-23
I have a request to the PowerPC porting gods. Please include the xorg.conf from 6.06 on the next ubuntu distribution.  Or if this is generated during installation please put the generator into the next ubuntu release. I had a mess trying to get the resolution to set properly on my iBook G3. Eventually, I installed 6.06, emailed it to me in an attachment, installed 8.04, through trail and error got evolution to work (set up assistant had problems displaying correctly), then finally got email to work, saved attachment, sudo cp xorg.conf /etc/X11/xorg.conf! Phew!

---

### Post by ajgreeny on 2008-12-23
The xorg.conf file is one of the few system files that I have always backed up since I learned enough about ubuntu to realise that graphics problems are a major problem to many people.  It wasn't until intrepid that I had to copy parts of that file into my current xorg.conf to get things working properly, for resolution.  There should at least be some way of getting the system to generate a useful configuration, instead of simply saying, for example:-
> Section "Device"
    Identifier    "Configured Video Device"
EndSectionwhich, let's face it is worthless if it happens to be configured incorrectly.  Progress seems to have been backwards with this as far as I can make out, and I have seen nothing that gives a certain and foolproof way of generating a configuration file if the auto produced one doesn't work.

---

### Post by stream303 on 2008-12-23
I have to say I was very surprised when I saw a full xorg.conf coming from a recent openSUSE 11.1 install on my G5, even with Xorg 7.3.  Looks like the "zero line" xorg.conf isn't mandatory at all.

I wish Canonical would restore it, but I think that a zero-conf xorg.conf is a selling point.

---

