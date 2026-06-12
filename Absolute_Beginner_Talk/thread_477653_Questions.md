---
title: "Questions"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-18
First of all I cant believe there isn't a programs forums; there free aren't they? 

Now I'm looking for a program for converting computer movies to DVD disc that are playable to in todays factory standard DVD players.  (windows winAVI & Nero)

Second I heard there was a program adapter that slipped on to most windows applications to make them run for Linux; any truth to that?

Linux is virus free right?

How do i check on my computer components? IE my:
hard drive usage
RAM
Chip / CPU

Is there something that monitors the temperature of your mother board?

Thanks ;)

---

### Post by rikbrown2k on 2007-06-18
Will answer what I can =)

> **Ssj3_man said:**
> First of all I cant believe there isn't a programs forums; there free aren't they?
[www.getdeb.net](www.getdeb.net) has some nice things on it, hehe.   Otherwise rest of these forums & google & the package manager is your friend ;)

> Second I heard there was a program adapter that slipped on to most windows applications to make them run for Linux; any truth to that?
There's a program called **Wine** which does this: it works with varying success depending on the application in question.  Get it from the package manager, and execute windows programs (or installers, best to install first), by typing **wine <programname>** in the terminal.

> Linux is virus free right? 
Short answer: yes.  Long answer: there have been several "proof of concept" viruses for Linux, but no real viruses. Windows viruses WILL NOT run, and because of the way in which Linux is designed (in terms of security), viruses are unlikely to happen!

> How do i check on my computer components? IE my:
hard drive usage
RAM
Chip / CPU
System > Administration > System Monitor
or System > Preferences > Hardware Information for detailed hardware info.

---

### Post by DBStevens on 2007-06-18
Linux is in itself a program so why would one need a programs forum to talk about programs that run under Linux ;-) ?
 
What kind of computer movie there are probably more media formats than atoms in the universe?  

You must be talking about wine or crossover or (can't remember)

No system is totaly immune, it is just a lot harder to get one to propagate under Linux, and the effects in a properly configured system are contained to the account thet activates the virus.

Drive usage      df
RAM                 free
Chip/CPU        cat /proc/cpuinfo

Yes

---

### Post by Ssj3_man on 2007-06-18
it didn't mater to the team of winAVI & Nero in Windows XP just looking for that killer combo here in  Ubuntu 7.04  - the Feisty Fawn.

---

### Post by DBStevens on 2007-06-18
Then why don't you get Nero for Linux.  It does exist.

I can assure you that it mattered to both winAVI and Nero what the formats were.

something to do with codec licensing etc....

also look up mencoder.

---

