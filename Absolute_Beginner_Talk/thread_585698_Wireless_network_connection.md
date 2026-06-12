---
title: "Wireless network connection"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by demoncleaner on 2007-10-21
I have been using a BT Voyager 1250 ADSL modem/router without any problems for the past 2 years under Windows XP.
After installing Ubuntu 7.10 and booting it up the system readily recognised my wireless network and asked for the WEP key when clicking on it. I entered the 64bit HEX key correctly and when trying to connect to the network the system caused the  router to continuously reset itself and therefore crash the network completely which stopped immediately when cancelling the contact attempt.
Any bright ideas how I can remedy this issue?
Thanks.

Chris

---

### Post by molly_001 on 2007-10-22
The description of the problem is certainly interesting.  Can you tell us what the network adapter is on your computer?

---

### Post by demoncleaner on 2007-10-22
It is a D-Link AirPlus G DWL-G122 Wireless USB Adapter.

---

### Post by evilregis on 2007-10-22
Do you know which driver is being used for your D-Link adapter?

---

### Post by demoncleaner on 2007-10-22
rt73usb

---

### Post by molly_001 on 2007-10-22
I suspected this was not an integrated or even PCI card based network adapter. (from the behavior described in the OP, I mean).

If you can confirm that your wireless G122 adapter is revision B1, then you can likely follow the directions below to get it working:
[http://jeremydenise.net/en/node/189](http://jeremydenise.net/en/node/189)

---

### Post by demoncleaner on 2007-10-22
Well, it seems that it is hardware version C1.
Will that work?

---

### Post by demoncleaner on 2007-10-22
When checking the Ralink website there seem to be several drivers including the one mentioned in the description and also an RT73 specific driver. Should I use that one?

---

### Post by molly_001 on 2007-10-22
In my opinion it would be very much worth a shot to try the Ralink version of the RT73 driver.  However, I would bookmark that guy's Jeremy site which I gave you earlier.

Then install this Ralink RT73 driver.  See if it makes life easier.

If it does not, then I would follow Jeremy's instructions (albeit with the RT73 driver) and see if it does the trick.

---

