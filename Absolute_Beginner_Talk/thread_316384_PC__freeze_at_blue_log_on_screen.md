---
title: "PC  freeze at blue log on screen"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-12-10
I used automatix to install/update drivers, etc. One of the drivers was an nvidia driver and now when pc boots up  it freezes at the log on window and if it gets past the log on window it freezes at the desktop screen. How do I fix this? Also when it boots up right before it gets to the log on screen nvidia screen appears then goes to the ubuntu log on screen.

---

### Post by Ecthelion on 2006-12-12
Does anything happen when you press Ctrl-Alt-F1 ?
Normally you should get a terminal screen.
(Ctrl-At-F7 should bring the graphical interface back)

If you do get something try this:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions, when you don't know leave it as it is by default.

Once you answered all the questions you should be back a the terminal.
Do
```
sudo /etc/init.d/gdm restart
```
normally your graphical interface should come up again and you shoul b able to login as you did before.

This is not completely a solution since you won't be using the nvidia drivers anymore, but you will have the graphical interface.
I recommend you try a Nvidia guide (you can find so many of them on this forum) and try to configure it yourself (following one of those guides of course).

I hope this helps!

---

