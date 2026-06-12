---
title: "[SOLVED] How to make Ubuntu 12hour instead of 24hr."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-20
On the clock prefernces, I only have:

24 hour,
Unix Time,
Internet Time

How do i make it 12 hour??

---

### Post by bamesah on 2007-06-20
I solved it by myself, just changed the session Lang. to English U.S

---

### Post by overdrank on 2007-06-20
> **bamesah said:**
> On the clock prefernces, I only have:

24 hour,
Unix Time,
Internet Time

How do i make it 12 hour??

Hi if you right click on the clock and choose preference and the you can choose 12 hr ;)

---

### Post by FleetAdmiral74 on 2007-06-20
I might as well ask here...why is 24hr the default? I thought most people used the 12hr system...

---

### Post by sailor2001 on 2007-06-20
no.. most of the world uses a 24 hour clock

---

### Post by overdrank on 2007-06-20
> **FleetAdmiral74 said:**
> I might as well ask here...why is 24hr the default? I thought most people used the 12hr system...

Well I cant speak for most but my installation was default 12 hour.:KS

---

### Post by bamesah on 2007-06-20
I solved the prob;em already

---

### Post by drivel on 2007-06-20
try "man date"
it will be helpful

---

### Post by FleetAdmiral74 on 2007-06-20
> **sailor2001 said:**
> no.. most of the world uses a 24 hour clock

For real? I thought military used that. Now I know Americans are pretty stupid, but I seriously did not think civilians from most countries went around normally saying stuff like 17-hundred.

---

### Post by ames89 on 2007-07-16
hello, plz can someone explain how to change it from the terminal? i have no idea, i tried it a lot and cant figure it out :'(

tnx to all the help :-)

---

### Post by freebird54 on 2007-07-16
Nahh - they just refer to 17 hours.  So - dix-sept heures,vingt-trois  (17:23)  :)

"Be back by 18  - Grandma's coming for dinner!"

It also tends to eliminate arriving 12 hours late for your flight - as well as eliminating your excuse after a good night for being late in to work!  Hard to explain mistaking 04:00 for 16:100 when you were to start at 08:00 !!

---

### Post by bodhi.zazen on 2007-07-16
> **ames89 said:**
> hello, plz can someone explain how to change it from the terminal? i have no idea, i tried it a lot and cant figure it out :'(

tnx to all the help :-)

Change what in a terminal exactly ?

The terminal command I use is date

I set this in .bashrc :

alias date='echo -ne "${LIGHTBLUE}";date "+%A %B %d, %Y %l:%M %p %Z"'

*Note Light Bule is defined earlier as : 
LIGHTBLUE='\e[1;34m'

---

### Post by ames89 on 2007-07-16
thank you so much :)
i was confused through that way, thanx :D
change the system clock from 24 to 12 in the normal view

---

