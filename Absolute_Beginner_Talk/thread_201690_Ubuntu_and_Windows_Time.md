---
title: "Ubuntu and Windows Time"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by otherworldbob on 2006-06-22
I've managed to get Ubuntu up and running and playing my MP3s, DVDs etc.

However, after running Ubuntu, where the time is correct, I've noticed that my WindowsXP clock loses one hour.
This only happens after running Ubuntu, booting Windows XP multiple times, the time remains correct, once I've corrected, it after a Ubuntu boot. 

Is there anyway to correct this - if so, which OS needs the tweaking, or is it my BIOS settings that need changing?
I'm in the UK with Daylight Saving in effect if that makes any difference.

Apologies if this has been covered before.
Thanks.

---

### Post by simone.brunozzi on 2006-06-22
hello,
it happens to me in dapper drake, i suppose that it depends on the time settings related to GMT clock.
I don't know how, but I managed to avoid it... try some different settings, and see if it works.

cheers,

---

### Post by drifternel on 2006-06-22
Now you mention it
the same has been happening to mine
Its got the potential to be a real hassle on a duel boot machine.
Too new to Linux to help though - sorry.
Sure someone here will know though.

---

### Post by oscar on 2006-06-22
I think windows XP assumes that the hardware clock is set to local time. By default ubuntu assumes the hardware clock is set to UCT (GMT). If you change it so that ubuntu has the hardware clock set to local time it should work.
Right click on the panel's clock and go preferences and untick use UCT.

---

### Post by jorn on 2006-06-22
Try to set:
> UTC=0
In the file:/etc/default/rcS

---

### Post by niteblind on 2006-06-22
noticed when i was installing kubuntu that when you click london by default it is set to BST and would set the clock accordingly. If u check out windows it shows london as being GMT hence the one hour jump

niteblind

---

### Post by otherworldbob on 2006-06-25
I tried the UTC=0 suggestion, but this didn't work - Windows still lost the hour.
However I seem to have gotten around it by telling Windows that I live in France.
Thanks for your efforts though.

---

### Post by Stolie on 2006-06-25
Strange, as it does seem to be a UCT problem. I remember reading somewhere (I can't link to it, since I forgot where it was) that if you set your time to use UCT? I think? Windows will lose an hour each time you reboot...

---

### Post by Apple 101 on 2006-06-25
Set Windows XP to use a NTP server.  That way the time is always accurate.

---

