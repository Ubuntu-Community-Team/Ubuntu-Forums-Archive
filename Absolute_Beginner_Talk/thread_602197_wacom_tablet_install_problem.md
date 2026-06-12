---
title: "wacom tablet install problem"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by wog on 2007-11-04
I have an old Wacom Digitizer II model number UD-0608-R, old enough that it uses a 9-pin serial port. I plugged it in, it has power, but Ubuntu does not seem to recognize it.

So I went into Synaptic and started installing everything associated with the tablet.

I got an error message:
[http://www.facebook.com/photo.php?pid=215778&id=726637818](http://www.facebook.com/photo.php?pid=215778&id=726637818)

What does this mean and how do I fix it?

---

### Post by SpiritIsReality on 2007-11-04
howdy
any help here?
[http://www.nabble.com/UD-II-pen-tilt-and-pad--t3886296.html](http://www.nabble.com/UD-II-pen-tilt-and-pad--t3886296.html)
could maybe reply to his mesage and get info?
I don't know how to find the driver he's talkin' about. maybe you do.

[http://www.google.ca/search?hl=en&q=linux+Wacom+Digitizer+II+model+number+UD-0608-R&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+Wacom+Digitizer+II+model+number+UD-0608-R&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+UD-0608-R&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+UD-0608-R&btnG=Google+Search&meta=)

wacom tablets at ubuntuforums.org, but UD-0608-R not mentioned.
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22wacom+tablet%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22wacom+tablet%22&btnG=Search&meta=)
trails

---

### Post by wog on 2008-03-02
> **SpiritIsReality said:**
> howdy
any help here?
[http://www.nabble.com/UD-II-pen-tilt-and-pad--t3886296.html](http://www.nabble.com/UD-II-pen-tilt-and-pad--t3886296.html)
could maybe reply to his mesage and get info?
I don't know how to find the driver he's talkin' about. maybe you do.

[http://www.google.ca/search?hl=en&q=linux+Wacom+Digitizer+II+model+number+UD-0608-R&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+Wacom+Digitizer+II+model+number+UD-0608-R&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+UD-0608-R&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+UD-0608-R&btnG=Google+Search&meta=)

wacom tablets at ubuntuforums.org, but UD-0608-R not mentioned.
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22wacom+tablet%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22wacom+tablet%22&btnG=Search&meta=)
trails

Nope.

The first one refers to a driver that requires tcl/tk and yum, and while I was able to install yum, tcl/tk doesn't currently exist for Ubuntu, or if it does, I haven't the faintest idea how to get it.

The second and third one refers to a tablet which is usb, and the pad I have has an rs232 connection instead. Not helpful, I think.

Inputting ```
wacdump -c serial -f art2 /dev/ttyS1
``` gets me a readout and outputs for all the appropriate numbers which are coming from the pad, but I still don't know how to get Ubuntu to recognize the pad. This tells me the pad is working properly.

I don't know how to install drivers for this pad. Can anyone help me figure out what to do to solve this?

---

