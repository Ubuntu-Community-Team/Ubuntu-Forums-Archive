---
title: "Gutsy Gibbon problems"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-10-26
I had been using Feisty Fawn for a little over a month now but I wanted to upgrade to GG when it came out. This time I dedicated my second hard drive to ubuntu and set up three partitions with /home, /boot, and /.

Before I even had the chance to install 7.10 im running into incredibly slow loading times from the disc. It took an hour for the disc to load up on my 32x cd-dvdrom. I thought this could be a problem with the cd but my 7.04 install disc came up quickly. I ran a checksum and verified the hash to make sure there wasnt a problem with a disc, everything came out fine. Then I had the disc run a check on itself to make sure there were no errors. Nothing came up. 

After it loaded I created my partitions and formatted my secondary hard drive. The installation went smoothly but took longer than the 7.04 install. Now when it loads up it takes more time that 7.04 was taking to load, and im noticing 'freezing.' I cant say what it is because the mouse doesnt move and nothing will come up during these times. The freezing can last anywhere to a few seconds to a minute plus. So far i've had nothing but problems during the clean install and switch. My question is if these bugs are resolved upon updating online? Has anybody else experienced this? Is it my hardware? By the way this is what im currently running.

Intel Pentium D
Intel D94GCcr motherboard
2gigs of ram (DDR)
ATI Radeon X1950 Pro

---

### Post by phidia on 2007-10-26
You may want to look and/or ask this question in the install and upgrade f[orum]("http://ubuntuforums.org/forumdisplay.php?f=140").

You can also try and open CLI by pressing Ctrl+Alt+F1 keys together and <enter>.
If you get the commandline you can then type dmesg and see if that will output where the boot is hanging at.

---

### Post by meanburrito920 on 2007-10-26
The problem might be that the graphical effects are hanging up your graphics card. Check to see if the card has 3d acceleration enabled or if your 3d effects are on. if you turn off the 3d effects or turn on the 3d acceleration it may solve your problem.

---

