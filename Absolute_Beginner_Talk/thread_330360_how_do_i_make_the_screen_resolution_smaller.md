---
title: "how do i make the screen resolution smaller"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by monchot on 2007-01-03
how do i change the screen resolution to 1280x1024. right now it only goes upto  1024x768. my monitor can support upto 1280x1024. and my video card is an nvidia fx5500 with 256mb memory. i dont know anything about linux.how to program and all that stuff.

---

### Post by axle_foley00 on 2007-01-03
Did you try going to **System->Preferences->Screen Resolution** ?

---

### Post by MkfIbK7a on 2007-01-03
i know excactly what to do
sudo dpkg-reconfigure xserver-xorg
when it asks you about resolution only choose what it should be e.g. choose only 1280x1024 deselect all other resolutions
next when it asks you something about simple medium advanced choose simple then choose 17 in monitor i had that excact problem and this is how i fixed it

---

### Post by monchot on 2007-01-03
thanks.got it to work

---

### Post by sinnerman on 2007-01-03
For best graphic and performance look for newest driver for nVidia graphic card on official nVidia site.

You can start test and result are tell you does card working properly ;-)

---

### Post by MkfIbK7a on 2007-01-03
did my suggestion work?

---

### Post by ir_newbie on 2007-03-30
how do i find out what the specs of my comp r.
stuff like cache, ram, hardrive and others...
its a dell latitude d500, and it used to be my brothers any clue how to find out stuff like that??

---

### Post by spinflick on 2007-03-30
ir-newbie please dont use other peoples threads to ask unrelated questions, it gets confusing, plus more people will see your problem if you post your own thread. 

[PHP]cat /proc/cpuinfo[/PHP]

[PHP]free[/PHP]

[PHP]df -h[/PHP]

---

