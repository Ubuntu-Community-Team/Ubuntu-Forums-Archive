---
title: "Dual boot problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by quanct on 2006-07-17
I recently configured my computer for dual boot (Windows XP, Ubuntu). It was working perfectly yesterday, but today, when I tried to boot up Windows XP, I keep getting one of those "blue screen" error messages. Unfortunately, the message goes away too quickly for me to read exactly what it says. Ubuntu, however, boots up normally. What could be the problem? Will I have to reinstall Windows? Should I delete Ubuntu?

---

### Post by rockfloyd on 2006-07-17
does grub come up first or is this after you select windows?

---

### Post by quanct on 2006-07-17
> **rockfloyd said:**
> does grub come up first or is this after you select windows?

grub does come up. I select to boot up Windows, and sometimes it'll look like it's loading normally (gives me my desktop and everything) and then...blue screen...then it restarts.

---

### Post by rockfloyd on 2006-07-17
try running that windows restore thing that lets you roll back your system. if that doesn't work you might have to run recovery console and set your windows back to factory. i can't imagine that uninstalling ubuntu would help this at all.

---

### Post by b1g4L on 2006-07-17
No, uninstalling Ubuntu wouldn't resolve this issue. Seems like the issue lies within Windows boot process. Try using a Windows XP boot disk (google) or try loading Windows in safe mode.

---

### Post by quanct on 2006-07-17
> **b1g4L said:**
> No, uninstalling Ubuntu wouldn't resolve this issue. Seems like the issue lies within Windows boot process. Try using a Windows XP boot disk (google) or try loading Windows in safe mode.

Loading in safe mode works, but what would I do after that?

---

### Post by gotname? on 2006-07-17
go to event viewer in you management snap in and see whats causing the crash

control panel -> administrative tools -> event viewer

browse for error reports which are marked in red. if there is limited info availble, browse the technet and knowledge base resources on the microsoft site using the error code as your search term

---

