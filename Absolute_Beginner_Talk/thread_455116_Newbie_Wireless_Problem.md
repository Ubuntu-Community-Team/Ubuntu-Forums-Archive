---
title: "Newbie Wireless Problem"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Belbarid on 2007-05-26
I just installed Ubuntu 7.0.4, and I can't get my Linksys USB wireless card to work.  After reading the directions a couple times, I've got more questions than answers.  :(

Why do I have two entries in System->Administration->Network for my wireless card?  I have a Wireless Connection (wmaster0) and a Wireless Connection (wlan0).

When clicking on the properties of either of the above, I do not have an "Enable this connection" checkbox, as the documentation says I should.  I have an "Enable Roaming Mode" box, which grays everything out when checked.  What does this do?

I do not have an "Default Gateway Device" select box in my Network window.

Reading the Troubleshooting Guide, I tried the following: "iwpriv wlan0 authmode 2" and was informed that authmode was an invalid command.

Any ideas?

---

### Post by Bachstelze on 2007-05-26
First, make sure your wireless adapter is properly detected :

```
sudo iwconfig
```

---

### Post by Austin_KW on 2007-05-26
Which adapter is it? 
If it is the ralink chipset, then the drivers supplied with ubuntu dont work. See this howto [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by Belbarid on 2007-05-26
Thanks much- I will give that a try.  I'm using the WUSB54GC, which does appear to use the ralink chipset.

---

