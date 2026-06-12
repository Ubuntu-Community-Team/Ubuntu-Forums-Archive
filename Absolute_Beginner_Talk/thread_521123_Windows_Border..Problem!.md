---
title: "Windows Border..Problem!"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-09
I am having a strange prob.. whenever I install a theme everything changes except Windows Border :( Earlier there were no such issues with Ubuntu :( Plz help .. In windows border the border itself did not get installed .. I had tried many theme but same problem :(

Regards

---

### Post by haricharan on 2007-08-09
do you have desktop effects or beryl installed by any chance??

---

### Post by Dark Star on 2007-08-09
> **haricharan said:**
> do you have desktop effects or beryl installed by any chance??
No :( Nothing just a fresh install of Ubuntu after open Suse :confused:

---

### Post by bobby_d on 2008-01-30
Hi there, 

Had the exact same problem, Ubuntu 6.06.2 Dapper persistent from USB.. First of all, I read somewhere (can't remember where) that I should have an ~/.xinitrc, which I didn't have, so I created it and put in 

gnome-settings-daemon &
exec gnome-session

Restarted, tried Themes again, same problem.. But then, I placed a launcher for Preferences/Theme on the desktop, and added a gksudo in front of its command.. Now if this is run, first you get a complaint 

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. ...."

but then it is run - if you click now through the themes - *only* the border changes, and nothing else :) Haven't yet seen if it persists .... I don't know if the .xinitrc and the gksudo thing are related, but hope it helps..

---

