---
title: "CPU fan won't come on in Feisty"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-07-24
New install of Feisty.  Kept shutting down after a few minutes.
Eventually found that my CPU fan is not running.   Works OK in Windows.

In the BIOS i had fan controlled by temperature and it worked OK, but under Feisty the fan simply will not start.

I have now disabled fan control in BIOS and am able to run Feisty again but with the fan running full belt at 100dB!

I've looked at other threads which all relate to laptop power management issues but my machine is a desktop.  Worked fine with 6.04, even running FAH 24 hours a day.

What's different in Feisty and how can I adjust it?

Thanks

---

### Post by benx009 on 2007-07-24
[HOWTO: manual fan control]("http://ubuntuforums.org/showthread.php?t=230673") 
don't know if it will help, but give it a shot

---

### Post by Phosphoric on 2007-07-26
Thanks for the link  benx009, interesting but not what I was after.

I currently have my BIOS temeperature control of the the CPU fan turned off, which stops Ubuntu's ACPI trying to control it.  Thus the fan runs at full speed.  I may then stick a 100 ohm pot in the 12V supply and adjust the speed manually, but it's not really the point is it. :(

In some of my reading elsewhere,  I think there may be a link to ACPI problems and the flgrx ATI driver, which I have.
I'll have a play with that I think.

---

