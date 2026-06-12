---
title: "password problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by talon4g63 on 2007-06-29
hey guys

i am a complete newb, i just installed the other day and i have been trying to make my wireless to work but every time i try and use a sudo command i get a pw error.  Listed below is part of the terminal command line, i feel like i am banging my head against a wall :( please help!  thanks cody  

:~$ sudo gedit /etc/network/interfaces
Password:
home0onSorry, try again.
Password:
home0oneSorry, try again.
Password:
sudo: 2 incorrect password attempts

---

### Post by LaRoza on 2007-06-29
Use gksudo for graphical apps like GEdit.

---

### Post by starcraft.man on 2007-06-29
The password is the same as the one you assigned to your user account by default. Only reason for it to be different is if you changed it manually via terminal. Could it just be your typo, or do not remember the pass you set?

On a related note, when launching graphical applications like gedit, its best to use "gksudo", sudo is supposed to be only for text commands >.>.

---

### Post by into_311 on 2007-06-29
The password sudo or gksudo is looking for is the exact same one you use to login to your user accuont when you  boot up your computer. The one assigned to that user.

---

### Post by Nyxess on 2007-06-29
its a simple answer, but check your caps lock.

---

### Post by talon4g63 on 2007-06-29
its not a typo,  i have tried everything including changing the pw several times and verified that it did get changed by re logging in.  Just having wireless issues but this seems to be more of a problem. thanks for the info about 'gksudo' thanks cody

---

### Post by talon4g63 on 2007-06-29
the use of 'gksudo' is that because i have a graphical pw manager or user interface? please clarify  my understanding of this. thanks cody

---

