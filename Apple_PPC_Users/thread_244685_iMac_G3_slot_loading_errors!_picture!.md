---
title: "iMac G3 slot loading errors! picture!"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by Rx7dude on 2006-08-26
does any one know what this means i need or whatever?


[IMG][IMG]http://static.flickr.com/97/225564845_329213b0cc_b.jpg[/IMG][/IMG]

---

### Post by DirtDawg on 2006-08-26
I've had this happen to my g3 before. The problem for me was a dead PRAM battery. Every time I unplugged computer, the time would reset to something like 1903 which in turn would cause this problem. Resetting the clock worked for me. Here's how to do it:

Set the hardware clock to the system clock:
```
hwclock -w
```
Set the date. Here the date is Aug 26 12:15 am 2006. or 08-26-1215-2006. Remember to use military time:
```
date 082612152006 
```
Finally, set the hardware clock again:
```
hwclock -w
```
Then on reboot, everything works just fine.

I hope this works and that your troubles aren't of a larger nature.

---

### Post by Rx7dude on 2006-08-26
okay, but when and where (what screen) would i enter this at?:confused:

---

### Post by DirtDawg on 2006-08-26
If I'm not mistaken, just click okay through all those windows and eventually you'll end up with a command line. Also, you may need to 'sudo' the aforementioned commands, I can't remember.

---

### Post by Dmain on 2006-08-30
I get the same errors, it seems as /dev/rtc is missing. And not being able to retrieve time from network, it resorts in failing.

How do I add it?

---

