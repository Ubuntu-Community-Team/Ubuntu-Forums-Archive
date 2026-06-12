---
title: "system clock not keeping correct time"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by wasp on 2006-04-11
Hi all,

Everytime I start up Ubuntu, the clock is the wrong time. Once I set the clock, it seems to keep time fine...until I start up Ubuntu again. Has anyone else had this, or know what could be causing it?

EDIT: I see other people have had this problem as well. Some possible solutions have already been posted. I'll try those.

---

### Post by wasp on 2006-04-11
Ok, I tried "sudo gedit /etc/default/rcS" , but UTC was set to "no" already, (I thought I remembered doing that during the install) and "tzsetup" doesn't work.

Any other ideas?

---

### Post by Topaz on 2006-04-11
[QUOTE=wasp]Ok, I tried "sudo gedit /etc/default/rcS" , but UTC was set to "no" already, (I thought I remembered doing that during the install) and "tzsetup" doesn't work.

Any other ideas?[/QUOTE]
[COLOR="Green"]Computer battery on main board going bad. [/COLOR]

---

### Post by wasp on 2006-04-11
[QUOTE=Topaz][COLOR="Green"]Computer battery on main board going bad. [/COLOR][/QUOTE]

The thing is though, the clock seems to still keep time. It's just 6 hours off. It seems very much like it's keeping UTC time, except UTC is set to no. Everything else on the computer seems to work ok. (although I'm not sure what would or wouldn't be fine if a battery on the main board was going)

My Windows partition has the exact same problem with the clock.

---

### Post by Topaz on 2006-04-11
[QUOTE=wasp]The thing is though, the clock seems to still keep time. It's just 6 hours off. It seems very much like it's keeping UTC time, except UTC is set to no. Everything else on the computer seems to work ok. (although I'm not sure what would or wouldn't be fine if a battery on the main board was going)

My Windows partition has the exact same problem with the clock.[/QUOTE]

[COLOR="Green"]The only other thing I can think of is you have your time zone set wrong.              [/COLOR]

---

### Post by erniewinner on 2006-04-11
mmm... i've got that problem with a thinkpad t21 laptop. they have a big portable battery and that works fine. do they have an onboard battery also... i wanted the clock to connect and set itself to the correct time on boot up but it doesn't and i have to do it manually.

---

### Post by wasp on 2006-04-11
[QUOTE=Topaz][COLOR="Green"]The only other thing I can think of is you have your time zone set wrong.              [/COLOR][/QUOTE]

No, the time zone is set to the correct one. Another thing is, in the terminal if i type "sudo hwclock -r" it lists the correct time. And if I check the time zone, the right time zone is listed. It's just the display in the taskbar in the top right hand corner that's wrong, it would seem.

This seems like a bizarre problem, I know. Maybe I'm the only one who's experienced it. :confused:

EDIT: I reset the clock while in Windows to the correct time, then booted up Ubuntu. The time stayed right, so maybe whatever the issue was is resolved.  *crosses fingers*

---

