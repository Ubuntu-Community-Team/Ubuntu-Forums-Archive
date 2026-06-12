---
title: "Unable to login"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Tamil on 2007-03-05
When I try to login to Ubuntu, login screen comes again after few seconds. It happens with all logins in system.

---

### Post by mahiyar on 2007-03-05
Could it be that that the password which you are entering is wrong, or you are putting in user name where your password is supposed to be (some gdm login screens have single window). Or  you can go into recovery mode and make a new login for yourself.

---

### Post by StarscreamD on 2007-03-05
Another problem could be disk space. Is the Ubuntu partition you are using completely full? If it is, try:

```
sudo apt-get clean
sudo apt-get autoremove
```

Hopefully that will free up enough space to start X. If not, hit Alt+Ctrl+F1(this will drop you into terminal). Once you get to a command line, start removing things (rm) you do not need until you are able to log in. I would be careful of what you delete in this manner, however. It could crash your system even worse. Good luck!

:guitar:

---

### Post by priegog on 2007-03-07
Hi. I have the same problem. My disk is full too, it seems. However, when I hit crtl+alt+F1 to enter the terminal, when i enter the sudo apt-get clean command, it tells me "login incorrect". Apparently I need to login from the terminal or something like that BUT I don't know how to do it. Also I don't know how to navigate through the folders from the terminal to delete stuff...  (I know the biggest noob).. Can you give me a little direction please?

---

### Post by maniacmusician on 2007-03-07
after doing ctrl + alt + F1, you'll see the following dialog:
> 
[Hostname] Login: 
You're supposed to enter your username there, and press enter. Then it asks for your password. Type that in, and hit enter. You'll be logged in.

Then proceed to enter the command:

> sudo apt-get clean && sudo apt-get autoremove

---

### Post by priegog on 2007-03-07
I was just able to login. Thanks a lot!

---

