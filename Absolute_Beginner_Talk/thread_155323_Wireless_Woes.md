---
title: "Wireless Woes"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by ShadeOfGreen on 2006-04-04
After consulting the wiki with no avail I figured I'd just ask.

I have a Netgear wireless adapter and before I had been getting a signal from my neighbor to get access.

The card comes up as ath0 and seems to pick up the different networks around my building but I can't get access. 

Is there anywhere where theres a graphical display for the signal strength.  I have a feeling the signal just isn't strong enough and if I knew where in the room I might get a strong one I might be better off.

Thank You.

---

### Post by moephan on 2006-04-04
There is an applet that you can add to your gnome controll panel that will show signal strength. However, possible a better way is to get the information from a terminal window. Open a terminal and type in the following command:

```

iwconfig

```

This will let you know if you are connected. For more information about wireless connection points, use:

```

sudo iwlist scanning

```

This will tell you what is available in your range, and give you information about the strength, qualitym, and speed of each point.

HTH.

Cheers, Rick

---

