---
title: "Macbook with Ubuntu 12.10 running extremely hot"
date: 2013-02-08
forum: Apple Hardware Users
---

### Post by patmur2010 on 2013-02-08
I have cleaned the laptop and through my analysis now believe the problem to be with the fan speed.  According to xsensors 0.70 the two fans are running 1000 rpms and the cpu temp is 57C and rising.  the fans will not adjust speed as the cpu gets hotter and my attempts to manually control them have failed.  

I now reach out to this community in my first post in an attempt to diagnose the problem and resolve the situation.

I attempted to run any programs i found from posts on this forum and elsewhere to no avail.  something called lm-sensor as well as this post [http://ubuntuforums.org/showpost.php?p=10246215&postcount=6](http://ubuntuforums.org/showpost.php?p=10246215&postcount=6)

ubuntu 12.10 is also not booting consistently, maybe 25% of the time is goes to blank screen but this is a minor inconvenience compared to the heat.

The macbook has not shut itself down from the heat yet but i have not left it running for long periods of time.  it does get extremely hot to the touch mainly above the keyboard, on the bottom, and the left half of the keyboard.  

The serial number is w863410dvwz and emc no. 2101.  It has a core2due processor and 1gig of ram, 32 bit processing only.  

Any and all help is appreciated!  Thank you

---

### Post by libarts on 2013-02-18
Hi, I had the same problem, and that's why I decided to only use the Virtual Box instead; however, I found your link to be interesting.  Did you follow all the steps?  What were the results of your attempts?  What other methods have you used?

Concerning heat and fan control, from what I've found, the community has little to offer.  I'd be interested in any solutions you arrive to and would like to help you with some places I've found as soon as you've answered the questions above.

Thank you, good luck. ):P

---

### Post by ksatta1 on 2013-02-21
> **patmur2010 said:**
> I have cleaned the laptop and through my analysis now believe the problem to be with the fan speed.  According to xsensors 0.70 the two fans are running 1000 rpms and the cpu temp is 57C and rising.  the fans will not adjust speed as the cpu gets hotter and my attempts to manually control them have failed.  

I now reach out to this community in my first post in an attempt to diagnose the problem and resolve the situation.

I attempted to run any programs i found from posts on this forum and elsewhere to no avail.  something called lm-sensor as well as this post [http://ubuntuforums.org/showpost.php?p=10246215&postcount=6](http://ubuntuforums.org/showpost.php?p=10246215&postcount=6)

ubuntu 12.10 is also not booting consistently, maybe 25% of the time is goes to blank screen but this is a minor inconvenience compared to the heat.

The macbook has not shut itself down from the heat yet but i have not left it running for long periods of time.  it does get extremely hot to the touch mainly above the keyboard, on the bottom, and the left half of the keyboard.  

The serial number is w863410dvwz and emc no. 2101.  It has a core2due processor and 1gig of ram, 32 bit processing only.  

Any and all help is appreciated!  Thank you

This works for newer Macbooks atleast: [https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa) (package macfanctld). You can set at which temps the fans run at full speed etc.

---

### Post by patmur2010 on 2013-02-22
well my fan started running at 3k+ rpm, so either the macfanctld worked or something in the latest update helped. I installed macfanctld from ubuntu software center and immediately suffered wifi connection issues until i removed it.  but the fans seem to be working better.  

I still have issues booting.  the first time i try to boot it always flashes the ubuntu background then the screen turns off (blank screen).  after a manual shutdown it then boots to the grub bootloader fine.

any ideas?

Update: i reinstalled macfanctld and now everything is working fine wifi and all.  i have not been able to figure out how to customize macfanctld though...

Update2: i installed ati driver from ubuntu software center and the system boots much quicker and skips the grub loader.  but (lol) when i log in my desktop is now blank ie. missing the top menu and desktop icons on the left.  uninstaling the ati driver fixes this but puts me back in the other situation so...i will attempt to find a way to get the desktop working correctly again with the ati driver...any help would be appreciated

---

