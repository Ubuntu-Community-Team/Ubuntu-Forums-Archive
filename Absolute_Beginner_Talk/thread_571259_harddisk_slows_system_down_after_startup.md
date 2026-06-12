---
title: "harddisk slows system down after startup"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by AlmaTlust on 2007-10-09
Hi,
very often (almost every time), after startup my harddisk starts spinning and the whole system gets very slow. I gues there's some background process using the harddisk, but I don't know. Anyway, it's rather annoying. How can I find out which process is using the harddisk, and whether I could do anything to improve the situation?
My system is Kubuntu Feisty with an older Sony Vaio Laptop (2.GHz processor, 60GB HD, 512 MB RAM)
Thanks in advance for any advice.

---

### Post by Jimmyfj on 2007-10-09
Hi - In a terminal you can type the command "top" This gives some great info.

---

### Post by kerry_s on 2007-10-09
> **AlmaTlust said:**
> Hi,
very often (almost every time), after startup my harddisk starts spinning and the whole system gets very slow. I gues there's some background process using the harddisk, but I don't know. Anyway, it's rather annoying. How can I find out which process is using the harddisk, and whether I could do anything to improve the situation?
My system is Kubuntu Feisty with an older Sony Vaio Laptop (2.GHz processor, 60GB HD, 512 MB RAM)
Thanks in advance for any advice.

it's most likely swapping since you only have 512ram.

---

### Post by AlmaTlust on 2007-10-09
top only shows cpu usage, but not "harddisk usage", right?
I use a monitoring program to see whether there's a lot of swapping going on, but it doesn't seem to...
top shows Kontact using about 11% of cpu, and kded about 4-5%. 
After some time the harddisk stops and then the system gets much more responsive, even with OpenOffice, Scribus and some other programs running together.

---

### Post by Joeb454 on 2007-10-09
As kerry_s said, the system is likely to be swapping due to the RAM.

If it's not that, then are you running any search utility in 'buntu?

Usually these tend to index your drive on startup, although they index less after a while, if your constantly adding files and removing files, then it will index more frequently

---

### Post by AlmaTlust on 2007-10-09
if swapping was the issue, shouldn't it then take place all the time? After a while the harddisk activity stops, so that doesn't seem to be the problem.
I tried pretty much every single desktop search engine available in Ubuntu (beagle, strigi,...), but they all slowed my system down way too much, so I took them off.
Is there a way to look which program is accessing the harddisk at the moment? That would give me a hint...

---

### Post by philinux on 2007-10-09
My system is ancient and no swapping occurs to slow things down.

Re-boot and fire up system monitor from System>Admin.

Check out all the tabs - really useful to see whats going on.

---

### Post by skymera on 2007-10-09
so is no swap good or bad?

sorry to interrupt, but would no or very little swap but lots of RAM be good for performance?

---

### Post by philinux on 2007-10-09
I always thought in windows that when the hard disk light was bashing itself ie system run out of physical memory and it was swapping was very bad for performance.
anyway here's a snap of my sys mon  only things running are network kopete firefox and sysmon and of course ubuntu desktop stuff.

---

### Post by Joeb454 on 2007-10-09
I'm guessing that you might still have a desktop search program still installed somewhere, if not fully then some component from it.

Best bet to find that out would be to try Synaptic and search for search

---

