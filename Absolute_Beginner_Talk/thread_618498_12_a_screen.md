---
title: "1/2 a screen?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2007-11-20
I am trying to run the 7.10 live CD and I only get the top half of the screen to display. Any ideas why and what I can do to fix it? :KS

DB

---

### Post by Het Irv on 2007-11-20
Can you only see the top half of the screen or is the whole screen compressed into half of the moniter.  When does the half screen thing start when you first get the CD menu (Start and Install, CD checker, stuff like that) or when the X Server starts (the desktop).

It may not be a bad idea to use the CD check option.

---

### Post by purebuilt on 2007-11-20
No, only 1/2 the screen displays and it starts when the desktop background image is displayed. Menu items extend below the 1/2 mark and the mouse will still find them (but blindly).

DB

---

### Post by Inxsible on 2007-11-20
> **purebuilt said:**
> No, only 1/2 the screen displays and it starts when the desktop background image is displayed. Menu items extend below the 1/2 mark and the mouse will still find them (but blindly).

DBMaybe your resolution is too low or something. Go to System>>Preferences>>Screen Resolution and change it to a higher value, if you can.

If no other resolutions show up, then you will need to change xorg.conf file

---

### Post by purebuilt on 2007-11-26
3rd time was the charm. I ran it again and it installed. The only problem I have now it that it won't allow me to ADD REMOVE programs. It keeps saying it needs to update the list and then looks like it does but then I click on the box to add ThunderBird email and it says it needs to update the list again.

How do I fix that?

DB

---

