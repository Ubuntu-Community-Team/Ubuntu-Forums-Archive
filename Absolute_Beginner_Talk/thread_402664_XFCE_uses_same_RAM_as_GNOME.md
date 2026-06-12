---
title: "XFCE uses same RAM as GNOME"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-04-06
I dont know if this is an absolute beginners question, but I am pretty much an absolute beginner to XFCE (I know GNOME alot better).

For some reason, whenever I control alt backspace and login to the XFCE interface, my system monitor shows almost exactly the same RAM usage.. GNOME runs at idle after bootup about 109MB, whereas XFCE is like 104MB. Considering that XFCE is supposed to be lightweight and all, it surprises me that it pretty much uses the same system resources as GNOME. Any info or advice?

Never resolved on a prior post is why my wireless works on GNOME but not XFCE, if any of you got any thoughts on it...

---

### Post by makz on 2007-04-06
Linux always uses the maximum possible RAM and that's a good thing, why do you want to have lots of RAM if your OS doesn't use it?

What is that RAM used for? Linux uses disk cache, it copies the most used blocks of the disk to RAM so programs can run faster. If you load another program it simply unloads the necesary cached blocks to make the program fit in RAM.

---

### Post by GSF1200S on 2007-04-06
> **makz said:**
> Linux always uses the maximum possible RAM and that's a good thing, why do you want to have lots of RAM if your OS doesn't use it?

What is that RAM used for? Linux uses disk cache, it copies the most used blocks of the disk to RAM so programs can run faster. If you load another program it simply unloads the necesary cached blocks to make the program fit in RAM.

Ohhhh... so XFCE would be lighter if it NEEDED TO BE.. I see. I was under the impression that each interface would use a specific amount of RAM based on how involved the details, controls, etc were.. Thanks for the info, I didnt know Linux did that. It doesnt really matter as I have 2GB on this machine, but I was just curious...

---

### Post by aysiu on 2007-04-06
More details [here](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

---

### Post by GSF1200S on 2007-04-06
> **aysiu said:**
> More details [here](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

Not bad.. I wondered how an application took longer the first time and then would open much faster the next time that I open it.

Windows seems to do this for certain things too, but I usually notice more and more processes building up. Another words, while linux caches info on RAM, windows actively loads a program partially in the event that it needs to be loaded again.. A perfect example of this is MS Office or IE7 where part of the application is loaded at bootup. Am I right in how I perceive this?

Thanks though.. thats good stuff.. You know, I really knew very about Linux when I started, and I chose Ubuntu because of the easy install, the Live CD and the forums.. I didnt realize how well designed the Linux kernel, GNOME and Ubuntu was designed. I will prolly never use another distribution for more than pleasure.

---

### Post by raul_ on 2007-04-06
Err...I'm not sure about that. It depends on how your system monitor is doing it's math..try typing "free" in the terminal and compare the data

My conky monitor, for example, doesn't add the cached memory, just the memory that's being used by programs

---

