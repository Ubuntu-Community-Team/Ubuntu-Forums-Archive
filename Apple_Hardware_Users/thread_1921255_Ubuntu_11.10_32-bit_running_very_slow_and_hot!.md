---
title: "Ubuntu 11.10 32-bit running very slow and hot!"
date: 2012-02-06
forum: Apple Hardware Users
---

### Post by RadiusClausemai on 2012-02-06
I recently installed Ubuntu 11.10 32-bit on my Macbook Pro 6.2. For the first few days it ran fine, a little hot, but nothing too bad. I watched a movie today and when it finished my machine began running slower than I've ever seen on any computer. The trackpad and Unity Launcher worked fine but anything I did within an application took about a minute to take effect. Also applications became unresponsive for no apparent reason.

I'm new to Ubuntu so it's probably just a noob mistake.

Could it be that I'm running 32-bit? Or, did I not install something?

Thanks for your help!

---

### Post by 2F4U on 2012-02-06
What are your hardware specs? I would suggest that you run top or htop in a terminal to see if any processes are taking up the CPU. Depending on what graphics card you have, there may be the option to install proprietary graphics drivers from nVidia or ATI, which usually have a better power management so that the graphics card stays cooler.

---

### Post by RadiusClausemai on 2012-02-06
Thanks a lot!

I was thinking that might be the problem

lspci in terminal gave me this: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)

I'll head to the nVidia site and see what I can find

---

### Post by MG&amp;TL on 2012-02-06
You probably want to install the drivers from the "additional drivers" dialog, not from the web. :) Easier and simpler.

---

### Post by RadiusClausemai on 2012-02-06
I installed the new driver, it's still a bit hot but a lot better than before. I'll try playing another movie and see what happens.

Thanks a lot!

---

### Post by RadiusClausemai on 2012-02-06
Yeah... it was working fine for about 5 minutes and now it's the same problem...

---

### Post by RadiusClausemai on 2012-02-06
One more thing

Upstart-udev-br is at 100% CPU and my CPU's are at about 25%us and 73%id, the rest are at 0-1%

---

