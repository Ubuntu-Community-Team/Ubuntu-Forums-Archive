---
title: "Ubuntu reboots itself in the middle of songs."
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-05-07
I am playing songs in Rythmbox (over a network if it matters) the computer will just spontaneously reboot. I don't know if this computer is having hardware problems or not, but I have not seen it reboot like this at any other time.

Any way I can see what specifically causes the reboot?

I have default Feisty install, I turned off enhanced desktop. The sound is on the motherboard (nforce3)

Thanks?

---

### Post by Tundro Walker on 2007-05-07
Open up a command-line, and use this to start Rhythmbox...

```
rhythmbox > /home/HelloKitty/Desktop/t.log 2>&1
```Replace "HelloKitty" with whatever your home / user directory is.

That basically tells Rhythmbox to start, but to log all feedback (both good and bad) to a log file called "t.log" on your Desktop.  When your computer reboots, open that t.log file and see if there was an error caused by Rhythmbox that caused it.

If there's no such error in the t.log file, then it was something else causing the spontaneous reboot.  Might want to check the regular system log files...

** (Start) > System > Administration > System Log**

Scroll all the way to the bottom of each one.  You should see some kind of error message some where, usually with something like **WARNING** or **ERROR** making it jump out.  Copy/Paste anything that looks suspicious in a reply, and it'll help others troubleshoot your issue.

---

