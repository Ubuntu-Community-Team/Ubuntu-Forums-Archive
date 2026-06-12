---
title: "Can't fill in password for super-user"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by McK on 2005-12-12
I wanted to "install" the drivers for my soundcard and gfx card, but when i want to log in as super-user ( using the command 'su' ) it asks for a password

i can't type anything there, all i can do it press enter and get an error :confused: 

anyone knows what my problem is?

---

### Post by luap on 2005-12-12
Type in your password and hit enter.. it'll work.. it doesnt show up when you type something in the password section

---

### Post by McK on 2005-12-12
goddamned, that worked fine
just switched from winxp, you're talking to a complete linux newb :D

---

### Post by qiemem on 2005-12-12
You shouldn't have to log in as a superuser.
You can use:
```
$ sudo [COMMAND]
```
for all your superuser needs (that will have you enter your password. it should work fine.)
Sorry if this is obvious. It is the absolute beginner section :)

I've read over and over that the root acount is disabled by default, this is probably equivilant to saying the superuser account is disabled by default (I don't know, I'm a noob too, I'm just curious...)

---

### Post by qiemem on 2005-12-12
oh heh oops replied while i was typing... hate it when that happens...
wait a sec... i just tried it... su password enter, and it failed. that's why i said what i said. what gives?

---

### Post by McK on 2005-12-12
oh cool, i just installed the ATI drivers and now it won't boot

awesome

---

### Post by ninotob on 2005-12-12
[QUOTE=qiemem]
wait a sec... i just tried it... su password enter, and it failed. that's why i said what i said. what gives?[/QUOTE]

You have to type:

sudo su

then you get a temporary root shell so you don't have to type sudo all the time.  If you type "exit", you'll be dropped back to your user-level shell.

EDIT:  I should say of course, that doing a "sudo su" allows you complete power to entirely hose anything in your system.

---

### Post by qiemem on 2005-12-12
oh cool thanks
ya, at first I thought it was really annoying to have to type sudo all the time, but now I realize how conscious it makes you of security and of exactly what one is doing at all times. Damn, those ubuntu people are so smart...
Sorry for the tangent, MCK.
Won't boot anymore? That blows... uh, I've read about problems with ATI cards, it seems to be a pretty prominent thing, so it shouldn't be to hard to find info on it. Sorry I can't help you with this though :)

---

### Post by psusi on 2005-12-12
You can use sudo -s instead of sudo su if you want to run several commands in a row as root.  Type exit to go back to normal.

---

