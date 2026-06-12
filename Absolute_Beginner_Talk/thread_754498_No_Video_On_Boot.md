---
title: "No Video On Boot"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by thep8ntballfreak on 2008-04-13
ok i installed ubuntu for the first time the other day and have been having problems with it since. i finally got all the updates to work and i thought i was done. well i found out that my video card (EVGA 7950GT) was not installed so i clicked to enable drivers in the restricted drivers window and it installed and i thought great. i had to restart after this and when it restarted i dont get any video signal at all as soon as i get to the login screen. my monitor turns off when i get there. as i am a linux/ubuntu noob i have no idea what i did or if it can be fixed. i have a dell dimension 5150 so a lot of stuff on boot is locked. i have a dual boot with windows vista and all that works great. so what i need to know is how do i get my screen to show up so i can log into ubuntu and continue to learn the operating system. also any bigenner tutorials you guys can point me to would be great. thanks in advance for all your help.

---

### Post by Crafty Kisses on 2008-04-13
You should get be at a DOS type screen, when you are try the following:
```
startx
```
If that doesn't work, try this:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions the best you can.

---

### Post by chewearn on 2008-04-13
At the login screen, even though you can't see anything on the monitor, type in your <username><enter>, then <password><enter>.  Once you logged in, does the monitor turned back on, and you can now see the desktop on the monitor?

If yes, you can either:
1. turn on automatic login
2. follow the instructions in this [link1]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") and [link2]("http://www.namanb.com/2007/12/ubuntu-bootup-resolution-problem-part-2.html")

If no, you can undo the changes to restricted driver by:
1. once you reach the login screen, press CTRL+ALT+F1
2. login the console prompt using your <username> and <password>
3. type the following commands:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```


EDIT:
Opps, late...

---

