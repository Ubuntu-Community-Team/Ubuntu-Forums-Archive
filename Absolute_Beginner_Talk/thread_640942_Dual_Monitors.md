---
title: "Dual Monitors"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by mopar31898 on 2007-12-14
I am trying to get two monitors working but for some reason they don't want to work just right.  I have a 19 inch dell LCD and a 16 inch CRT.  When I first tried this, i got all the of stuff set up and the resolution set just right but for some reason the CRT was the main monitor and it would not let me use the Dell.  I tried all the configurations.  I kept setting the dell as the primary but it would not work.


Any suggestions?


Thanks

---

### Post by criskat777 on 2007-12-14
If you are on Gutsy 7.10 you should try xrandr its realy simple to use. it's as simple as adding this to your /etc/profile : xrandr --output VGA-0 --mode 1280x1024 
xrandr --output DVI-0 --mode 1280x1024 --above VGA-0    but first run xrandr to id your mon names (DVI-0 and VGA-0) in my case. fell free to change res ect to meet your needs.:popcorn:

---

