---
title: "Notebook battery"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-20
Ok, here's my dilema, i'm a college student, and i switched to ubuntu just before school.... but since being a college student my battery is strongly required... since i put ubuntu on my battery seems to have half of it's life...  so unless there is a solution to this i'm going to switch back to windows for the remainder of my school career...  Well....  hopefully you guys can help, but if not...  thanks anyways...  i will keep you updated to see if i actually went back to the shitty windows or not....

---

### Post by 3rr0r on 2006-09-20
So you're only getting about 1/2 as much juice from your battery as you used to get?  You can try dimming the screen or putting it to hibernate every time  you aren't using it. 

One thing I noticed from my laptop was in windows, when I unplugged it, it automatically dimmed the screen, but in ubuntu it does not.

---

### Post by Metacarpal on 2006-09-20
> **3rr0r said:**
> So you're only getting about 1/2 as much juice from your battery as you used to get?  You can try dimming the screen or putting it to hibernate every time  you aren't using it. 

One thing I noticed from my laptop was in windows, when I unplugged it, it automatically dimmed the screen, but in ubuntu it does not.

If you right-click the battery icon, you can configure your laptop's power usage (separate tabs control the plugged and unplugged settings).  Screen dimming makes a world of difference - I keep mine to around 50% when unplugged.

---

### Post by Devile on 2006-09-20
no no i did all of that... i run it dimmed even with it plugged in... an i'm in class pretty well all day, so it's on all day, and when iw as just word processing with windows i got 5 hours straight out of it without turning it off, now i get aorund 2....  just word processing....

---

### Post by nts on 2006-09-20
5 hours straight...?  :confused: 

On what laptop/battery..?

---

### Post by dasunst3r on 2006-09-20
Ubuntu has never been good when it came to power management on my laptop (Dell Inspiron 6000).  You should consider trying out SUSE.

---

### Post by jordanmthomas on 2006-09-20
I have an i6000 too and I get over 4 hours of battery (I only got 3 and a half in windows)
Try this
```
sudo dpkg-reconfigure gnome-applets
```
and enable the SUID bit for the CPU frequency applet
Then, put the CPU frequency applet on your panel and go to its preferences so you will be able to set the governor for your CPU.

I use ondemand when I am on battery, but if you want hardcore battery life, try powersave.
(I am, of course, assuming you have a scalable CPU)

Before I did this, my processor was running at a high speed more often than it needed.
You can try it and see if it helps

---

### Post by i.be.doh32 on 2006-09-20
I have the same problem too now.  However, when I first started using Ubuntu, it scaled the processor usage based upon how much of a demand I was placing on it.  It would automatically scale to a lower power usage level when I was doing simple stuff like word processing, and to higher levels when I was doing many different things at once.  

I recently updated the kernel to 2.6.15-27 from 2.6.15-26 and ever since I did, it stopped scaling the cpu.  I was in a panic earlier today when my battery was running down to less than an hour of power left until I rebooted into the 2.6.15-26 kernel and everything started working all dandy-like again.  Is there any way to set the 2.6.15-27 kernel to the way the 2.6.15-26 one is?

---

### Post by UltraMathMan on 2006-09-20
I managed to get an extra half hour out of my battery (Inspiron E1505) by changing the powerstate on my ATI X1400 to the lower lever.

 ```
aticonfig --lsp (lists all available power modes)
aticonfig --set-powerstate # (switches the current running mode)
```

---

### Post by tylerjames on 2006-09-20
hmm... yeah i definitely have the same problem
I just bought an Inspiron 6400 with a 9-cell battery
in Windows I can get about 5.5 hours and in Ubuntu I can only get about 3 hours.... pretty dramatic difference, and i do have my screen dimmed quite a bit when unplugged... hopefully some improvements come about in the short run

does anyone know if that ATI X1400 tweak has negative effects on graphical output?

---

### Post by UltraMathMan on 2006-09-21
I haven't noticed anything - but you can't (or at least I couldn't) apply it using XGL. I also turn swap off (with 2GB RAM I rarely tap into it unless I'm running VMware and a ton of other stuff) with ```
sudo swapoff -a
``` I don't know if that does anything though.

---

