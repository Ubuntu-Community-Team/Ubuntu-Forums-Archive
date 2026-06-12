---
title: "sudo password problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by naggis on 2008-04-01
I am a newby of less than a week. I worked my way through spiderbatdads sticky regarding finding programs. All worked well until I got to using commands in the Terminal. The basic command he gave was straightforward enough but pressing Enter resulted in a request for a password - [sudo] password for roger: When I tried to enter my login password, nothing appeared on screen! 
What did I do wrong? Is their another password I don't know about?
Is their any way of disabling the need for a password at startup?
Thanks for any help you can offer

---

### Post by Oldsoldier2003 on 2008-04-01
> **naggis said:**
> I am a newby of less than a week. I worked my way through spiderbatdads sticky regarding finding programs. All worked well until I got to using commands in the Terminal. The basic command he gave was straightforward enough but pressing Enter resulted in a request for a password - [sudo] password for roger: When I tried to enter my login password, nothing appeared on screen! 
What did I do wrong? Is their another password I don't know about?
Is their any way of disabling the need for a password at startup?
Thanks for any help you can offer

the password is completely masked when you type it. (this is a security enhancement and can be a bit unnerving at first)  Just type your password and hit enter.

---

### Post by sayakb on 2008-04-01
@OP
To enter the password through a GUI, use gksudo instead of sudo. For example, use gksudo for gedit, nautilus, firestarter etc, and use sudo for any CLI tool.

---

### Post by naggis on 2008-04-02
Thanks very much for the replies. As you say it is unnerving at first - but now I now that the typing is hidden, all seems to work ok

---

