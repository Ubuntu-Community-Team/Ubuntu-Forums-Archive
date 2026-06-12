---
title: "Update Manager does not run by itself"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-12-12
The update manager no longer automatically notifies me of updates. It works fine from bash or if I manually run the gui, but it use to appear in fiesty and tell me of new updates. I have the notification area set in my panel as well. Any ideas?

---

### Post by Shinbu-Otaku on 2007-12-12
i had a similar problem, but i cant remember exactly where i found the file. Its in the etc/ folder and there is a file that runs the update manager, just double click this and it comes up with a load of options, just enable all them that you need (i.e. security updates) and then it should work.

Soz i cant remember the exact directory, but i know thats how i done it (would look for ya, but im at work using XP lol)

---

### Post by d0nny2600 on 2007-12-12
To have it run automatically select System->Preferences->Session and add the command there. It will launch every time you login

---

### Post by plucky on 2007-12-12
Check your software sources

**System>Administration>Software sources>Updates**

Tick the box for automatic updates

Voila

---

### Post by apienk01 on 2007-12-12
Also, I think that on laptops Update Manager does not auto-check as long as the system runs on battery (for reason unknown to me; power management?).

---

