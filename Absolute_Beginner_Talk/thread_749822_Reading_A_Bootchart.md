---
title: "Reading A Bootchart"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2008-04-08
The computer in question is a IBM R40, is there anything I can do to streamline my boot sequence?  

Also,  in leu of a splash screen I have the computer flood my screen with the start-up routine/loading sequence.   Is there any way to dump that to a text file,  I see several read [FAIL] go by but too quick to read.



[IMG]http://i306.photobucket.com/albums/nn261/plecostomus_tank/gutsy-20080408-5.png[/IMG]

---

### Post by Soundman2 on 2008-04-08
Much of what you want can be found in /var/log/dmesg  after booting.  This file contains timestamped messages that were generated during the most recent boot.  The record of the last several boots are stored in files matching /var/log/dmesg*

Hope this Helps,
Soundman2

---

### Post by Epic Plecostomus on 2008-04-08
Sure does.     


Still not sure what the data in Bootchart means though, can anyone point me to a resource?

---

### Post by Soundman2 on 2008-04-08
This website describes it pretty well:  [http://www.bootchart.org/index.html](http://www.bootchart.org/index.html)

---

### Post by ctyc on 2008-04-09
have you turned off and uninstalled the services you do not need, just to start the ball rolling  :)

---

### Post by Epic Plecostomus on 2008-04-09
in order to do that I need to know what is what on this chart.... so lets start there.   What processes do what?   Can I get a breakdown of what I'm loading?

---

