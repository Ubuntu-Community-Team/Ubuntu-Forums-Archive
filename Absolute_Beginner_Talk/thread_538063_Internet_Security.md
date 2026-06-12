---
title: "Internet Security"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-29
How do i make my ubuntu 7.04 secure if i were to want to protect it from any viruses? Can it use stuff like AVG Free? Does it have built in Security Programs?

---

### Post by amosharper on 2007-08-29
One of the great things about Linux is that there are hardly **any** known viruses, since it is not the most popular Operating System. This means that most users are content to go without an antivirus or antispyware program.

However, if you're not convinced, you can use 'Clam AV'.

---

### Post by WebSiteGuru on 2007-08-29
Ubuntu is already secured.

---

### Post by redfox1160 on 2007-08-29
Thats what i thought, but i wasnt exactly sure. So it probably wont get any viruses from browsing around.

---

### Post by amosharper on 2007-08-29
> **redfox1160 said:**
> Thats what i thought, but i wasnt exactly sure. So it probably wont get any viruses from browsing around.

The chance is next to 0.

---

### Post by asmoore82 on 2007-08-29
> **redfox1160 said:**
> How do i make my ubuntu 7.04 secure if i were to want to protect it from any viruses? Can it use stuff like AVG Free? Does it have built in Security Programs?

[https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)

:KS

---

### Post by aysiu on 2007-08-29
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by redfox1160 on 2007-08-29
thanks! Also, if i plug my computer into my router, would i need to install any software or anything (wired router). Im using Verizon DSL...

---

### Post by dewcansam on 2007-08-29
My experience with linux has yeilded ONE virus (really a worm) that was called [Linux.Ramen.Worm]("http://www.symantec.com/security_response/writeup.jsp?docid=2001-011713-2000-99&tabid=2") . However, I could have prevented this infection by keeping my system up to date. I have also had my systems comprimised once, again because I was running a version of ssh that had a known security hole ( that has since been fixed). The key here is that as long as you keep your system up to date you should be relitively secure. 

HOWEVER, my experience with windoze has yeilded hundreds if not thousands of viruses on my systems and others (mostly on others systems). I use [Anti-Vir]("http://www.free-av.com/") on what win systems i do run it stops most of them. But, most frustrating is that in windoze and can be downright hard to find, track and kill viruses that are not caught by anti-virus software. Mostly because windoze keeps very little logs and even what logs it keeps are not clear and consice as to what happened.

You can't really run AVG or any other anti-virus software made for windoze. But, you don't really need to either.

The easiest way to avoid viruses, worms, hacks or any other malicious software from running is to keep your system up to date. Then use tripwire to track system changes. iptables for firewall rule filters. Which will block any ports that don't need to be accessed from the world.

---

### Post by ts51 on 2007-08-29
Personally, I believe If you are using Ubuntu, Mac OS, or any other linux/unix OS, you'd be wasting your computer and time and possibly money with virus scans and firewalls.

---

### Post by redfox1160 on 2007-08-29
> **dewcansam said:**
> My experience with linux has yeilded ONE virus (really a worm) that was called [Linux.Ramen.Worm]("http://www.symantec.com/security_response/writeup.jsp?docid=2001-011713-2000-99&tabid=2") . However, I could have prevented this infection by keeping my system up to date. I have also had my systems comprimised once, again because I was running a version of ssh that had a known security hole ( that has since been fixed). The key here is that as long as you keep your system up to date you should be relitively secure. 

HOWEVER, **my experience with windoze has yeilded hundreds if not thousands of viruses on my systems** and others (mostly on others systems). I use [Anti-Vir]("http://www.free-av.com/") on what win systems i do run it stops most of them. But, most frustrating is that in windoze and can be downright hard to find, track and kill viruses that are not caught by anti-virus software. Mostly because windoze keeps very little logs and even what logs it keeps are not clear and consice as to what happened.

You can't really run AVG or any other anti-virus software made for windoze. But, you don't really need to either.

The easiest way to avoid viruses, worms, hacks or any other malicious software from running is to keep your system up to date. Then use tripwire to track system changes. iptables for firewall rule filters. Which will block any ports that don't need to be accessed from the world.

Same Here... Last December I Had To Format My HDD And Reinstall XP (i saved some of my documents). There were lots of viruses on it, but the one that destroyed my computer probably could have been prevented (or prolonged) with updates (and i was running McAffe or whatever its called, its crap). But I have had many many MANY viruses on Windows (98 and XP).

---

### Post by asmoore82 on 2007-08-29
> **ts51 said:**
> Personally, I believe If you are using Ubuntu, Mac OS, or any other linux/unix OS, you'd be wasting your computer and time and possibly money with virus scans and firewalls.

good call **except** for *Mac OS X*.

I've heard there are a few dubious creations that can run a muck on Macs
particularly because the all-in-one solutions (iMacs/eMacs) are so very hardware near,
with CRT/LCD controls and Open Firmware controls in Software...
you can imagine the damage.

---

### Post by KCPokes on 2007-08-29
> **redfox1160 said:**
> thanks! Also, if i plug my computer into my router, would i need to install any software or anything (wired router). Im using Verizon DSL...

Assuming you haven't configured your network incorrectly (assigning a static IP that isn't possible, for example), you should be good to go without any additional software.

---

### Post by dewcansam on 2007-08-29
I should also add that since moving to ubuntu even just a week ago. I am thoroughly enjoyed with it. It is so much easier that trying to get what rpm's are out there. Or even trying to get the latest version and compile it with errors and trying to figure out what went wrong.

Just a simple ```
sudo apt-get upgrade
``` keeps your system up to date. Also with iptables already installed and already set-up. NOTHING could be easier. Just sit back and enjoy your system.

---

### Post by dansco on 2007-08-29
although linux is very secure and not prone to virus's(or viri) what i have read is if you network with windoze boxes that may not have an AV it will stop a potential virus spreading to them.

---

### Post by str8line on 2007-09-06
All current Verizon Modems have a built in Firewall that is turned off by default and nearly all routers from all manufacturers also have a built in Firewall.  I prefer to use the hardware option and then open the ports that I want within the Graphical User Interface (GUI) of the modem/router much the same way you would in a software firewall.

This takes the onus from each PC needing to run additional software and blocks the threats before they get to the PC.

---

### Post by dewcansam on 2007-09-13
Update: I saw somewhere that AVG **IS** avialable for linux. So check it out here [AVG Anti-Virus Free Edition 7.5 for Linuxl]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl")

---

### Post by bodhi.zazen on 2007-09-13
[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

