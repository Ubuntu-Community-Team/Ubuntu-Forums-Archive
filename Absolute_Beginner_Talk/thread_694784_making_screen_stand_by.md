---
title: "making screen stand by"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by diskotek on 2008-02-12
i'm just wondering, if i can make my screen stand by by mouse click or assigned key from keyboard. 

i tried "lock the screen", but there is just blank screen my screen doesn't goes stand by... i want to use it since i'm not on the desk everytime, and i check my computer often. 

if there is a way or a script or just some configuring, it would be great.

---

### Post by kerry_s on 2008-02-12
i just turn the screen off with a icon on my desktop.

the command is:
sleep 5; xset dpms force off

that gives you five seconds to take your hand off the mouse.

here's what it looks like on the desktop, bottom right corner

---

### Post by diskotek on 2008-02-12
wow that's great!
how you can make a file executable for that?

---

### Post by kerry_s on 2008-02-12
> **diskotek said:**
> wow that's great!
how you can make a file executable for that?

you shouldn't need a file, just put that command, where it says command.

if you stick it in a file, make like this->

!/bin/sh
sleep 5; xset dpms force off

then right click the file and set it executable
then point your launcher at that file.

---

### Post by diskotek on 2008-02-12
thank you, this script worked flawlessly.i'm starting to promote it around.. since it will save lots on electricity :)

---

