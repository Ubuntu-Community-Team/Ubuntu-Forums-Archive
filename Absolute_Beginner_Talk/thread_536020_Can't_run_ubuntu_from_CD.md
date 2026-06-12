---
title: "Can't run ubuntu from CD"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by CobraJunky on 2007-08-27
I've copied ubuntu ISo  to a CD.  I boot from the CD and get to the start screen.  I select the first choice to Start or Install ubuntu, the screen flashes "loading system..." (or something like that) and the screen goes blank.

---

### Post by Jussi01 on 2007-08-27
Ok, couple of things, how long did you leave it for? (it takes about 5 mins for me).

Also what is your hardware? do you have an ati or nvidia graphics card? Please list your exact hardware here so we can know a little more.

---

### Post by Webby_s on 2007-08-27
You may want to  check the MS5SUM of the disk and ISO file. Also they recommend to burn the disc at 4x (really slow) so as not to screw up the image burning.

[Here is a link]("https://help.ubuntu.com/community/BurningIsoHowto") that will help you with all of this! If you have done all that is listed then I would maybe just try a new cd and reburning the image. Good luck.

---

### Post by khughitt on 2007-08-27
One option you could try is to run a newer [testing version of Ubuntu]("http://cdimage.ubuntu.com/releases/gutsy/tribe-5/"). I wouldn't recommend installing it since it is not as stable as the normal version, but if it works it could at least give you a chance to play around with Ubuntu, and possibly shed some light as to the nature of your problem.

---

### Post by abhilash82 on 2007-08-27
What is your hardware specs.? Try booting in safe graphics mode option.

---

### Post by Jimmyfj on 2007-08-27
Depending on your hardware specs you might wanna try the alternate install Cd. Be sure to check the MD5SUM before burning the iso to a disk.

---

### Post by CobraJunky on 2007-08-27
Thanks for the quick replies.  I'm burning the CD at 4X and will try again.  I didn't wait but only a minute or so. I'll be more patient next time. Sorry, should have posted the system details. System is:

Dell Dimension 4500
Pent 4 CPU 1.8GHz
IDE CDROM - Samsung CDRW/DVD SM332B
Display Adapter - Intel(R) 82845G/GL/GE/PE/GV Graphics Controller

Todd

---

### Post by CobraJunky on 2007-08-27
> **Jimmyfj said:**
>  Be sure to check the MD5SUM before burning the iso to a disk.

How?

---

### Post by Outrunner on 2007-08-27
> **CobraJunky said:**
> How?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kerry_s on 2007-08-27
> **CobraJunky said:**
> Thanks for the quick replies.  I'm burning the CD at 4X and will try again.  I didn't wait but only a minute or so. I'll be more patient next time. Sorry, should have posted the system details. System is:

Dell Dimension 4500
Pent 4 CPU 1.8GHz
IDE CDROM - Samsung CDRW/DVD SM332B
Display Adapter - Intel(R) 82845G/GL/GE/PE/GV Graphics Controller

Todd

you left out the important part "ram", 256->512, 512 recommended for the livecd.

---

### Post by CobraJunky on 2007-08-27
> **kerry_s said:**
> you left out the important part "ram", 256->512, 512 recommended for the livecd.

640Meg

---

### Post by CobraJunky on 2007-08-27
Tried a new burn at slower speed and no luck.  Fails at the same point.  Seems to be graphics related but uncertain.

---

### Post by Marat Galiev on 2007-08-27
Start ubuntu live-cd in "safe graphical mode".

---

### Post by CobraJunky on 2007-08-27
> **Marat Galiev said:**
> Start ubuntu live-cd in "safe graphical mode".

Tried that.  Still nothing

---

### Post by khughitt on 2007-08-28
Your best bet is either to install in textbook either with the regular livecd or the alternate install, or, you can try loading gusty and see if that works.

---

### Post by CobraJunky on 2007-10-02
Still can't load the live CD.  I can successfully run this on my HP Laptop but have graphics problem on my Dell Demension 4500S with Albatron Monitor.  Again,  I boot from the CD and get to the start screen. I select the first choice to Start or Install ubuntu, the screen flashes "loading system..." (or something like that) On my laptop, it has a series of loading status text in lime green font.  My desktop just shows long skewed  lime green lines across the screen.  Anything I can do to get around this?

---

