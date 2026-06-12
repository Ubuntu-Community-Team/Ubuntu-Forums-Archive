---
title: "apt-get!!"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-14
Hi

Most of the help information on this site seems to point you towards downloading necessary packages using apt-get and using synaptic to install them.  I am an absolute beginner with Linux, but even I know apt-get is no good while I'm still struggling to connect to the internet through Ubuntu.  Anyway, after many hours of trawling and ripping at what little hair I have left, I believe I have found the necessary software to get my USB D-Link dongle device working... linux-wlan-ng-0.2.0-hh1.tar.gz.  I downloaded it through XP and eventually managed to extract all the files into a folder onto my Ubuntu desktop.  This is where things have come to a complete standstill.  How to I now install the software into my system?  I knew getting Linux would be a learning curve, but nobody told me I would need crampons and plenty of rope!

Any help would be very greatfully appreciated :confused:

---

### Post by mavr on 2006-03-14
What is in that package?

---

### Post by mavr on 2006-03-14
and by the way, what r u trying to have working? a wireless card? a usb modem? Couldn't understand that.

---

### Post by Norfolk 'n' Good on 2006-03-14
I believe the package contains the necessary drivers to get my USB D-Link dongle device going.  Unfortunately I can't give you anymore information then that because I'm at work at the moment And my computer is several miles away.
I found the package somewhere among the Wiki pages while searching for my device... model no: DWL-G122.

Hope that helps

---

### Post by Norfolk 'n' Good on 2006-03-14
I have a wireless ADSL router.  The bit I'm trying to get working is the bit that plugs into my computer's USB.  It transmits signals to and from the router.  I believe once I get the lights flashing on the dongle the rest should be plain sailing.

---

### Post by AndyCooll on 2006-03-14
Usually it goes something along the lines of:

```
cd /into/directory/of/file/to/compile
sudo ./configure
sudo make
sudo make-install
```

---

### Post by Norfolk 'n' Good on 2006-03-14
I have tried exactly that code.  I managed to run through the configure putting the Y's and the N's in the right places, but things ground to a halt after I typed make install.  The reply kept querying the command 'make'?

---

### Post by az on 2006-03-14
You don't need to compile anything.  

[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)

---

