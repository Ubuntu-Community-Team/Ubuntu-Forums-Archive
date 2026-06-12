---
title: "New to Linux and Ubuntu have some video card drivers upgrade questions"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mkabwilliams on 2007-01-31
Hi
I'm new to Linux and Ubuntu and need a little help. I've installed 6.10 on a new Dell Optiplex 745 it has a Radeon X1300 Card in it and I need to know how to update the drivers in Ubuntu. I have absolutely no idea how to do this.


Thanks

---

### Post by tchoklat on 2007-01-31
try this


[https://launchpad.net/ubuntu/+ticket/3299](https://launchpad.net/ubuntu/+ticket/3299)

---

### Post by Spr0k3t on 2007-01-31
I just tested a Dell Optiplex 745 and had no issues with the installed hardware, everything installed with edgy no problems.  The only item I do not have is the ATI X1300.  At least this will eliminate other hardware issues for you.  Not a fan of these things... I unboxed 164 of these things and will be shipping back almost a third due to doa.  Tight spot in some areas of the form factor (case) and quite proprietary.  So if any bit of the hardware fails later on, expect a high dollar for replacement components.

Here's an unofficial Wiki install guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Here's a good guide for which has the above link:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Hope that helps!

---

### Post by 67GTA on 2007-01-31
I just finished installing the driver for my x1600 radeon card. Go to ATI and download the driver for your card, it is self installing. Log in as root. Follow the instructions and it will install. When it is done open the Terminal and run the command:    /usr/X11R6/bin/aticonfig --initial    to configure the driver and then reboot. You can also veiw the install instructions at the driver download page.

---

