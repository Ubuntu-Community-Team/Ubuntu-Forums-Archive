---
title: "EXT serial modem + serial-to-usb cable = problems"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2007-04-15
Finally got around to tackling the modem today.  It was detected just fine and I thought another problem was licked but the dial-up program (kppp) failed on initialization.

I think the problem was with baud rate, between the cable/modem:

[img]http://www.extinctionlevelevent.com/misc/linux/modem01.png[/img]

PL2303 is the chipset for the cable.

I used the instructions from [this thread to set it higher - ](http://ubuntuforums.org/showthread.php?t=51085&highlight=modem+baud+rate)

[img]http://www.extinctionlevelevent.com/misc/linux/modem04.png[/img]

That appears to have fixed the baud rate problem but kppp is still terminating at the initialization stage.  I'm out of clues at this point.

---

### Post by Jack the R on 2007-04-15
No ideas?

---

### Post by Jack the R on 2007-04-15
Here's what I got from running tail - f /var/log/messages - 

[img]http://www.extinctionlevelevent.com/misc/linux/modem05.png[/img]

---

