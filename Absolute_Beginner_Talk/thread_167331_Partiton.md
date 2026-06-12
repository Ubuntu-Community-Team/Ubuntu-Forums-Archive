---
title: "Partiton"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by LogiGuy on 2006-04-28
I just started using Linux for the first time, just a few hour's ago.
So far all I know is how to use a browser im a very slow learner.. anyway im wondering how would I make a partiton on Ubuntu 5.10 Breazy? and then install WinXP on it.. and then when it boots up I have Ubuntu/XP as my selected boot.

I know im asking alot, but when I searched the forums. All I got was partition questions, not actually how to make it.

---

### Post by Sef on 2006-04-28
Read this excellent tutorial to learn how to dual boot.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by LogiGuy on 2006-04-28
[QUOTE=Sef]Read this excellent tutorial to learn how to dual boot.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")[/QUOTE]

It say's,

"This website is for people who have a Windows operating system in their computer and want to add a Linux operating system. "

Are you sure this is what I need? As I said, im running Ubuntu right now.

---

### Post by mostwanted on 2006-04-28
The easiest solution is to backup your data and install Windows first. Remember to manually edit the partitions in the Windows installer, so you get the size you want. When you install Ubuntu afterwards (remember to manually edit partition tables again or select the option where you install on largest free space) it will automatically detect and set up Windows in your bootloader after you're done installing.

Windows is not designed to detect and set up alternative operating systems. Ubuntu is designed to detect and set up Windows.

---

### Post by LogiGuy on 2006-04-28
[QUOTE=mostwanted]The easiest solution is to backup your data and install Windows first. Remember to manually edit the partitions in the Windows installer, so you get the size you want. When you install Ubuntu afterwards (remember to manually edit partition tables again or select the option where you install on largest free space) it will automatically detect and set up Windows in your bootloader after you're done installing.

Windows is not designed to detect and set up alternative operating systems. Ubuntu is designed to detect and set up Windows.[/QUOTE]

:confused: 

..Think I'll just live with using Ubuntu. I'll probably learn faster this way.

---

### Post by Sef on 2006-04-28
> .Think I'll just live with using Ubuntu. I'll probably learn faster this way.

Yes, you do learn faster. (Though not without mistakes. So keep the back ups current.)

---

