---
title: "2 things i need help with"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-08-01
1)  I installed beryl and ran it and got a white screen, I can't login anymore so I'm using a different account which is not admin. I want to get my account back, how do i do this?

2)  I have Ubuntu 7.04 and no other OS on my computer. I want to install windows XP withought losing Ubuntu, is this possible? any help is appreciated. (dual boot) For gaming purposes.

---

### Post by {A}Poly on 2007-08-01
help?

---

### Post by alienexplorers on 2007-08-01
You can load windows XP on your system.  The only thing you need to change is the location of the grub loader so it knows you are running Windows XP.

---

### Post by overdrank on 2007-08-01
> **{A}Poly said:**
> 1)  I installed beryl and ran it and got a white screen, I can't login anymore so I'm using a different account which is not admin. I want to get my account back, how do i do this?

2)  I have Ubuntu 7.04 and no other OS on my computer. I want to install windows XP withought losing Ubuntu, is this possible? any help is appreciated. (dual boot) For gaming purposes.

HI please don't bump the thread so quickly, your first problem can be solved by booting the computer and using the keys ctrl,alt, F1 all at the same time will bring you to the terminal then you can login user name and password, Then use the command ```
sudo apt-get remove beryl
```
then you can restart with the command 
```
sudo shutdown -r now
```
As for your second issue if you choose to install window after the install of ubuntu you will need to reinstall the grub after the windows install. This thread will help in that
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Smu on 2007-08-01
When you're logged in on the other account press Ctrl+Alt+F1 (don't press it yet read first!). This will take you to a terminal log in there try to log in with your normal account. When your logged in type "sudo apt-get remove beryl" this should remove beryl from your account and hopefully let you log in again.. And yes, to get back to your normal session press Ctrl+Alt+F7.

It is possible to doalboot XP and ubuntu but its easier to do it when you install XP first. When you have only ubuntu installed  you need to make a partition (with Gparted) where you'll  install XP. After that you have to re-install GRUB or else you won't be able to boot into ubuntu... There's lots of info regarding this on the forum. Just take a look around and you'll find the answers.

..a bit too late with the info... :D

---

### Post by {A}Poly on 2007-08-01
Ok i guess I'll just install windows and than install ubuntu again, since it's easier. and that will fix the blank screen issue aswell.

---

