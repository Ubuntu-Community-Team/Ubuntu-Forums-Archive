---
title: "How to start ubuntu?"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by Redbettas on 2005-08-21
Hi,

I have finish install Ubuntu and upon starting up, im prompt to enter my userID and password. Once enter, it just stuck there and didnt go into the GUI screen. Any other command that i need to enter?

---

### Post by humanity_to_others on 2005-08-21
```
startx
```

---

### Post by aysiu on 2005-08-21
Have you tried *startx*?

---

### Post by Redbettas on 2005-08-22
I have not try that yet. Would do so tonight. So that the command to start it, im totally lost as my unix command sux. I only try out the list directories command. Thank

---

### Post by Knome_fan on 2005-08-22
Hi,
how did you install Ubuntu?
If you did a standard install, you should see a graphical login screen by default.
Did you an expert install?
If so, install ubuntu-desktop which should give you a graphical login:
sudo apt-get install ubuntu-desktop

If not, do you get any errors that say X can not be started?

---

### Post by Redbettas on 2005-08-23
hi, i try the startx command and it prompt me there no such command. I didnt see any standard or expert mode during the installation. I start installation by keying the "server" command.
I didnt see any GUI login screen..mine it DOS login screen.

---

### Post by Lord Illidan on 2005-08-23
That explains it. Server comes without a GUI, I think...

Try re-installing it, and don't enter server, just press enter at the installation prompt..

---

### Post by Knome_fan on 2005-08-23
Lord Illian is right, that explains it.
However, I don't think you have to reinstall. Simply installing ubuntu-desktop and then restarting should be enough.

---

### Post by Lord Illidan on 2005-08-23
> Lord Illian is right, that explains it.
However, I don't think you have to reinstall. Simply installing ubuntu-desktop and then restarting should be enough. 

Right you are...

If you want to re-install, you can re-install, otherwise, just put in the cd, and type in the terminal:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Redbettas on 2005-08-23
ok thx a lot. I was wondering why i cant go into the GUI.....cos i did try to run "live" with before and it work. Would try out again tonight.

---

