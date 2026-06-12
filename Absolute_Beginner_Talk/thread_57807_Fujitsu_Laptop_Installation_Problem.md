---
title: "Fujitsu Laptop Installation Problem"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by Elim on 2005-08-17
Hello.  I have installed Ubuntu 5.04 on my desktop with no problems, and love it, and I am now trying to put it on the laptop that I am taking to university.  The laptop is a Fujitsu Lifebook N3510.  I made it maybe five seconds into the installation before hitting a brick wall.  The screen reads:

hub 4-0:1.0 connect-debounce failed, port 1 disabled
hub 4-0:1.0 over-current change on port 2

So it then cycles through ports 1 to 6 and then starts over again with port 6.  Like this:

hub 4-0:1.0 connect-debounce failed, port 1 disabled
hub 4-0:1.0 over-current change on port 2
hub 4-0:1.0 connect-debounce failed, port 2 disabled
hub 4-0:1.0 over-current change on port 3
hub 4-0:1.0 connect-debounce failed, port 3 disabled
hub 4-0:1.0 over-current change on port 4
...

After waiting a few minutes hoping for some change, I turned it off.  (I had to use to power button; is there any other way to stop the installation?)  I tried again twice but with the same result.  So, does anyone have any ideas on how to figure this out?  I'm sorry I can't provide more information; I'd be glad to try to find out anything that I've left out.  Any suggestions would be most appreciated.  Thanks for your time.

--Elim

---

### Post by nic2 on 2005-08-18
Have you tried running the Live CD to see if that at least boots up?

---

### Post by Elim on 2005-08-18
^^I have not; thanks for the suggestion.  I'll probably have to wait until this evening to try it, but I'll let you know what happens.

---

### Post by Elim on 2005-08-21
The live CD runs into the same problem that the regular CD does.  Anyone have any other ideas?

---

### Post by nic2 on 2005-08-21
Try using the default settings in the BIOS, if you still get the same error try updating the BIOS (latter worked for me on previous notebook after I got a whole lot of error messages)

---

