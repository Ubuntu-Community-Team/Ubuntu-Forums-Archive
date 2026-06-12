---
title: "Ubuntu wont log in"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by ODF on 2007-12-30
Ubuntu crashed while installing updates on a fresh install because of the crappy Netgear wireless adapter drivers so i'm still able to boot ubuntu add my login name and password and then nothing happens.

[SOLVED] : I had to boot in restore mode by pressing esc while booting like f8 with windows, then I used that code line to correct my uncompleted updates.

```
dpkg --configure -a
```

---

### Post by Dr Small on 2007-12-30
Does it give you an error of wrong user name and password, or does it proceed past the login screen, and then goes blank?

---

### Post by ODF on 2007-12-30
No errors, no blackout ... the orange background is still there but nothing load.

---

### Post by Dr Small on 2007-12-30
Hmm. Well, have you tried shutting it down properly, and then booting it back up?
... I'm trying to think of what could be the problem.

---

### Post by ODF on 2007-12-30
Just did it, my mouse isn't freezed. I can't ctrl+alt+del.

I mean i can simply reinstall ubuntu but i know there's a solution and i want to learn it =)

---

### Post by ODF on 2007-12-30
Fixed, I logged with a different sesson wich was the 3rd option. I can't tell because my screen setting wasn't good enough for me to read the fonts.

Thank you, I can now use and continue to explore ubuntu.

---

