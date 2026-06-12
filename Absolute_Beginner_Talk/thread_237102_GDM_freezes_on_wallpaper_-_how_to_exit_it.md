---
title: "GDM freezes on wallpaper - how to exit it?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by dans0n on 2006-08-15
I start ubuntu and am presented with the yellowish login screen asking for user and password. 

I enter these and the wall paper appears and a loading bar showing loading things like 

"Title Bar" 
"Metacity window manager" 
"The Panel"

Then the bar disappears and I have just my wallpaper and mouse. 

This did use to work - I really don't know what happened.

Question is how do  I get back to a console?
If I press ctrl+alt+backspace GDM simply restarts. Sometimes I can type a few lines on the console but then gdm restarts itself. 

Any help much appreciated!

Daniel

---

### Post by linear on 2006-08-15
Try ctrl-alt-F1; should get you to a shell prompt.

---

### Post by mcneely.mike on 2006-08-15
> **dans0n said:**
> I start ubuntu and am presented with the yellowish login screen asking for user and password. 

I enter these and the wall paper appears and a loading bar showing loading things like 

"Title Bar" 
"Metacity window manager" 
"The Panel"

Then the bar disappears and I have just my wallpaper and mouse. 

This did use to work - I really don't know what happened.

Question is how do  I get back to a console?
If I press ctrl+alt+backspace GDM simply restarts. Sometimes I can type a few lines on the console but then gdm restarts itself. 

Any help much appreciated!

Daniel

log out of your desktop or do the ctrl+alt+backspace
then
press CTRL and hold, then press ALT and hold, then press F2

you will be taken to text mode.  login as yourself and type
    mv .ICEAuthority .ICEAuthority.original
this will keep the original file safe from being over-ridden in case this is not the problem.

then press ctrl+alt+f7 to get back to gdm and log in again.

if it works this time, then it is safe to remove the backup
    rm .ICEAuthority.original

if it doesn't work, type
    mv .ICEAuthority.original .ICEAuthority

hope it helps

---

