---
title: "Kubuntu is terribly slow"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by kurishiiu on 2007-05-31
Hi, 
I posted this in the sluggish section but i really need help. I really don't know why but kubuntu is getting horribly slow. It works fine for a couple of hours and then it's almost impossible to do anything on it. 

I will post any info you may need to help solve this problem. I really don't want to reinstall, I just did a couple of weeks ago

My hardware is this

Pentium 4 CPU 3.06 GHZ
Cache size 1024
Memory 512mb
HD 80 Gygas Samsung HDO80Hj
video Integrated Intel 82865G

---

### Post by jamesjtucker on 2007-05-31
The best place to start figuring out what is slowing you down is to use top. Entering the below command into a terminal will generate top information every 10 minutes for an hour and write it to toplog.txt. Take a look at the information it provides, and see if you can see a process that is using a lot of cpu, or memory being eaten up by a specific program. This will give you a better idea as to whats happening here. Here is the command:
 top -b -d 600.00 -n 6 > toplog1.txt & 
Is there any particular program you are using when the slowness occurs?

---

### Post by jamesjtucker on 2007-05-31
Another thing i just thought of... i remember i used to use the automatic wallpaper switcher in kubuntu a while back to swap every so often. I eventually had to turn that off as it would drag my system to a crawl after a few hours. Are you using that feature?

---

### Post by Sparkster185 on 2007-05-31
This was happening to me, too.  It turns out it was SuperKaramba (not all themes, only some of them -- specifically ones that are dynamic like monitors, Liquid Weather, etc.).

It must have something to do with my graphics card/driver and SuperKaramba, because my laptop runs 4-5 dynamic widgets at once and it never idles above 3% CPU.

Try closing SuperKaramba if you're running it, that might help.

---

### Post by pappapump on 2007-05-31
And lets not overlook the obvious.
It may even be the CPU fan slowing down or dying.
If you have a laptop and the bios has a heat monitor that should be compensated for in your os like some of the strange laptops, that may cause it.
It wouldn't hurt to check any background proceses as mentioned above to see if one of your widgets is eating up cpu or ram either.

---

### Post by kurishiiu on 2007-06-01
> **Sparkster185 said:**
> This was happening to me, too.  It turns out it was SuperKaramba (not all themes, only some of them -- specifically ones that are dynamic like monitors, Liquid Weather, etc.).

It must have something to do with my graphics card/driver and SuperKaramba, because my laptop runs 4-5 dynamic widgets at once and it never idles above 3% CPU.

Try closing SuperKaramba if you're running it, that might help.

I have Superkaramba installed but i only had the calendar theme.  I just quit it, I'm lloking for the toplog file, as soon as i find it i'll paste it here.

I don't think is the machine, I got this one in January, but even so I'll check.

Thanks to all

---

### Post by kurishiiu on 2007-06-02
> **Sparkster185 said:**
> This was happening to me, too.  It turns out it was SuperKaramba (not all themes, only some of them -- specifically ones that are dynamic like monitors, Liquid Weather, etc.).

It must have something to do with my graphics card/driver and SuperKaramba, because my laptop runs 4-5 dynamic widgets at once and it never idles above 3% CPU.

Try closing SuperKaramba if you're running it, that might help.

It's not SuperKaramba, it should be something else, i did not find the log. It could be related to firefox and something about the graphics, When I tried to unlock the screen after lunch it was unusable...

I'll keep updatig to see if we find the answer. I think it has something to do with the graphic card or something.

---

### Post by jpgeerets on 2007-06-02
hi folks,

i have the same.
dell latitude D800 laptop. 
1 Gb memory
60Gb harddisk.
nvidia graphic board.

recently re-install ubuntu.
i preserved my /home partition.
the rest is re-installed.

my feelings tell me it is something with nvidia.
during startup of kubuntu, normaly i saw the nvidia splash screen.
at this moment i dont see it.

when i use top, it tells me the system is doing nothing... a lot of noting... :-)

anyone any idea?


thanks!!

Jean-Paul

---

