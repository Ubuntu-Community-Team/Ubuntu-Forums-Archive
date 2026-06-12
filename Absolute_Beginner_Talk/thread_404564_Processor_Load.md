---
title: "Processor Load"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by hlnoiku on 2007-04-08
Hi,

Just installed 6.1 onto a 400mhz P2 Dell Inspiron 7500. Is there a reason why the cpu utilization is constantly pegged above 95% (idle usage ie. me doing nothing) all the time? XP had it at 3-4% unless it I was actively using applications. Any ideas? Thanks in advance for your time and effort!

---

### Post by hyper_ch on 2007-04-08
where does it say 95%

Please open a terminal, enter "top" and post the load average here :)

---

### Post by hlnoiku on 2007-04-08
It shows the load in the system monitor application.

System-Administration-System Monitor

I entered the "top" command in the terminal as per yoru instructions however I'm not too sure as to what im looking for.

After the "load average" it states "2.07, 1.61, 1.19"

---

### Post by hyper_ch on 2007-04-08
ok, and what are the top running applications that you see?

---

### Post by hlnoiku on 2007-04-08
I'm assuming you mean the apps listed under the "command" column? 

If so they are: Xorg, gnome-system-mo, top, gnome-terminal, init.

Just an update, the processor load dipped down from the high 90's (where it had been for the past 20 minutes) and is now fluctuating between 13% and 22%.

---

### Post by hyper_ch on 2007-04-08
maybe it was just a temporary thing....

yes, below the stats on top you see the processes liste (normally) sorted by the current cpu usage

---

### Post by steevk on 2007-04-08
It's quite possible that it's because you're running it on a P2. I mean, modern desktop environments like Gnome or KDE aren't exactly low-resource friendly.

---

### Post by hlnoiku on 2007-04-08
Well the problem's gone now. I'll take it that maybe it was configuring itself or performing an update. Either way its pretty speedy when compared to the XP Pro installation I had on it, so all in all I'm one happy camper. Thank you very much for your help hyper_ch. It was greatly appreciated. I'll probably be on and off these forums quite a bit as I attempt to orient myself with the OS/linux. It gives me great peace of mind to know that there's such a speedy and knowledgeable support base among the community. 

Cheers,

hlnoiku

---

### Post by tgalati4 on 2007-04-08
Whenever you add programs or after a certain period of time, the slocate database gets updated.

This can take a while.

With a stopwatch try:

sudo slocate -u

This updates the slocate database so you can use

locate gimp

Other processes are the dpkg database--where your dependencies are stored--this can take a while after doing any upgrades.

Housecleaning of /var/log.  Do you have a lot of files there?

Run w to get a quick snapshot of load.

Whenever your load is consistently above 1.0 (rough number of tasks waiting or 100% cpu usage) then run top to see what is causing it.

killall mylongrunningprocess

If you are impatient or if you know you have something hung.  Otherwise wait and let Linux be linux.



To find all occurances of gimp.

---

