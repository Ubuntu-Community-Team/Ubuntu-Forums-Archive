---
title: "Help!! gnome panel don't work"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-03
I removed something I shouldn't of via packet manager but I dunno what it is!! ](*,) ](*,) ](*,) ](*,) :confused: 

Now my panel don't work. I also tried logging in as root using "root" and "same pw as my username" and that didn't work (at login screen) seems I can't login as root.

Also, before my startbar stopped working, when I went to shut down, I couldn't, I could only hibernate or suspend..

Plssssss help!! :( :(

---

### Post by linuxbun on 2006-12-03
I've accessed firefox by right clicking, creating a launcher (gnome-terminal) and by launching firefox from terminal.

Whats the cmd to launch packet manager? Tried a few things, can't get it up!!:confused: :( :(

---

### Post by noneofthem on 2006-12-03
When you are logged in try this:

1. Right-click anywhere on the desktop and select "new terminal"
2. Type "killall gnome-panel"
3. Repeat step 2 until you get a response like "process doesn't exist" or similar
4. Now type "gnome-panel" and you should be back to normal

Hope that helps...

Amir

---

### Post by linuxbun on 2006-12-03
It does, ty :mrgreen: :mrgreen: :mrgreen:

---

### Post by noneofthem on 2006-12-03
You are welcome... Next time you will help me. ;-)

---

