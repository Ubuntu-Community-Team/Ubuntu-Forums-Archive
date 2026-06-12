---
title: "terminal search command?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-08-14
hello. does anyone know how do i search for programs by terminal? a friend told me that i must search then pick the name of the program and then "sudo apt-get install program's_name" to download&install it. thanx.

---

### Post by davebgimp on 2006-08-14
You're searching for programs to install?

If so...

**sudo aptitude search "keyword"**

or 

**sudo apt-cache search "keyword"**

---

### Post by engla on 2006-08-14
hey dave, since searching doesn't modify anything, you naturally don't need **sudo**. That part can be droppped.

---

### Post by davebgimp on 2006-08-14
> **engla said:**
> hey dave, since searching doesn't modify anything, you naturally don't need **sudo**. That part can be droppped.

Force of habit. My bad, thanks.

---

### Post by LadyDoor on 2006-08-18
Alternatively, there's always **sudo aptitude**, which will bring you into aptitude's nice "gui." Then if you press **/** you can search for something. Pressing **n** will search again.

--Door

---

### Post by m666 on 2007-03-09
But why **apt-cache search** and **aptitude search** bring different results?

---

### Post by knight17 on 2007-03-09
WOW! I never knew such a thing existed.Thanks for the great tip

---

### Post by m666 on 2007-03-09
Just figured it out.
'aptitude search example' lists packages with 'example' in package name whilest 
'apt-cache search example' lists packages containing 'example' either in package name or package description

---

