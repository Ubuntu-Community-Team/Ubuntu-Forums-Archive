---
title: "Unusual high pitch noise"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-03-26
my monitor makes a high pitched noise ( very high) ... is this due to frequency missconfig?

It does not let me alter in gnome-->preferences --> screen resolution  :confused: 

TIA!

---

### Post by octoberdan on 2007-03-26
If the high pitched noise is in fact due to misconfiguration then it would most likely be caused by an incorrect refresh rate, not resolution. What make/model of monitor do you have? What is your current refresh rate set at? Check your monitors specs. You might also want to try googling this a bit, it's a common problem (both a blessing and curse when trying to find the solution). Good luck and happy geeking

---

### Post by jrlii on 2007-03-27
I'm a beginner with Linux, but monitor squeels ware quite common with old CGA monitors: The squeel was metal parts oscilating in time with the flyback frequency, higher than most (but far from all) people could hear.

I suspect some combination of the resolution and the refresh rate is resulting in some metal part vibrating in time with the flyback.

- John.

---

### Post by johnnyw on 2007-03-27
> **octoberdan said:**
> If the high pitched noise is in fact due to misconfiguration then it would most likely be caused by an incorrect refresh rate, not resolution. What make/model of monitor do you have? What is your current refresh rate set at? Check your monitors specs. You might also want to try googling this a bit, it's a common problem (both a blessing and curse when trying to find the solution). Good luck and happy geeking

viewsonic e70f+sb 

I do not know much about my setup I just made the basic instalaltion :S

I have dapper 6.06

> **jrlii said:**
> I'm a beginner with Linux, but monitor squeels ware quite common with old CGA monitors: The squeel was metal parts oscilating in time with the flyback frequency, higher than most (but far from all) people could hear.

I suspect some combination of the resolution and the refresh rate is resulting in some metal part vibrating in time with the flyback.

- John.



Thanks J, I ve already taken the monitor to the official representative of Viewsonic and they ve said the failure I describe is not presented to them. It must be something of my config then, huh?


J

---

### Post by groeswenphil on 2007-03-27
I had something similar.........but I traced it to a USB hub........which then died.
Phil

---

### Post by johnnyw on 2007-03-28
I have no networking devices around me.. actually I had a d link router but died about days ago and noise persists :S

---

### Post by octoberdan on 2007-03-29
J,

could you please open a console window and enter the command xrandr, then post the result?

---

### Post by hardyn on 2007-03-29
high pitched sqeals are most common from switching power supplies (or other devices with high speed oscillations, wifi, etc)  that are eithe being overloaded, or have failed.

there are switching power supplies in both the PC and the monitor, and possibly a printer.

start putting your ear against things... turn things off and on... im sure it will either be the tower or monitor.

---

