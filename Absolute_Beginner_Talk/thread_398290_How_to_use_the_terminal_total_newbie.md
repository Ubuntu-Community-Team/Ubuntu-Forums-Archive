---
title: "How to use the terminal? total newbie"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by 55kjsmith on 2007-03-31
I'm a brand new Ubuntu user. Always used Windows, but a friend told me about Ubuntu. I downloaded 6.10 Edgy and installed it on a Sony VGN-T270P subnotebook. I got it installed and ran the update manager. Now I want to install Flash plug-in for Firefox, but the install notes say to navigate to the desktop in the terminal. Clueless on how. Is there a link to using the terminal for dummies? Any help would be appreciated. Thanks.:)

---

### Post by Majorix on 2007-03-31
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

All commands there.

To be specific with your question, you have to use "cd" to change directories. In your example, you get to the desktop this way:

```
cd Desktop
```

or you can use a wildcard (which is an asterisk):

```
cd D*
```

Hope it helps. Good luck!

---

### Post by Maestro23 on 2007-03-31
Some links to get you started:

Installing Software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Command Line: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Linux Command.org: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Welcome to Ubuntu and Good luck.;

---

### Post by annda on 2007-03-31
and two more to go:

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

as for the flash player:
[www.getautomatix.com](www.getautomatix.com)

---

### Post by aysiu on 2007-03-31
Well, first of all, I think you can install Flash by just visiting a website that requires Flash and then going through Firefox's *missing plugin* dialogue. This will install Flash for only the user you're logged in as (not system-wide for all users).

But if you want to know where the terminal is:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

And if you want to know how to use the terminal to install Flash system-wide (for all users):
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by AndyCooll on 2007-03-31
Also on these forums (for instance), if you do a search and people tell you how to do something, usually they will include the commands you are required to type in the terminal. The simplest method is to copy and paste these into a terminal.

:cool:

---

### Post by 55kjsmith on 2007-03-31
Thanks so much. Got flash installed. Can't wait to start looking at those links. The Ubuntu community is so friendly!

---

### Post by true_friend on 2007-03-31
> **AndyCooll said:**
> Also on these forums (for instance), if you do a search and people tell you how to do something, usually they will include the commands you are required to type in the terminal. The simplest method is to copy and paste these into a terminal.

:cool:

for pasting in terminal u have to use shift+insert command.

---

### Post by aysiu on 2007-03-31
Or you could right-click and select *paste* if you're a more mouse-oriented person.

---

### Post by nsilva on 2007-04-01
Also try different consoles, some bring extra features such as mutiple tabs, and copy paste, others are more rudimentary such as xterm.

Keep in mind you can do a Ctrl+Alt+F1 (F1 thru F6 are virtual consoles) to get back to 
the GUI you do Ctrl+Alt+F7.

If for some reason one day you GUI gets stcuk (Windows popular phenomenon) you can go to any of these virtual consoles and kill GUI or that specific program.

---

