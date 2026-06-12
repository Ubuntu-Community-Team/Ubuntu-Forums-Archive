---
title: "Writing a script for application to launch on plug-in?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by sid351 on 2007-12-30
Hi,

I was wondering if it's possible to have a script act on plug in of a device.

I've got my iPod working, but I've got a separate partition I use to store files I want on my iPod, and it'd be nice to automate the procedure of backing them up.

Does anyone know if this is possible?

I assume it is, as Rhythmbox opens automatically when you connect an iPod, and you can write scripts for boot, so...anyone know how to go about it?

---

### Post by bodhi.zazen on 2007-12-30
The easiest way is to add any commands you want to run at boot to /etc/rc.local

Alternately you can write a script, make it executable, and run the script from /etc/rc.local

NOTE: rc.local is run as root

---

### Post by markp1989 on 2007-12-30
you could put the script called autorun.sh on the ipod, and change the settings in removable drives.

---

### Post by bodhi.zazen on 2007-12-30
Ooops, I mis-read the OP (I thought the question was on boot).

Yes, markp1989's solution is much better.

---

### Post by sid351 on 2007-12-31
> **markp1989 said:**
> you could put the script called autorun.sh on the ipod, and change the settings in removable drives.

Do I find this script somewhere, or do I write it myself?

---

### Post by blueridgedog on 2007-12-31
Yes, you would need to write it, as only you know what you want it to do.  It would be a fun learning experience.

Also, as an alternative, you could change the action in System -> Preferences -> Removable Drives and Media -> Multimedia Tab -> Portable Music Players.

Currently it calls you music application, you could have it call a script that copies your files, then call your music application on exit, but again you would need to create such a script.

There are plenty of people here to help you.

---

### Post by sid351 on 2008-01-01
So where is a good place to start learning?

---

### Post by blueridgedog on 2008-01-01
These helped me:

[http://www.oreilly.com/catalog/bash3/](http://www.oreilly.com/catalog/bash3/)

[http://www.oreilly.com/catalog/shellsrptg/](http://www.oreilly.com/catalog/shellsrptg/)

There are a thousand or so people here that would be glad to proof/comment/suggest as you developed your scripts.

---

