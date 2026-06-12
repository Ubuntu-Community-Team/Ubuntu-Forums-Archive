---
title: "What is my root password?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by carl_schulze on 2007-06-26
I'm totally new and rapidly becoming befuddled.  I tried downloading and installing a Java plugin for Firefox and ran into instructions to open Terminal and type in **su.**  Did that and got polled for my root password.   I have no idea what that is; when I installed Feisty Fawn, the only i.d. I had to volunteer was a user name and a password.  I tried that password as my "root password," but it did not work!  2 Questions:  what is my "root password" and how do I "navigate" to root?

Carl

---

### Post by w4ett on 2007-06-26
Your root password is the same as your login password....when you enter it in the terminal, the characters are not echoed on the screen for extra security, just enter your PW and press enter.

---

### Post by wormser on 2007-06-26
Ubuntu does not set up a root password during the install.  Instead you are suppose to use **sudo** and **gksudo** (for gui apps) before the command for root privileges.  Just for your knowledge to set the root password **sudo passwd root**.  But there is no need to use root so stick with sudo and gksudo.  Your sudo and gksudo password is your password.

---

### Post by Maxtorm on 2007-06-26
To add to wormser, you can also use 
```
sudo su -
```
to get a temporary root prompt.  As far as I am aware, you can change/assign the su password with just
```
sudo passwd
```

---

