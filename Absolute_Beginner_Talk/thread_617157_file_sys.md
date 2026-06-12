---
title: "file sys"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Josh@linx on 2007-11-19
1.I am yet another os convert but am still a bit green.
I am trying to alter the timeouts in the menu.list and dhclient.config.
When I click save I get a yellow bar at the top of the fie browser saying Im not the
owner and unable to save changes .

2.When entering code examples in the terminal, do they go directly after "username@computer"

---

### Post by jordanmthomas on 2007-11-19
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) <-- you may find this helpful

To edit a file not owned by your user, use gksudo (or sudo in cases where you're not using a gui editor) to edit your file.

For example, your menu.lst file you're editing:
```
gksudo gedit /boot/grub/menu.lst
```

^^ this is an example of "code examples" as you put it, and yes, you just type it directly after your prompt in the terminal.

Be careful any time you use sudo or gksudo because this gives you power to do anything you want to your computer, even delete everything.

---

### Post by Josh@linx on 2007-11-19
I have tried to enter the above code into the promt.
When I press enter i am asked for my password but no input from key boars is
accepted.

---

### Post by jordanmthomas on 2007-11-19
Does a window pop up and ask for your password?  If not, make sure you've typed gksudo and not just sudo.

In the case that you are using sudo, nothing will be displayed as you type you password in.  This is a security feature.  Just type your password and then press enter.  It **is** accepting input, you just can't see it.

---

### Post by Josh@linx on 2007-11-19
thankyou bud that worked a treat

---

