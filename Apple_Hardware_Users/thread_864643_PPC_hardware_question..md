---
title: "PPC hardware question."
date: 2008-07-19
forum: Apple Hardware Users
---

### Post by MDSanta on 2008-07-19
A while back I got my hands on an old iBook G4 with a dead hard drive, so I did what anyone else would do. Install a new hard drive and put some ubuntu on it. Ubuntu works as much as you would expect it to work on that computer which is good enough for me. But I have a little problem, the laptop over heats like crazy now and just crashes constantly. At first I thought it was the OS change. But then I realized, im one of those people who always has a screw left at the end of a project and doesnt bother tosee where it goes. 

Amyways,when I placed the hard drive in, I removed the metal shielding inside the laptop which I assuming was meant to be spreading out the heat evenly on it. Now that is all gone, do you think replacing it with regular aluminum foil would work as a replacement? or will i have to cough up 20 bucks a thin sheet of metal cut out for the laptop on ebay?

---

### Post by cyberdork33 on 2008-07-19
Aluminum foil is probably not thick enough, plus you will have to be very careful with it to make sure it does not come into contact with anything that is not supposed to.

---

### Post by stream303 on 2008-07-20
Only on my G4 iBook, I found that Network Manager was eating up most of the cpu time, causing the system to overheat and run the fans pretty hard.  Can you run top in a terminal and see if Network Manager shows up at the top of the list?

If so, you may want to disable it, rather than remove it:

[https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

Another thing to check is that cpu frequency-scaling works.  You could try adding a frequency-scaling monitor applet and see if the cpu is constantly running at full-speed.

If so, one thing you may want to do is try using CPUDYN rather than the default POWERNOWD daemon to control the cpu freq.  Cpudyn is downloadable from the repos.  (Note: this was only an issue on my G5 iMac, and I sold the ibook before I got a chance to check the frequency-scaling issue out there too.)

---

### Post by MDSanta on 2008-09-01
thanks for the suggestion, ill give it a shot.

---

