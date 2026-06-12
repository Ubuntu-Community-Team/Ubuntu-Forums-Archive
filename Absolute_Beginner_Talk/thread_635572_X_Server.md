---
title: "X Server"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Rick Doll on 2007-12-08
I read another thread on this earlier but when I tried the commands in it I am not sure exactly what it is doing.

Basically the command was to stop the server altogether and when I do it it goes to a dos screen tells me 6 commands it is running and then just sits there. Is exiting the server something that takes a long time and I should just wait it out?

What I am trying to accomplish is to install my nvidia driver but when I run it it says I have to exit the x server. So I tried the stop code and as I said it just sits in the dos screen, is it not supposed to come back and let me resume opperations or something?

First couple of days on Linux so you will have to forgive me if this is an easy question.

---

### Post by Dr Small on 2007-12-08
Could you please post the commands that you were given, to stop the X server, so we may best help you ?

Kind regards,
Dr Small

---

### Post by Rick Doll on 2007-12-08
sudo /etc/init.d/gdm stop

after entering it it goes into a dos screen where it has the 6 things it has checked and said ok, last being something about boot script, and does nothing, just sits there.

Is it supposed to go back to the terminal?

---

### Post by Dr Small on 2007-12-08
Try pressing ALT + F1 to go to a terminal.

Dr Small

---

### Post by PmDematagoda on 2007-12-08
Actually Dr.Small, isn't the sequence supposed to be Ctrl+Alt+F1?

---

### Post by Dr Small on 2007-12-08
> **PmDematagoda said:**
> Actually Dr.Small, isn't the sequence supposed to be Ctrl+Alt+F1?
Only if you are in an X session, do you need to press CTRL. If you are in another terminal (which apparently he is at VT8 ) then all he would need to press is ALT + F1.

Dr Small

---

### Post by Rick Doll on 2007-12-08
Thank you, got the nvidia driver all installled.

---

