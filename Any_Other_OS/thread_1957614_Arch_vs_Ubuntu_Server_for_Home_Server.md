---
title: "Arch vs Ubuntu Server for Home Server"
date: 2012-04-12
forum: Any Other OS
---

### Post by b2zeldafreak on 2012-04-12
What do you guys recommend?

I've had both installed on my Home Server, and I've had problems on both. 

Arch is currently going through some weird conflicts whenever I try to install software or upgrade Pacman. Arch is a fast boot and instant response to SSH requests.

Ubuntu Server (10.04) works, but is much much slower booting, and responding to initial SSH requests and log-ins.


I primarily use the machine headless, but I did have a DE availble in my Arch install. 

Would you guys recommend Ubuntu 12.04 for the server, or just reinstalling Arch?

---

### Post by CharlesA on 2012-04-12
Use whatever works best.

I've been running 10.04.4 for a while and it's been rock solid - SSH response is good, but I haven't blocked outbound traffic in ip tables. From what I remember, if you block outbound traffic, sshd takes a while to prompt for a login/log you in because it's trying to do a reverse DNS lookup of your IP (or something like that).

---

### Post by roelforg on 2012-04-12
My home server runs 11.10 server
Want a gui? LXDE+xinit (no lxdm, just log in to the console and run startx)
Ssh? Some things are just what they are, no os is perfect.
Boot? 2 min on my 256meg ram p4 server.

Never used arch, but here are my 2 cents ^

But like charlesa said: Use whatever works best.

---

### Post by CharlesA on 2012-04-12
Heh, I think the boot time on my home server - i7 3.xx 16GB of RAM and 500GB HDD is around 2 minutes - most of that is POST + RAID card stuff.

EDIT: Maybe I should break down and do a bootchart and see what happens.

---

### Post by snowpine on 2012-04-12
Arch is arguably one of the worst server distros due to its "rolling release" cycle.

I wouldn't worry too much about the boot time (how often do you reboot a server?) but the SSH issue is intriguing.

---

### Post by CharlesA on 2012-04-12
> **snowpine said:**
> Arch is arguably one of the worst server distros due to its "rolling release" cycle.

I wouldn't worry too much about the boot time (how often do you reboot a server?) but the SSH issue is intriguing.
That's what I was thinking as well. I'd go with something like CentOS or Debian/Ubuntu personally.

---

### Post by roelforg on 2012-04-12
> **CharlesA said:**
> That's what I was thinking as well. I'd go with something like CentOS or Debian/Ubuntu personally.

I like debian style pkgmgmt and ubuntu's huge repos and good community.
The 2min i measured was from when i press the power button to when i can login over ssh.
Ssh is 10s delay, i blame my obsolete (but cheap/free) hw.

---

### Post by bubylou on 2012-04-13
I would not recommend arch for a server. Its bleeding edge style causes it to be more bug and crash prone. Like everyone has said boot time means nothing since your server will most likely be on constantly and your ssh problem is probably an easy fix. Mostly just find a distro that works for you, there are no huge difference between different distros. They are all still Linux.

---

### Post by roelforg on 2012-04-13
> **bubylou said:**
> I would not recommend arch for a server. Its bleeding edge style causes it to be more bug and crash prone. Like everyone has said boot time means nothing since your server will most likely be on constantly and your ssh problem is probably an easy fix. Mostly just find a distro that works for you, there are no huge difference between different distros. They are all still Linux.
 
+1
 
Add 1 afternoon of tinkering to optimize stuff and it all runs smooth (you need to do that on, like, every distro but it's worth it)

---

### Post by smellyman on 2012-04-13
It's your home server.....use anything.
 
Although maybe you don't want the help desk calls and angry users at 2 am....?

---

