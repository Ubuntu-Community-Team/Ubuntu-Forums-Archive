---
title: "about the adept manager in kubuntu"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by zivxx on 2007-12-08
Hey everyone, ive installed many programs from the adept manager in kubuntu..and my questions is like that...they don't show up at the right place in the KMENU so what is the folder everything from adept is installed to?
really thanks if someone can help.

---

### Post by PetePete on 2007-12-09
most files are installed to /usr/bin

if you want to find something try this command.
sudo updatedb
whereis programName

or ... sudo updatedb
locate programName

---

### Post by viking777 on 2007-12-09
Katapult can be quite useful for locating programs you cant find. It is launched from the Utilities menu in kde and just presents a large icon when launched. Just start typing the program name that you are looking for and it will offer suggestions based on every letter that you type - give it a try it can be useful.

---

