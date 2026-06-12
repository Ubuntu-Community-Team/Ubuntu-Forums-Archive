---
title: "need help in enabling the pen in T series Fujitsu"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-05-23
I need help in enabling a pen computer, here is the current screenshot, how do I enable root. (this is my friends computer)

[[IMG]http://img70.imageshack.us/img70/9214/screenshot9vf.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshot9vf.png)

I am following the instructions on this page:
[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D)

---

### Post by Gimbo on 2006-05-23
To enable root, type "sudo" before the rest of your commands (sudo means "do as superuser", which effectively gives you root permissions temporarily).

eg sudo apt-get install setserial

EDIT: when it asks for your password, just enter the password you use to logon (it won't show up in the terminal, but press enter once you're done and it should work)

---

### Post by Klaidas on 2006-05-23
About sudo: see my 4th link in signature :)

---

