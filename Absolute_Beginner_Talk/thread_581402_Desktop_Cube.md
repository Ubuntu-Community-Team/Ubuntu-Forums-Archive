---
title: "Desktop Cube"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by RobotAlligator on 2007-10-19
I enabled the desktop cube with compiz fusion, but its not a cube.  its only two sided, and I can't figure out how to make it become four sided

I know i'm missing something obvious, so anyone know whatsup?

---

### Post by jdawson on 2007-10-19
Increase your number of workspaces to four, I trust I don't need to explain why or the number of sides to a cube :)

---

### Post by techno-mole on 2007-10-19
go to system - preferences and select "advanced desktop effects" or "compiz config settings manager" (if you have them installed) then under general options click the tab that says desktop size and change the horizontal virtual size 2 4 and that should do it.
it may be the case that you dont have either of those under system - preferences, for some reason the settings manager doesnt get installed in gutsy by default, i have no idea why though.
if you are running gutsy and dont have the options i mentioned you will need to install the settings manager.
i dont know how else you can change the desktop size, but i would recommend installing the settings manager anyway as it gives you alot more options.
cheers

---

### Post by Duck2006 on 2007-10-19
Or go to the work spaces and right click on them and go to preferences and click on that and a box will come up, change the number of work spaces in there.

---

### Post by andrewsomething on 2007-10-19
Right click on your workspace switcher on the Gnome Panel. Select preferences. Change columns to 4.

---

### Post by nhioi on 2007-10-19
silly question: but can i play with the cube when im in livecd mode?

---

### Post by andrewsomething on 2007-10-19
> **nhioi said:**
> silly question: but can i play with the cube when im in livecd mode?

It's possible if your drivers were detected correctly or if you install the restricted drivers, but things will be pretty slow and choppy unless you have have LOTS of RAM.

---

### Post by digital_exhaust on 2007-10-19
> **andrewsomething said:**
> It's possible if your drivers were detected correctly or if you install the restricted drivers, but things will be pretty slow and choppy unless you have have LOTS of RAM.

Is it possible to install restricted drivers during a live session? I thought a restart was required in order for the restricted drivers to completely install??

I could be wrong here, just curious....

---

### Post by Hospadar on 2007-10-19
you don't need to restart the machine, just the x server, which can be done without shutting down the machine.  either from a text terminal (ctrl-alt-f1) "sudo /etc/init.d/gdm restart" or just do a ctrl-alt-backspace

---

### Post by digital_exhaust on 2007-10-19
> **Hospadar said:**
> you don't need to restart the machine, just the x server, which can be done without shutting down the machine.  either from a text terminal (ctrl-alt-f1) "sudo /etc/init.d/gdm restart" or just do a ctrl-alt-backspace

Thank you... that really helps:)

---

### Post by utkjamie on 2007-10-20
I'm having a strange problem with the desktop cube under Kubuntu. Here's what I've got:

The Compiz settings are:
```
Desktop size: 4
Vertical size: 1
Number of desktops: 1
```

The cube works great, but my taskbar desktop pager shows only 1 desktop. If I increase the pager to 4 desktops, then 16 show up on the taskbar. If I then go back and change the pager to only 1 desktop then 4 desktops show up -- which is what should have been there initially.

Is this a bug or am I missing something?

Also...is there a way to set a different background image for each of the four desktops on the cube?

---

### Post by PogMoThoin on 2007-10-20
Hey, got compiz working, but how do i enable it to have a small cube like i saw in the beryl vids on youtube. Atm its just a rotating desktop

---

