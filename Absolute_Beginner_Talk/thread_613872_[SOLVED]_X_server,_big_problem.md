---
title: "[SOLVED] X server, big problem"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-11-15
I am using Feisty and tried to run compiz-fusion. The computer insisted on a re-start to correct my nvidia drivers, I did this and now am unable to start Feisty as it goes straight into "dos" (sorry) and then gives me a message "faled to start X server" and a restart gets the same result.
As I can't start Feisty I am sending this via XP (dual boot). Is it possible to give me any kind of help which I can return back to Feisty to correct this problem. I am not terribly technical but can follow instructions.
Thanks.

---

### Post by overdrank on 2007-11-15
> **Benbow said:**
> I am using Feisty and tried to run compiz-fusion. The computer insisted on a re-start to correct my nvidia drivers, I did this and now am unable to start Feisty as it goes straight into "dos" (sorry) and then gives me a message "faled to start X server" and a restart gets the same result.
As I can't start Feisty I am sending this via XP (dual boot). Is it possible to give me any kind of help which I can return back to Feisty to correct this problem. I am not terribly technical but can follow instructions.
Thanks.

HI when you get to the command line, Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by Benbow on 2007-11-15
Thanks, overdrank, it did the job! Marvellous!!

---

