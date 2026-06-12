---
title: "Lost Both toolbars"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by ukfatboy on 2007-05-22
Greetings to everybody !

My first post and I've managed to break it !

Started as a newbie about a month ago and upto now was loving it .

got fiesty installed on my laptop , ( sony ) and have been getting more and into it.

Got beryl running fine.

Today i decided to play and added xpenguins and added the eyes and fish to the taskbar as applets. Everything ok until I rebooted.

Now when booting I get as far as loading the desktop and the top and bottom bar appear then flicker on and off  for 20 seconds or so and then Im left with the desktop and no bars ie no applications

Any help much appreciated

---

### Post by Sparkster185 on 2007-05-22
That might be an issue with Beryl. I noticed sometimes when Beryl starts up, my taskbar flickers, too.  Just a thought.

---

### Post by siralphred on 2007-05-22
have similar problem, my panels sometimes do not load after a reboot, when i type "gnome-panel" into alt+F2 i get "panel already running" although i dont see it, i usually have to restart ctrl+alt+backspace  and relogin for them to appear, i have searched but cant seem to find a solution,,,would appreciate some help.

---

### Post by ukfatboy on 2007-05-22
OK , thank god I've got my taskbars back !

if its helpful to other people the solution was as follows :-

get to a terminal and

"sudo aptitude purge gnome-panel && sudo aptitude install gnome-panel"

and for good measure

"gconftool-2 --recursive-unset  /apps/panel"


the first i believe wipes current config and reinstalls 

the second sends gnome back to default config.

When I rebooted I got the same thing filckering etc but with a dialogue box saying trouble with a faulty applet did i want to delete ? I was quick and deleted and all my problems solved.

Hope this helps someone !!!

---

### Post by amarphadke on 2007-05-31
Thanks a lot!
I had the same problem after adding xpenguins to the panel. I had Beryl installed but was not using it at this time. I had tried fish and eyes before and they did not break the panel.

---

