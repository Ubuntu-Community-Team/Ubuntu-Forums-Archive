---
title: "How much ram is in my )@%^ computer ?!?!?!"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by enopepsoo on 2006-08-15
can I type something on sonsole to find out?

thanks, all.:KS :KS :KS :KS :KS

---

### Post by Klaidas on 2006-08-15
You could go to BIOS, this info should be there.
As for checking it on Ubuntu, well, good question, I don't know :/

---

### Post by calx on 2006-08-15
```
free
```

> **enopepsoo said:**
> can I type something on sonsole to find out?

thanks, all.:KS :KS :KS :KS :KS

---

### Post by enopepsoo on 2006-08-15
wow 512MB!:rolleyes: 

That's Twice as much as there was when I went to sleep last night!  I sure hope it keeps doubling every night!  Within a month I will have more memory than god!:---) :---) :---) :---) 

p.s. culture is great!:-({|= :-({|= :-({|=

---

### Post by enopepsoo on 2006-08-15
p.s. I tried to check my bios but the monitor did not turn on before it got to my grub portion.  I did not feel like restarting.

Now, time for a bit more orchestra! :-({|= :-({|= :-({|= :-({|= :-({|=

---

### Post by it.henrik on 2006-08-15
what is this culture you guys are mentioning? some cool app?

---

### Post by Darkriser on 2006-08-15
Try typing "free". Thic command displays information about free and used memory on the system.

---

### Post by NZ-Wanderer on 2006-08-15
Just poking my nose into this thread for a minute if I may...

Can we take this a little further and ask is there a way to display  your system information in Ubuntu (you know, like system information on Windows) :) :)

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

---

### Post by chalex on 2006-08-16
```
free
``` is a neat little utility that will present the memory information for you.  You can get the raw data by looking in /proc/meminfo
```
cat /proc/meminfo
```

You probably want to type ```
free -m
``` to display the information in megabytes.  To find out more about free:```
man free
```
> **NZ-Wanderer said:**
> Just poking my nose into this thread for a minute if I may...

Can we take this a little further and ask is there a way to display  your system information in Ubuntu (you know, like system information on Windows) :) :)

What sort of system information are you looking for?  You could check ```
cat /proc/cpuinfo
``` or ```
lspci
``` or ```
lspci -v
```  Or you could go to System->Administration->Device Manager, which will display the same information.

---

### Post by NZ-Wanderer on 2006-08-16
ahh many thanks, that's exactly what I was looking for :) :)

---

