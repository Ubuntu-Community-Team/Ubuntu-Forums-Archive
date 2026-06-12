---
title: "I'm gonna scream in a minute!!!!!!!!!!!!!"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Ace Ironballs on 2006-09-12
Hi
I'm a total newcomer to Ubuntu [5.10] and Linux. I have installed the system and i am really impressed.
The problem i have is probably ridiculous to you guys but please be be patient. I am trying to set up a network connection using a BT Voyager 105. Everything was going swimmingly until it got to the part where i needed to change the synch .bin file from synch o1 to synch 03 which is needed for the Voyager 105.
Are you still with me??? this is where the problem lies...
I have the synch03 file in my home folder and i want to get it into /etc/eciadls/ but every time i try this i keep getting a dialogue box popping up to tell me i don't have permission.

Any suggestions please

---

### Post by croak77 on 2006-09-12
Use sudo for any editing of files not in /home.

---

### Post by Daremo on 2006-09-12
open a terminal window and type: sudo nautilus

press the enter key and then enter your password and press the enter key again. 

this will open a nautilus file manager window with root access. just be careful as you can move or delete just about any file this way.

---

### Post by Brownedwg89 on 2006-09-12
or use the command line to do
```
sudo cp ~/synch03 /etc/eciadls/synch03
```

---

