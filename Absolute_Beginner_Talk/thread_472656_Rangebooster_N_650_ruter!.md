---
title: "Rangebooster N 650 ruter!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-13
Hi, i just got a fresh Rangebooster N 650 ruter in the mail. only problem is that i can't install it in ubuntu cuz the install CD is for windows. and I don't have windows:(

---

### Post by danny_kay1710 on 2007-06-13
Personally i dont think you will need to CD to set it up but you could always try using Wine to run the CD.

You can get it by running the following commands in terminal

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

Then when you put the CD in browse to the exe file and right click it and select run with other program. Click other program option and type in Wine.

I can't definately say it will work as there is a chance it won't be compatible with what it needs to do but you could give it a shot

Alternatively you will need to find a windows machine

hope this helps
danny_kay1710

---

