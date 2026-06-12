---
title: "Dapper and GRUB"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by aristotlewilde on 2006-06-10
I have been having a blast learning things with Dapper.  

I don't however have everything migrated to Linux yet, so I'd like my default OS in GRUB to be XP still.

I know how to get into the menu.lst, but how do I alter it so that XP is the default OS??

---

### Post by linuchsan on 2006-06-10
default=
Look at what start with title. The first title is 0, the second 1, etc.
When counting you will come to the xp title...maybe it is 4.
Than you have to set default=4 in menu.lst.

---

### Post by Herman on 2006-06-10
Hello, aristotlewild, Grub is a lot more fun than any other bootloader. It is extremely flexible and customizable and has no peers.
[*Click here*]("http://users.bigpond.net.au/hermanzone/p15.htm") for my web-page on GRUB and Ubuntu. 
linuchsan's advice is correct.
Regards, Herman :D

---

