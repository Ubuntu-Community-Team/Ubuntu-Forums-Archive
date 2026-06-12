---
title: "LCD Brightness reset.. (Gutsy)"
date: 2007-10-27
forum: Apple Intel Users
---

### Post by letorah on 2007-10-27
I installed Gutsy on my Macbook.
It is a problem  that screen brightness resets(dims down) 
when I execute some program using SDL Library.
Then I have to brighten up manually.

---

### Post by THEDARKNESSHASCOME on 2007-10-27
.

---

### Post by THEDARKNESSHASCOME on 2007-10-27
> **thedarknesshascome said:**
> .

.

---

### Post by THEDARKNESSHASCOME on 2007-10-27
> **thedarknesshascome said:**
> .

.

---

### Post by volanin on 2007-10-27
It's just a guess, but try this:

1. Press ALT + F2 to open the run dialog.
2. Type *gconf-editor* and press ENTER, to open the gnome "registry".
3. Navigate to APPS -> GNOME-POWER-MANAGER -> BACKLIGHT
4. Uncheck the item named *enable*
5. Close the window.

See if that solves your problem.
:)

---

### Post by eterps on 2007-11-20
Worked for me, thanks volanin!

---

### Post by pveith on 2007-11-21
hm. I am having the same behaviour when i start mplayer, which is also SDL based i read. Changing the gconf-key "enabled" did not help. Starting mplayer reduces brightness directly to 0% absolutely independant of any configuration of the "enabled"-key. But for some reason setting "idle_brightness" to 0 did work out... Strange, but worked...

---

### Post by mustang on 2007-11-23
Hi Volanin:

your proposed solution did not fix the problem. Is a restart necessary (not asking because I'm lazy but I have a lot of stuff open ;) )

---

### Post by volanin on 2007-11-23
Well, I don't remember if I needed a reboot or not.
If anything, try also pveith solution above.
And, as a last resort, reboot later!
:)

---

### Post by mustang on 2007-12-08
Doh, even after a restart, nothing worked. Are there any other possible solutions I could try?

---

### Post by mustang on 2008-01-20
*bump* This problem is really annoying. Any help would be really appreciated.

---

### Post by pertheusual on 2008-02-14
Anyone? This is happening to me, and it make writing SDL programs SUPER annoying. 
The Backlight check box was already unchecked when I looked in the config.

Please :(

Per

---

### Post by tacutu on 2008-05-04
+1 here on hardy heron.
funny thing is i didn't have this problem in gutsy...

---

### Post by pp77 on 2008-05-13
+1 here on hardy heron. Tried some scripts with echo 9 > /proc/acpi... in rc.local but the brightness resets as soon as GDM starts.

Solved my problem by installing xbacklight and adding it to startup programs in sessions preferences with "xbacklight -set 100", the value is to anyones taste.

---

