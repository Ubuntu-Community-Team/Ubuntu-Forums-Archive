---
title: "login"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by DustyH4 on 2008-03-13
I have just install UBUNTU 7.10.  I have booted to Login______
password________.  It will not accept either one.  I type in my login name
hit enter.  Password _______ appears but I can't type in anything.

I really would like a program that I don't have to be a geek to operate.
Are any one of the operating system versions that i can download and then add what I need after I learn to move around in program.  I do not know what any of things are that I am ask if I want it  or not.  Or at least step by step instruction I can print with out going to numerous pages to get one answer.  or shoukl I stick with windows and suffer through.

---

### Post by Cypher on 2008-03-13
The username and password you are being asked for is the same one you entered during the installation. If you've forgotten the password, then in the GRUB menu choose to boot the (recovery console) option, you'll be taken to a prompt..there type
```

passwd <username>

```
Substitute your username for <username> and then set the password. Now reboot the machine and boot into the normal Ubuntu option, enter the new password and you should be logged in..

---

### Post by bodhi.zazen on 2008-03-13
You mean your box boots to a command (log in) prompt ? If that is the case there is a failure of the X (gui) windows system.

Did you install the Desktop or Server ?

Your login name should appear as you type. Nothing will appear on the screen as you type your password.

---

### Post by aysiu on 2008-03-13
One of these links should help you:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by DustyH4 on 2008-03-13
when I boot it runs a lot of install stuff and the last thing is login.  I enter the name and then the pass word. nothing shows onthe pass word but I hit enter and get login incorrect.
I tried to boot grub menu by hitting esc, but I get a menu of ethier linnux or windows no other option. should I delete the software and start over.

---

### Post by bodhi.zazen on 2008-03-13
Follow Cypher's advice to reset your password. Make sure CAPS LOCK is not on.

---

