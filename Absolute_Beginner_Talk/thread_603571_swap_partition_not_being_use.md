---
title: "swap partition not being use"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by pairojte on 2007-11-05
I notice that my swap partition is seldom use by system and that cause my system running very slow.(I monitor by using system monitor) How can I force system to use swap partition? (My swap partition is 1 GB)

---

### Post by Inxsible on 2007-11-05
Ubuntu automatically figures out when it needs to use the swap. So if its not required then it won't use it.

How much RAM do you have? 

There could be another app which has a memory leak which may be causing your system to run slow.

---

### Post by mikedep333 on 2007-11-05
Check your /etc/fstab file ( open it with gedit as root [alt+f2, enter: gksu gedit /etc/fstab]).
You should see a line with "swap" in it like this:
UUID=2e82692a-647f-4fb1-b782-872c0b8060a3 none swap sw 0 0

The UUID will vary according to system, but if nothing else is different then your system is configured to use swap fine.

Keep in mind that unlike Windows, Linux doesn't use the swap file unless it has to, which is much more efficient. For example, Windows XP uses up 250 megs of memory + 250 megs of swap on boot, while ubuntu 7.10 uses up 250 megs of memory + like 1 meg of swap on boot.

If you have alot of memory (1 gig or more, and perhaps even 512 megs) then there is probably no good reason for your system to use swap unless you are doing some memory intensive huge rendering job or something. If your system is slow, it is probably due to something else, like some other process using up a lot of CPU time/power.

Still, why don't you tell us what the average CPU usage, the average memory usage (user memory in use by programs, not memory in use by buffer or cache), and the average swap usage are when your system goes slow?

---

### Post by LowSky on 2007-11-05
If you have more than enough RAM then Swap wont be used as often

try playing a dvd and watch the system monitor, or open 15 programs,  swap space will get used fequently at that point.

---

