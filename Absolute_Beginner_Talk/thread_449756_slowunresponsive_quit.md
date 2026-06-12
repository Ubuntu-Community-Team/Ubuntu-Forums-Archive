---
title: "slow/unresponsive quit"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-20
the quit option has become increasingly slow and unresponsive. Often, I will click the quit icon, and a few minutes later it will appear. Any idea what could be causing this? I have only had ubuntu installed for around a week and did not have this problem until a day or two ago. The only things I have installed have been screenlets and a few programs from synaptic.

---

### Post by wmichaelb on 2007-05-23
jba6511: I had a similar problem with Dapper. What happened is that the behavior changed as I installed more software; it would come and go as I added programs. Right now, everything's working fine. I don't know if this is some even or odd number of packages installed thing, phase of the moon, wolfbane pollen concentration, or ??

The moral of the story is: try installing more software, and see if that fixes it. If nothing else, it's easy and free to try!

---

### Post by jba6511 on 2007-05-23
thanks. like you said it comes and goes. Right now I am having no troubles with my laptop. Having separate issues with a wired connection and the internet on my desktop. Search for my posts if you think you can help.

---

### Post by garystewart on 2007-07-20
Hi,
      Having the same problem. Quit is very slow, almost unresponsive. Takes quite a few minutes to come up. Adding software has not been the solution to the problem. Does anyone have any technical insight and a probable solution?

Thanks!

---

### Post by nowshining on 2007-08-20
i had the same problem after removing some stuff such as compiz plugins just a bit ago lolz.. :( but i don't use compiz or desktop effects so that could be the problem if you used synaptic manager to uninstall thosem well at least compiz...

---

### Post by nowshining on 2007-08-20
well try this as you might have some unneeded dependencies

open up a terminal

type or copy and paste

sudo apt-get -f install

if there is any do  (make sure that nothing critical is in there, the above as ruint me before)

sudo apt-get autoremove

---

### Post by nooblot on 2008-06-27
so...looks like there's no solution in this thread
yeah it is ridiculously slow.

Anyone have a fix ?

thanks

edit: never mind. Solution found : enable "Power Manager"

---

### Post by kylirh on 2008-07-12
> **nooblot said:**
> so...looks like there's no solution in this thread
yeah it is ridiculously slow.

Anyone have a fix ?

thanks

edit: never mind. Solution found : enable "Power Manager"

I had the same problem as everyone else on here: when I went to quit, hardy took a minute or two to present the options.

I fixed it by adding gnome-power-manager to System>Preferences>Session. It actually was already there, but wasn't enabled. (I may have just disabled it or something).

---

