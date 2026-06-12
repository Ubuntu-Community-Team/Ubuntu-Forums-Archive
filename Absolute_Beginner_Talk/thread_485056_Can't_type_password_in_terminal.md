---
title: "Can't type password in terminal"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by helpneedsme on 2007-06-26
Ok so I have a problem and am trying to fix it and I need to use the terminal with admin privileges so I type in  "sudo username" and it then ask me for my password and I try to type it in and the keyboard won't let me none of the keys except space bar  will work at that point until I start over a new command in the terminal.

---

### Post by corney91 on 2007-06-26
Passwords in the terminal do not show up but they still register. Just type the password and hit enter and it should work.

---

### Post by w4ett on 2007-06-26
For security, your password characters are not echoed on the screen, just type them in normally and press enter.

---

### Post by overdrank on 2007-06-26
> **helpneedsme said:**
> Ok so I have a problem and am trying to fix it and I need to use the terminal with admin privileges so I type in  "sudo username" and it then ask me for my password and I try to type it in and the keyboard won't let me none of the keys except space bar  will work at that point until I start over a new command in the terminal.

Hi you are typing it is not showing for security! :popcorn:

---

### Post by helpneedsme on 2007-06-26
Thanks guys

---

### Post by helpneedsme on 2007-06-26
I just did it and it said. Command not found>

---

### Post by Orochi on 2007-06-26
You don't type "sudo username" you type "sudo commandyouwanttorun"

---

### Post by Seisen on 2007-06-26
Are you trying to run a application from the terminal? If your are then do just put in 

```
sudo nameofapplication
``` or gksudo if it is a graphical application.

---

### Post by helpneedsme on 2007-06-26
A picture is worth a thousand words.
[IMG]http://img240.imageshack.us/img240/7448/screenshotjq6.png[/IMG]

---

### Post by Seisen on 2007-06-26
Put this in the terminal

```
sudo dpgk --configure -a  
```

---

### Post by w4ett on 2007-06-26
The instructions are in the pic.....in the terminal type:

sudo dpkg --configure -a

press enter to repair the error

---

