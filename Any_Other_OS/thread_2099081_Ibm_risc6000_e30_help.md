---
title: "Ibm risc/6000 e30 help"
date: 2012-12-28
forum: Any Other OS
---

### Post by FepzHz on 2012-12-28
I have stumbled upon an IBM RISC/6000 E30. It was used as a server for a company back in the 90's. I was asked to take a look at it, and well i have ZERO experience with servers but i want to take the chance to learn something from this. But i obviously don't want to damage anything. I pluged the power and it turned on, it was spitting out some numbers from a display it has on the front bessel, i was unable to get my hands on the manual for this server so im not sure what any of those numbers mean, if its anything like my desktops motherboard's DR,DEBUG im assuming theyre just running checks to see if everything is normal, i also heard something i would say sounded like a siren or alarm but nothing happend. i tried to plug a monitor w/ a VGA connection to the rear connections that looked like VGA ports, theyre were a total of four but none of them were able to connect to the monitor. So now im on a laptop w/ an intel core 2 duo T7300 runing ubuntu desktop 12.10. I connected the server and laptop w/ an ethernet/LAN cable but i was unable to connect to the server. I would appreciate any help i can get, i want to connect to the server and take a look at it, and also find out if it can be used and for what can it be ideal for.  From what ive read from the IBM site it was quite a server in its day.

---

### Post by oldfred on 2012-12-28
Moved to otherOS as that is a Unix system, not Linux.

---

### Post by TheFu on 2012-12-28
I used to manage R6000 multiple F40 and a P25s. That was many years ago.
I worked in a small software development company that supported about 10 different platforms, so we had a few of each.

You probably need to connect to the serial port to see anything if you don't have the correct monitor. I think those servers used PS2 keyboards and mice, so that is good news.  Older models used proprietary interfaces.

Knowledge of PC BIOS isn't very helpful with IBM RS-6000 systems from that time. When one of our boxes failed to boot, we had to call IBM to get service ($200/hr). Turned out one of the CPUs had come loose during shipping from another part of the company and it was the primary CPU.

It is likely that machine doesn't have a graphics card inside, so  only network or console access will work.  DHCP didn't exist back then,  so you'll need to know the exact subnet and IP to access the server from another box,  assuming it even boots into an OS.

I hate to say this, but your new toy is mostly worthless beyond the slight interest in looking at it. I might not even have an OS. My smartphone probably has more CPU power.  AIX was/is a fine OS, BTW.  I found using **smitty** just fine for those times when I needed an administrative GUI.  However, I hated that IBM didn't provide man pages by default.  

I'd have similar, but slightly different complaints about a SunOS, Solaris, HP-UX, DEC or SGI box from that time. To an end-user, the OSes were mostly similar, but to an admin, they were significantly different.

Anyway, good luck.  Your best bet is probably Craig's List or at the local Linux LUG where some greybeard has a basement full of crap that his wife is making him clean out.

---

