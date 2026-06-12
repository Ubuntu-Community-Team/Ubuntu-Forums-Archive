---
title: "Problem with X-server"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by krs on 2006-12-03
I cannot run any program with GUI in terminal

> krs@Krzysiek:/home/krs$ kadu 
Xlib: connection to ":0.0" refused by server 
Xlib: No protocol specified 

kadu: cannot connect to X server :0.0 
krs@Krzysiek:/home/krs$ kate 
Xlib: connection to ":0.0" refused by server 
Xlib: No protocol specified 

kate: cannot connect to X server :0.0 
krs@Krzysiek:/home/krs$ konqueror 
Xlib: connection to ":0.0" refused by server 
Xlib: No protocol specified 

konqueror: cannot connect to X server :0.0

I am not logged as root.
I have modified xorg.conf and commented wacom drivers.
Every program I can run 'normally' (not in console) but I am writing a program with GUI in java and I need to run it in terminal - so I need to solve this problem somehow :( 


I hope I made my problem clear :)

---

### Post by frostie on 2006-12-03
Try adding yourself to the x-server access list:

$ xhost +local:krs

---

### Post by krs on 2006-12-04
I've tried it already but it does no work :( 

> krs@Krzysiek:/home/krs$ xhost +local:krs
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0.0"
krs@Krzysiek:/home/krs$


---

