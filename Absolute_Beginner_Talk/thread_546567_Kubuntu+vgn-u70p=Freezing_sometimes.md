---
title: "Kubuntu+vgn-u70p=Freezing sometimes"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by shadowsa on 2007-09-09
during use of the system it freezes and does not react in any kind of ways, the keyboard is dead the mouse is dead, there is no rule when it freezes, its not a thermal or hardware problem i excluded these already, i ran ram test for 3 days, and theremal it cant be for 2 reasons because when i bootup a live cd or boot from an other system this problem does not happen and also when i restart the computer imediately it works again for a while and freezes but mostly it take more time to freeze then previously. beside that i need to say that vgn-u70p is a sony handhelp palmtop like full feature laptop with touchscreen, i installed the evtouch drivers, im not sure if the problem is or can maybe related to this, im actually doubting this but the thing im suspecting is that it is some kind of kernel related.

thank you in advance shadowsa

---

### Post by benerivo on 2007-09-09
I had a very similar problem. After around five minutes, the system would lock totally (the mouse pointer wouldn't move and even number lock on the keyboard was frozen). After a restart it was fine. This was with kde, but it also happened once in gnome. I reinstalled and turned off all power manager features and services and it has been fine since.

---

### Post by shadowsa on 2007-09-09
but dont i need the power management features?

---

### Post by shadowsa on 2007-09-09
i just recognized i have acpid and apmd installes can this couse the problem?
should it be usually either or or both? 

ahh yes powernowd is also installed

---

### Post by benerivo on 2007-09-09
Well i turned off acpid and apmd from the services list (i didn't actually uninstall them from the system - i just unticked them to stop them running). I left powernowd running as i wasn't entirely sure what it does and i didn't want to break anything. You could also go to the power management settings from the preferences and turn off all options there.

---

### Post by shadowsa on 2007-09-10
do i need all those things?
acpid,apmd and  powernowd?
or does my laptop live also without it?

---

### Post by shadowsa on 2007-09-10
oh yes kpowersafe is also installed

---

### Post by shadowsa on 2007-09-10
anybody anything?

---

### Post by benerivo on 2007-09-10
I'm sure you can live without all power management features. I have them all turned off, other than powernowd (i'm not sure this is a power management service) and my system is fine.

Of course my computer never goes in to standyby / sleep / hibernation mode, but i never leave it unattended for long periods where they would be used.

Be sure of the difference between uninstalling something and just having it turned off. I have not uninstalled anything, but have simply stopped the power management services from running at boot. You can add the 'System Guard' applet to your panel to see what process are running at a time when your pc freezes.

---

### Post by shadowsa on 2007-09-11
is there any way to anable some kind of logging system which will automatically log all the kernel errors or whatsoever?
so i cant see what is caousing the problem?

---

### Post by shadowsa on 2007-09-11
even i turned off all those things still freezing

---

### Post by shadowsa on 2007-09-11
no changes

---

### Post by shadowsa on 2007-09-12
anybody anything please help

---

### Post by shadowsa on 2007-09-12
not solved yet

---

### Post by shadowsa on 2007-09-13
just updating before it gets lost

---

### Post by benerivo on 2007-09-13
You may be able to find more info on what causes the freeze, by looking in the logs located in /var/logs but i'm not sure what i would be looking for.

---

