---
title: "about boot"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by teko80 on 2006-01-25
hi, I installed ubuntu successfuly but when during bootup it tries to connect to ntb.ubuntulinux.org to adjust clock it fails because internet is connected later. So the boot process is delayed. How can i disable only this configuration? (the message is "synchronizing clock to ntb.ubuntulinux.org -then it delay- fail")

---

### Post by earobinson on 2006-01-25
if you install bum it will let you edit what happens at boot.

---

### Post by dueY on 2006-01-25
[QUOTE=earobinson]if you install bum it will let you edit what happens at boot.[/QUOTE]

Any other way to do this?  Sounds like there is little to no educational value in using BUM. :p 

teko: You can press CTRL+C if it is taking too long to skip it.

---

### Post by earobinson on 2006-01-25
[QUOTE=dueY]Any other way to do this?  Sounds like there is little to no educational value in using BUM. :p 

teko: You can press CTRL+C if it is taking too long to skip it.[/QUOTE]
true but then you have to do it every time dueY

---

### Post by dueY on 2006-01-25
[QUOTE=earobinson]true but then you have to do it every time dueY[/QUOTE]

Yeah, that's why I asked if there was another to do it.  Maybe involving the terminal and editing some files or something, not downloading some program to do it for you :p

---

### Post by Iowan on 2006-01-25
One short, incomplete, and possibly unadvised method would be to edit the RC file to not start the clock sync program. [Here]("http://ubuntuforums.org/showthread.php?t=89491&highlight=how-to") is some other info on speeding up the boot process.

---

### Post by earobinson on 2006-01-25
Iowans way works, I just tend to fire off the most simple answer in Absolute Beginner Talk, but your right I should have given both answer sorry.

EDIT: to spell Iowans correct

---

