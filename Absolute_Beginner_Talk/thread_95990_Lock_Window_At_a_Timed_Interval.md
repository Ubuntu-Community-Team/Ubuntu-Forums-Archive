---
title: "Lock Window At a Timed Interval?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by mrgnash on 2005-11-27
Is there a way to set the system to lock after a certain amount of time and require an administrator password to reactivate?

Thanks in advance.

---

### Post by az on 2005-11-27
In the advanced screensaver settings, you tell your screen to power off after a certain interval.  The screen is locked and you need to enter your password to get back in.

---

### Post by mrgnash on 2005-11-28
Thanks, but not really what I'm looking for... I don't want it to look after inactivity, but rather lock after a period of time no matter what (unless I, the admin, disable it of course ;) )

---

### Post by patrick295767 on 2005-11-28
[QUOTE=mrgnash]Is there a way to set the system to lock after a certain amount of time and require an administrator password to reactivate?

Thanks in advance.[/QUOTE]
  
I tried the function :
at 19:00 [option] script
  
with script : /etc/init.d/gdm stop
  
that's working but on the other hand:
the worst is the bug of ubuntu
if u do it, the ubuntu got frozen (sometimes)
  
bug bug !
and only a cold reset can sometimes help
sometimes alt ctrl backspace do so...
  
This way is not the right one; i tried ... 
 
very interesting post !!!
  
thank you !

---

### Post by patrick295767 on 2005-11-28
And to lock the gdm at specific time; I recall i already saw that 
it's possible to exit the gdm and replace it by a window saying :
PC IS LOCKED, enter the root passwd to unlock 
  
....
possible yes but how ... i dont really know .. 
they were expert in informatic who did that ... 
  
Good courage !

at => to set a script
atq => to view job list
atrm => to remove jobs

---

### Post by patrick295767 on 2005-12-21
```
apt-get -f install kcron
```
  
And you can easily set up alll you want and needs with this Kcron!!
  
Enjoy, Buffy !

Pat'

---

