---
title: "Chinese invasion"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by dolphinboy on 2007-03-07
[FONT="Arial Black"][SIZE="2"]:confused: :confused: :confused: [/SIZE][/FONT]
A puzzlement: recently, when i access a file that was saved to local folders or ANY of my saved files, THEY ALL COME BACK IN CHINESE SCRIPT...now, they didn't go in that way, so what the hell is going on? is it a virus? Did the Chinese banks buy my desktop, or what? This is very frustrating!

---

### Post by dolphinboy on 2007-03-07
:confused: :mad: :confused: lately when i access a savedfolder or a file from ANY place, i get back chinese script! What happened and how do i fix it...PLEASE HELP, I CAN'T FUNCTION...it's like all my memory is in a differnt language that i don't read!

---

### Post by bapoumba on 2007-03-07
Threads merged.

---

### Post by dolphinboy on 2007-03-07
I don't understand french either...what the heck is going on? My question about chinese script was serious

---

### Post by bapoumba on 2007-03-07
> **dolphinboy said:**
> I don't understand french either...what the heck is going on? My question about chinese script was serious
Well, I did take it seriously, but I'm not sure I can help you. 
What kind of file is it ?

---

### Post by dolphinboy on 2007-03-07
hey, sorry for bein' testy...but it's ALL my saved files, in local folders or saved to disc...when retrieved...chinese! It just started happening out of the blue...

---

### Post by bapoumba on 2007-03-07
Make up a new user, say "temp" ```
sudo adduser temp
```
see **man adduser**.
Logout of your session and log back into the "temp" session. Do you have the same problem ?

---

### Post by dolphinboy on 2007-03-07
I'm not sure i understand but i'll try it, thanks

---

### Post by bapoumba on 2007-03-07
> **dolphinboy said:**
> I'm not sure i understand but i'll try it, thanks
If this is something to do with your regular user config files, then a new user, having the default config files should be okay.
If not, we'll have to look into your precise files (the ones that mess up), but I'm not sure where to start, in that case ...

---

### Post by dolphinboy on 2007-03-07
Thanks, bapoumba, for tryin' but i'm lost when i go to the terminal/command line stuff...i'll have to get my son to try when he's not busy...peace be with you, friend

---

### Post by bapoumba on 2007-03-07
Open a terminal and run:
```
sudo adduser temp
```
for a temporary user (you can choose what you want here instead of "temp").
When prompted, give your user password (nothing will appear on the screen, it's normal).

Then leave blank all the questions but give a password. Then logout, and log back in the "temp" user session (or whatever you called it), give the password you just set up, and browse your files.
If the files are okay, then I have a couple of ideas ;)

---

