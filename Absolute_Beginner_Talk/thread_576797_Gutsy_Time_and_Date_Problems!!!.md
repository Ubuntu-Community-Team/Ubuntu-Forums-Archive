---
title: "Gutsy Time and Date Problems!!!"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-10-15
I have recently upgraded from feisty to gutsy release candidate.  However, I cannot edit the time and date for some reason.  When I was installing gutsy, there were multiple errors with the tzdata package, I think.  Like, there were problems with multiple files, but they were all in the tzdata package.  Including locales and others.  Now, once in gutsy, I ran update and upgrade, and im pretty sure it installed what I was missing.  Does anyone know what I need to do to edit the time and date?  It is killing me to look up and the time and it is like 7 hours off!!

---

### Post by LowSky on 2007-10-15
I used to get a simular problem in Windows:
You might need to fix the clock time in your BIOS first, if the OS and BIOS times are really off the time cannot be updated.

---

### Post by borovy3488 on 2007-10-15
OK, I'll try that.  But would that make it to where I can't even open the config window?

---

### Post by borovy3488 on 2007-10-15
Tried, but no dice.  Any other suggestions out there???

---

### Post by oilchangeguy on 2007-10-15
> **LowSky said:**
> I used to get a simular problem in Windows:
You might need to fix the clock time in your BIOS first, if the OS and BIOS times are really off the time cannot be updated.

where do you get your information? this couldn't be more wrong. the bios time, or the os time does not matter. changing one, changes the other.and it's not either's fault if the os time zone is wrong. and for the op, this is what you get when you play with beta software. have you tried to right click the clock, and select adjust time and date?

---

### Post by MatthewPlanchard on 2007-10-15
So you can't use adjust date & time from right clicking on the clock?

I would try the terminal commands listed on this website, under sudo if necessary.
[http://linux.about.com/od/linux101/l/blnewbie5_3.htm]("http://linux.about.com/od/linux101/l/blnewbie5_3.htm")

I hope this helps. If not, there might be a way to repair your installation using the ubuntu live or alternate CD's? I'm not sure, I'm really new to this.

---

### Post by MatthewPlanchard on 2007-10-15
I did also just come across this command:


To set the hardware (BIOS) clock from the system (Linux) clock, use the command (as root) setclock

---

### Post by LowSky on 2007-10-15
> **oilchangeguy said:**
> where do you get your information? this couldn't be more wrong. the bios time, or the os time does not matter. changing one, changes the other.and it's not either's fault if the os time zone is wrong. and for the op, this is what you get when you play with beta software. have you tried to right click the clock, and select adjust time and date?


Man somebody woke up cranky... :confused: 
I'm sorry I didn't know of any linux fixes so I thought why not try what worked for me in Windows

As for playing with beta software, I have gutsy running fine for almost two months.

---

