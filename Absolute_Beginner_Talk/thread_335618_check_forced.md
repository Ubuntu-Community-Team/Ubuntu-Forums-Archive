---
title: "check forced"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-01-10
new user here, very curious about what happened:

upon normal boot, i got this message:

"linux has been mounted 20 times and has not been checked. check forced"

where it proceeded to scan my system or something. then continued to boot as normal. 

anyone care to explain what this is? thanks

---

### Post by ComplexNumber on 2007-01-10
> **finer recliner said:**
> new user here, very curious about what happened:

upon normal boot, i got this message:

"linux has been mounted 20 times and has not been checked. check forced"

where it proceeded to scan my system or something. then continued to boot as normal. 

anyone care to explain what this is? thanks
absolutely nothing to worry about. it just checks every now and then to see if the filesystem is in good working order

---

### Post by d3v1ant_0n3 on 2007-01-10
> **ComplexNumber said:**
> absolutely nothing to worry about. it just checks every now and then to see if the filesystem is in good working order

Normally when you just need to boot the computer quickly to check something:-k  It knows, I tells ya!

---

### Post by meng on 2007-01-10
This is a normal maintenance procedure. It could potentially be annoying if it happened 2 minutes before you really needed to use the computer in a hurry (e.g. presenting to clients or co-workers). If this could be a problem, then you could use tune2fs to change the parameters (i.e. number of mounts in between checks).

---

### Post by jvc26 on 2007-01-10
Another good input from Ubuntu (except in situations like those Meng mentioned ;)) Just makes sure all is in good working order, and also tends to make sure errors dont go long unchecked.
Il

---

### Post by MindRiot on 2007-01-10
I know this isn't Windows, but Is there way to schedule the check on the next mount, so you can reset the timer, so too speak?

---

### Post by Hendrixski on 2007-01-10
I believe it only does this with a dual boot setup. Uninstal your Windows partition and problem solved.

Also you can skip it if you need to get stuff done.  hit ESC or something

---

### Post by ajgreeny on 2007-01-10
> **MindRiot said:**
> I know this isn't Windows, but Is there way to schedule the check on the next mount, so you can reset the timer, so too speak?

Shutdown using a terminal by typing:-
sudo shutdown -hF -now
or
sudo shutdown -rF now

The first will halt the machine and do fsck next boot, the second will restart and do fsck straight away.

---

### Post by MindRiot on 2007-01-10
Nice. :) 

Thank you

---

### Post by jd65pl on 2007-01-10
> **Hendrixski said:**
> I believe it only does this with a dual boot setup. Uninstal your Windows partition and problem solved.

Also you can skip it if you need to get stuff done.  hit ESC or something

fsck is called periodically regardless of whether another operating system is present. The function checks for errors on each partition and for filesystem consistancy. It shouldn't pop up to much on boot unless you are prone to alot of reboots. It may also be called if the system has a "difficult" shutdown

J

---

### Post by G Morgan on 2007-01-10
> **Illuvator said:**
> Another good input from Ubuntu (except in situations like those Meng mentioned ;)) Just makes sure all is in good working order, and also tends to make sure errors dont go long unchecked.
Il

I don't mean to be picky but this is a general trick in Linux not unique to Ubuntu.

The time to be worried is when your partition stops periodically fscking since then something has gone wrong.

Note that it will do this for all partitions and they may not all be set to check after the same number of mounts so it is possible to get a fsck then reboot and get another straight afterwards.

---

### Post by ramjet_1953 on 2007-02-22
The check forced scan can be a problem for those of us who use laptops and visit clients.

Of course, Murphy will come into play and the 30th mount will occur, just as you have your hottest prospect waiting.

I downloaded a great app called [COLOR="Red"]Bonager[/COLOR], which gives you control over when the scans occur. It can even delay a scan if it comes up at an inconvenient time.

There is a thread somewhere on these forums for Bonager, just do a search and I'm sure that you will find it.

Regards,
Roger :cool:

---

### Post by nanotube on 2007-02-22
you can just hit <ctl>C to cancel the scan.

---

### Post by parsim on 2007-05-03
This raises an issue that has bugged me for years. Why are periodic fscks scheduled for boot rather than shutdown?

Obviously any time the system boots following an improper shutdown, it needs to fsck. But for the life of me I can't figure out why the every-21st-mount fscks, which are just in case there's been any undetected corruption, have to happen at the exact moment you want to use your computer.

When I shut my computer down for the day, I don't care how long it takes. But when I turn it on, I want it available ASAP, not seven minutes later. Why not fsck on every 21st unmount?

---

