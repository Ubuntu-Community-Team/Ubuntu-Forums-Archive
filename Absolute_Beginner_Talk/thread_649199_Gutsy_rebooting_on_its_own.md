---
title: "Gutsy rebooting on its own"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by bill.blankenship on 2007-12-24
Hi everyone,

I have updated my Dell Latitude D620 laptop to Gutsy and it went pretty smooth. However, I've had three different occurrences (so far) of the computer rebooting completely on it's own. Luckily, I didn't really lose any work because I save and save often. ;-) However, this IS an issue that I think needs to be addressed.

I'm nowhere NEAR being leet on using Linux, but I at least know how to go in an take a gander at the log files. I was unable to find *any* indication of an error immediately prior to rebooting...  one minute it's running just fine, and the next it's going through a reboot. The screen goes pale white, then I see my BIOS screen that shows during a cold power up, and the computer works just fine.

I'm pretty confused on this one. This MIGHT be related to a [[COLOR="Blue"]similar posting by *auditory*[/COLOR]]("http://ubuntuforums.org/showthread.php?t=463640"), but I do NOT have auto-updates enabled, and I KNOW it wasn't due to a power outage since I was sitting at the machine and working when it decided to reboot.

Clues anyone? 

Happy Hacking!

---

### Post by ijason on 2007-12-24
my gutsy install would reboot itself when the openGL screen-saver tried to kick on... i'm running XGL for my 3d acceleration. the only solution i could find was to turn off the screen saver :/ don't know if this might be your problem :confused:

---

### Post by bill.blankenship on 2007-12-24
I would have suspected something like that if the machine had been idle before rebooting, but this happens when I'm actually working on the box. (yes, I do have to work sometimes... ;-) )

I haven't been able to detect any type of pattern on the programs I'm using (if that would be causing the problem...) One time I was browsing with Firefox, and the most recent time I was working in KMyMoney.  There just doesn't seem to be any indication as to what is causing it to reboot.

---

### Post by Majorix on 2007-12-24
I have the same problem with Hardy. However I am thinking I know the reason: A stupid program called beagled and beagled-helper use helluva CPU power, probably causing it to overheat and forcing the motherboard take measures (ie reboot the PC) but then it is booted back into an environment with this silly program.

What I suggest:
-Launch System > Admin > System Monitor.
-If View > All Processes is not enabled, then enable it.
-Check if there is any program using too much CPU, like with beagled in my case.
-If you have found any programs that do so, kill their processes for now and write a few lines in your /etc/rc.local that would kill these processes as soon as the comp starts up.

What I suggest otherwise:
I was having these problems before too, with just any OS, any program. I found out that it was my Reset button that was getting automatically pressed on its own, forcing a reboot. Taking out its pins on the motherboard fixed it for me. I never used that stupid button anyways.

Best of luck.

---

### Post by ijason on 2007-12-24
weird. i'd recommend booting off the livecd and running it for a while to see if the problem persists. if it does, then there may be some weird inherent incompatibility with your system, or some inconveniently timed hardware glitch on your machine. if it doesn't happen, then you've at least limited the scope of the problem to something inside your particular install :)

---

### Post by e_james on 2007-12-24
About 2 weeks ago my desktop started doing similar things (Windows or Linux), with 2 exceptions. It was most likely to reboot when the internal DVD started to spin. The PC would start up on its own after being switched off. After some thought I replaced the psu and the problem seems to be fixed.

---

