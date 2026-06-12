---
title: "Can I install Edgy on my G3?"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by milkwood on 2006-10-27
I read this ubuntu's home

Ubuntu is suitable for both desktop and server use. The current Ubuntu release supports PC (Intel x86), 64-bit PC (AMD64), Sun UltraSPARC and T1 (Sun Fire T1000 and T2000), _PowerPC (Apple iBook, Powerbook, G4 and G5) and OpenPower (Power5) architectures._

Can I not install Edgy?
And Deos Edgy for ppc have Firefox 2.0?

---

### Post by Peter76 on 2006-10-27
as long as you have a new world g3, running ubuntu shouldn't be a problem.
And yes, edgy has firefox 2.0.
Good luck installing...

---

### Post by cmorgan47 on 2006-10-27
my g3 500mhz uBook is just finishing the upgrade process right now.  dapper* felt like it was meant to run on it--other than the damn ATI issue--and i have no reason to believe edgy will be any different.

will report back when it finishes up.

*i did switch to xfce rather than gnome which makes it feel much quicker

---

### Post by cmorgan47 on 2006-10-27
spoke too soon.

after rebooting into edgy everything appears to go well, then x won't start and i get an "your x server is probably not configured error."

off to figure it out, unless anyone has advice:

ibook g3, 500mhz, mobility M3 agp 2x

---

### Post by Peter76 on 2006-10-27
@cmorgan47: Had the same trouble; turned out xserver-xorg wasn't installed anymore...

sudo aptitude install xserver-xorg

solved it

---

### Post by cmorgan47 on 2006-10-27
yep, just found that out as well.
unfortunately, i'm not anywhere that i can use the info.  have to wait till 5.

incidentally, and way off topic, what's the difference between apt-get and aptitude?

---

### Post by milkwood on 2006-10-27
Thanks for a lot!;) 
Mine is "new world" iMac DV Grape.
I'm using macos9 as TV and dapper as PC.
I like,of course,new thing.
But I had many trouble when install dapper on my mac.
I had to install over again many times.
But this why is not completing burning CD.
I'm not good at computer's things as well as my English.
So I don't want to handle many difficulty.
Anyway I'll give it a try in a littele while.
If I've finished upgrading then I would get back here again to report my condition.
Thanks for your opinions.I hope more growth of ubuntu's world.
Thanks:mrgreen:

---

### Post by milkwood on 2006-10-27
I did a try gksu "update-management" -c.
and this warnings turned up  

warn("apt API not stable yet", FutureWarning)

What is this meaning?
Will I better not to upgrade to Edgy?

---

