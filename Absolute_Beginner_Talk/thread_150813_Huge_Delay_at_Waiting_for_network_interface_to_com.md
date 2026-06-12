---
title: "Huge Delay at Waiting for network interface to come up"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-26
When I boot with my ethernet cord in it takes about 10 seconds until it moves from "waiting for network interface to come up," to the next thing. When I don't have it in, since I am on a laptop, it takes over 40 seconds. Would Initng help ?

---

### Post by bluevoodoo1 on 2006-03-26
I think there's a way to skip over an event. I remember reading something around here and I think it's Ctrl+c. I'm not entirely sure, but if that's not it, I'm sure there's a way to skip over something that's taking a while to load.

---

### Post by xXx 0wn3d xXx on 2006-03-26
[QUOTE=bluevoodoo1]I think there's a way to skip over an event. I remember reading something around here and I think it's Ctrl+c. I'm not entirely sure, but if that's not it, I'm sure there's a way to skip over something that's taking a while to load.[/QUOTE]
ok, is there a way to possibly lower the delay ?

---

### Post by xXx 0wn3d xXx on 2006-03-26
[QUOTE=MasterChief1234]ok, is there a way to possibly lower the delay ?[/QUOTE]
I think I found a solution...let's see if it worked.

---

### Post by xXx 0wn3d xXx on 2006-03-26
Does anyone know how to stop my network from auto starting (Like at boot) ? I got Ubuntu to connect to my network if while I am using ubuntu, I plugin my ethernet cord.

---

### Post by deathbyswiftwind on 2006-03-26
open a terminal and enter

sudo apt-get install bum

then in the terminal enter

sudo bum

uncheck the one labeled as hotplug-net

then apply changes

I personally took off hp printing,powerdnow,cups and a few other things and my boot time is super fast

---

### Post by xXx 0wn3d xXx on 2006-03-26
I don't have the option under bum. I also tried svf-conf (sp?) and when I disabled it freezes at Configuring Network Interfaces.

---

### Post by nanotube on 2006-03-26
if you want it to not bring up ethernet on boot, just comment out the line "auto eth0" in /etc/network/interfaces 
of course, that means you will then have to bring it up manually.
the simplest way is to just hit <ctrl><c> when it gets to "configuring network interfaces". :)

---

### Post by bluevoodoo1 on 2006-03-26
[QUOTE=nanotube]the simplest way is to just hit <ctrl><c> when it gets to "configuring network interfaces". :)[/QUOTE]

That's what I was thinking in my earlier post.

---

### Post by nanotube on 2006-03-27
[QUOTE=bluevoodoo1]That's what I was thinking in my earlier post.[/QUOTE]

yep, good thinking, blue. :)

---

