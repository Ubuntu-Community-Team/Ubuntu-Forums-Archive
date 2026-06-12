---
title: "installing tar.gz package"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by chrisb.40 on 2007-07-09
very new but keen to learn.  How to install Clamtk 2.99.

Question 1:- where do I place the package so that I can follow the instructions below?

Qu 2:-  are the lines below 2 - 4 commands that I need to input to Terminal, and if so does this mean one at a time or together?


"NOTE: If you're using Ubuntu, there's no prebuilt ClamTk 2.99 yet. So, do this instead:
1. Download the ClamTk *.tar.gz file by following the "Downloads" link to the left.
2. tar -xzf clamtk-2.99.tar.gz
3. chmod +x clamtk-2.99/clamtk
4. sudo mv clamtk-2.99/clamtk /usr/bin/"

Regards

---

### Post by swisscow on 2007-07-09
Download it to your Desktop (home/Desktop)

Then in a terminal type ```
cd Desktop 
```(note the capital C) press return

Then type in the comands one by one.

Goodluck

---

### Post by Outrunner on 2007-07-09
First of all, a .tar.gz file is a compressed archive, so you don't install a .at.gz, you extract it(command 2).

And also, you can simply install clamtk from the repositories, you don't need to compile it

```
sudo aptitude install clamtk
```

EDIT: Oh and yes, 2-4 is what you would input into the terminal

---

