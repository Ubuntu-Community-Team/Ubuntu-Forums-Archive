---
title: "Problems Running From Command Line"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Rhyth on 2007-11-21
I'm running the check.sh file from the ati radeon linux driver page, or attempting to, and I get the following when I try to run it

rhyth@Hyper-Basket:~/Desktop$ ./check.sh
=====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

I guess ./ isn't what I'm supposed to do. How am I supposed to run this file?

---

### Post by Inxsible on 2007-11-21
Cd to the directory where you have the file. I am assuming its your desktop
```
sudo check.sh
```Have you made it executable though?

---

### Post by Rhyth on 2007-11-21
Yeah, I chmodded it, I get the following when I try to do your script

rhyth@Hyper-Basket:~/Desktop$ sudo check.sh
sudo: check.sh: command not found

---

### Post by mellowd on 2007-11-21
try sudo ./check.sh

---

### Post by Rhyth on 2007-11-21
Trying sudo ./check.sh I still get the same as I did the first time

rhyth@Hyper-Basket:~/Desktop$ sudo ./check.sh
=====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

---

### Post by mellowd on 2007-11-21
have you completely closed x?

---

### Post by Rhyth on 2007-11-21
I don't understand, what is x?

---

### Post by mellowd on 2007-11-21
x is the system your gui runs on top off. get out of the gui completely.

---

### Post by Rhyth on 2007-11-21
I really have no idea what you're talking about, can you explain?

---

### Post by Inxsible on 2007-11-21
> **Rhyth said:**
> I really have no idea what you're talking about, can you explain?Press Ctrl + Alt + F1 to go into command line mode. But I don't see how that will help !

---

### Post by mellowd on 2007-11-21
I'm not sure about the ati driver, but I just installed the nvidia driver and I had to completely close X off before it would install

---

### Post by Rhyth on 2007-11-21
I'm not trying to install it, I'm just trying to run this little preliminary file they have to tell me which driver I need. Also, I just tried the ctrl, alt f1 thing and logged in and it told me the same thing I posted before

---

### Post by Rhyth on 2007-11-21
What else could I be doing wrong? It's definately not chmod so could it be something to do with administrator priviledges that I've overlooked? I have not much clue what I'm doing with this.

---

### Post by mellowd on 2007-11-21
what happens if you sudo su first and then try and run it?

---

### Post by Rhyth on 2007-11-21
I get the same, but where it says rhyth before it now says root:

root@Hyper-Basket:/home/rhyth/Desktop# ./check.sh
=====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

What does this mean?

---

### Post by Inxsible on 2007-11-21
could you give us the link where you got the instructions to run the said script? maybe there is something else that you may be missing out.

---

### Post by mellowd on 2007-11-21
I don't really know as I haven't come accross that error yet and I'm not running ATi hardware either. I found this link though, it may be of some help:

[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/6684](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/6684)

---

