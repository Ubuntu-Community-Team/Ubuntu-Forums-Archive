---
title: "how to start gnome?"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by dronepower on 2005-12-24
For some reason ubuntu wont boot straight into gnome. the startup sequence is as normal, but when I gotta fill in name / pw it drops back to plain text with no GUI. How can I start gnome?

thanks,

---

### Post by chimera on 2005-12-24
login with your username&password and do "sudo gdm"

---

### Post by odin on 2005-12-26
If you tryed to "sudo gdm" and worked here there is a way so you dont have to do that anymore and GNOME will start every time you boot.

Well there are more methods but I think this is the easiest.

Install the boot up manager

sudo apt-get install bum

then run in Sytem->Administration->Boot up manager (please imagination cause this is translated from spanish) or by just typing in a terminal "sudo bum" 

This is a very good tool for setting what you want to run at boot.Very easy to use.

Hope this helps

---

