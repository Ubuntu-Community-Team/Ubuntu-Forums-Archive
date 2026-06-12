---
title: "Maverick MacbookPro6,2 keyboard lighting controls."
date: 2010-10-18
forum: Apple Hardware Users
---

### Post by AzN1337c0d3r on 2010-10-18
Hello all,

Today I installed Maverick on my new MBP. I followed the instruction in this Help page: [https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick) but seem to be having trouble getting the keyboard backlight hotkeys to work (LCD Brightness, Media keys, and Sound keys appear to work correctly).

Could anyone point me in the right direction to resolve this issue?

---

### Post by AzN1337c0d3r on 2010-10-18
Seems like the version in the repository is too old (1.32) and doesn't support the latest generation of MBPs.

I tried the 1.34 package from Debian but it seems buggy (doing pommed -d to get debug messages clearly shows the keyboard backlight turning on, but will not turn back off when the light sensor goes back up beyond the range to turn it off)

---

### Post by Technoviking on 2010-10-18
I just uploaded pommed 1.33 built for Maverick to my ppa ([https://www.launchpad.net/~mike.basinger/+archive/ppa](https://www.launchpad.net/~mike.basinger/+archive/ppa)). It should build in the next day or so.

T-V

---

### Post by AzN1337c0d3r on 2010-10-18
Thanks, at last it works.

There is still a weird bug with pommed wanting to turn the keyboard backlight on to full under low light conditions when I hold down the decrease brightness button to turn it off.

---

