---
title: "screen freezing"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-10-28
Since upgrading to Gutsy my screen has taken to freezing at regular intervals. The only way out is to turn off the computer by pulling the plug out. Neither keyboard or mouse will operate.
Scroll and Caps Lock leds flash.
Has anyone got any ideas? This is killing Ubuntu for me.

---

### Post by genbuntu on 2007-10-28
go back to fiesty (thats escaping ;) )  or if you can try troubleshooting by finding out how and when does it freeze? BTW does ctrl+alt+bkspace work?

---

### Post by FuturePilot on 2007-10-28
Usually flashing keyboard lights indicate a kernel panic.
I'm not sure what could be causing it though

---

### Post by axamax on 2007-10-28
initially, I thought it was happening when the screensaver cut in. It wouldn't come out of the screensaver. I disabled the the screensaver and it still froze. I have also had it freeze on me in the middle of doing things.  It is very frustrating not being able to leave the computer running. To confuse matters further, the other day it ran all day without a problem!
How would I fix a Kernel Panic, if that is the issue.
I had no problems under Fiesty. How would I go back to Fiesty, It doesn't appear in my grub menu. 

Thanks

---

### Post by axamax on 2007-10-28
Ctrl+alt+backspace doesn't work, nor does anything on the keyboard.

---

### Post by axamax on 2007-10-28
bump

---

### Post by Epper on 2007-10-28
Exactly the same problem here with Ubuntu Gutsy.

Randomly keyboard doesn't seem to do anything, i can move the mouse but the pointer remain always the same and there are no effect on click or on mouse over desktop icons.

However the system is working: during these freeze I can say that the system monitor panel that I've on the gnome bars is refreshing normally and shows that the CPU is not 100% busy.

Adding or removing USB devices works and i can see relative messages on screen. Even toggling AC power (it's a laptop) show me the right message.

So, in these situations, everything works except from the keyboard and the mouse events.

The only way to get back controls is to shutdown my notebook.

Tips?

---

### Post by Epper on 2007-10-28
Wowowowo...

It's just happend again: i was talking with a friend using skype, the same freeze happen and, while nothing respond on keyboard or mouse events, i was able to continue talking with my friend! So skype was working... Seem that only keyboard and mouse controls are somehow "disabled" ! :|

---

### Post by Crafty Kisses on 2007-10-28
> **axamax said:**
> Since upgrading to Gutsy my screen has taken to freezing at regular intervals. The only way out is to turn off the computer by pulling the plug out. Neither keyboard or mouse will operate.
Scroll and Caps Lock leds flash.
Has anyone got any ideas? This is killing Ubuntu for me.

Have you seen if anything is taking up a lot of resources, I know that **trackerd** takes up a lot. You can see what is taking up resources by going into terminal and doing the following:
```
top
```

---

### Post by icechen1 on 2007-10-28
try alt+sysrq and R E I S U B it is a emergency reboot key in linux.
I have this problem too but it fixes by disabling some compiz-fusion plugins.

---

### Post by Epper on 2007-10-28
> **Codename said:**
> Have you seen if anything is taking up a lot of resources, I know that **trackerd** takes up a lot. You can see what is taking up resources by going into terminal and doing the following:
```
top
```
If he has the same problem of mine (and it seems so) the system doesn't respond on keyboard and mouse events so it's impossible to open a shell and to lunch top...
Event CTRL+ALT+F1,2,3.. doesn't work. :(

Anyway about the resource, i can say that the CPU is working normally and is used less than 5%... I can say this because i've the system monitor panel on gnome bars that shows the cpu graph... It refresh normally.

---

### Post by icechen1 on 2007-10-28
> **Epper said:**
> If he has the same problem of mine (and it seems so) the system doesn't respond on keyboard and mouse events so it's impossible to open a shell and to lunch top...
Event CTRL+ALT+F1,2,3.. doesn't work. :(

Anyway about the resource, i can say that the CPU is working normally and is used less than 5%... I can say this because i've the system monitor panel on gnome bars that shows the cpu graph... It refresh normally.

Do you have compiz-fusion enabled?
Can you do alt+sysrq then REISUB buttons (it reboots the system) when freezed?

---

### Post by Epper on 2007-10-28
> **icechen1 said:**
> Do you have compiz-fusion enabled?
Can you do alt+sysrq then REISUB buttons (it reboots the system) when freezed?
Yes, I had compiz-fusion enabled.

I've done alt+sysrq + reisub and yes, i've get back to the shell.
Then doing CTRL + ALT + F1 and logging in i've restarted the GUI with startx.

Now i've disabled compiz-fusion... Do you think that compiz could be the problem?

---

### Post by icechen1 on 2007-10-28
> **Epper said:**
> Yes, I had compiz-fusion enabled.

I've done alt+sysrq + reisub and yes, i've get back to the shell.
Then doing CTRL + ALT + F1 and logging in i've restarted the GUI with startx.

Now i've disabled compiz-fusion... Do you think that compiz could be the problem?

i haven't gotten frozen for 2 days since i disabled some compiz-fusion plugins so i think so.

---

### Post by Epper on 2007-10-28
> **icechen1 said:**
> i haven't gotten frozen for 2 days since i disabled some compiz-fusion plugins so i think so.
Thanks very much ;)

I'll check if disabling it solve the problem... If so i'll try to disable some plugins...
Do you remember which one you disabled?

---

### Post by icechen1 on 2007-10-28
> **Epper said:**
> Thanks very much ;)

I'll check if disabling it solve the problem... If so i'll try to disable some plugins...
Do you remember which one you disabled?

cube plugins(cube caps,cube reflect,etc(every plugins with cube in it)),reflect,window preview,water plugin,draw fire on the screen,blur,screenshot,grpup tab,application swicher,ring swicher,fade to desktop.
or just use extra option in apparances.

---

### Post by axamax on 2007-10-29
sorry< THIS TOOK OFF WHILE I was away from the pc. 
Can't use REISUB. I don't know if compiz is enabled. How would I find out?
How would I disable the plug ins? Where would I find them?

Thanks

---

### Post by axamax on 2007-11-11
bump

---

### Post by kbozen on 2007-11-14
I had the same problem

for me disabling tracker (tracker search tool) solved it

 I disabled  indexing services (System > Preferences > Indexing)

and uncheck Tracker  (System> Preferences> Sessions)

after a restart no more freezes

---

### Post by chiefbearclaw on 2007-11-14
I sometimes get something similar.. resulting in a hard reset in LinuxMint XFCE Beta 008 (gutsy). For me, If I exit or kill the updater process I can leave the machine on all day with no freeze. Just throwing that one out there.. there are a million reasons a machine could freeze. :P

---

### Post by kbozen on 2007-11-29
sorry, but I had random freezes also after disabling indexes services etc.
I formated and reinstalled gutsy from cd, but nothing, I have still
the freezes  like described in this post [http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)


 AMD 2600+, ATI radeon 9200 SE

---

### Post by eolson on 2007-11-29
One other thing that can cause a system freeze is a bad memory stick.  Do a memory check and if should hang when it hits the bad spot.  To confirm it was the bad memory causing the hang, write down the info and run the memory check again.  It should hang in the same place or very close to it,

---

### Post by dragonflyseven on 2007-12-08
I am having a similar problem, only when the screensaver kicks in. I recently updated compiz and added some new plugins like the snow one.

---

### Post by nikolas68 on 2007-12-13
recently i enabled in compiz the reflection effect and the system was freezing 2/3 times a day!!! now (it's off) and it's back to normal...

---

