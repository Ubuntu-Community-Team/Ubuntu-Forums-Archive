---
title: "Wireless-It's there but...not really"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by geek_overlord on 2007-06-06
Fist I'd like to say that the documentation on this site is excellent. I would not have come this far had I not taken the time to read it. I'm working with breezy on my laptop (an old emachines clunker) and my wireless chip is recognized in lshw however when I go to system/preferences/networking I only see eth0 which is an rj-45 port and a modem connection (not enabled). Do I need a driver for this wireless chip? Thanks in advance for your help.

---

### Post by Ek0nomik on 2007-06-06
What kind of wireless card is it?

You can do```
lspci
``` to find out

---

### Post by geek_overlord on 2007-06-06
According to lshw it's a Broadcom BCM4306 wireless 802.11 b/g wireless controller. lshw also states that it is unclaimed. Hope that helps. The wireless worked earlier today when I had the Win XP drive plugged in.

---

### Post by Ek0nomik on 2007-06-06
Here are some links to get you started.  It doesn't work out of the box, but with a little tweaking you should be able to get your wireless working soon.

[http://doc.gwos.org/index.php/Broadcomm_with_Ndiswrapper](http://doc.gwos.org/index.php/Broadcomm_with_Ndiswrapper)

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

[http://ubuntuforums.org/showthread.php?t=75239](http://ubuntuforums.org/showthread.php?t=75239)

[http://www.mepis.org/node/13166](http://www.mepis.org/node/13166)

I got my 1390 working with ndiswrapper.  Good luck!

---

### Post by geek_overlord on 2007-06-06
Thanks much. It looks like this should do the trick.

---

### Post by geek_overlord on 2007-06-06
question about the code: what is that vertical line after lspci? I don't see anything like it on my keyboard.

---

### Post by neotasic1 on 2007-06-06
> **geek_overlord said:**
> question about the code: what is that vertical line after lspci? I don't see anything like it on my keyboard.

It's a pipe command - you will find it on your keyboard as a broken vertical line (like two vertical dashes)(conventional enhanced desktop keyboard) over the backslash character (\) (Likewise on a laptop keyboard - I just checked) 

It is used to redirect the output to another command usually.  e.g. lspci | less  pipes the output of the lspci command to the less command so that you can then scroll through the output page by page or line by line, scroll backwards etc, rather than having several pages of output dumped on your terminal.

---

