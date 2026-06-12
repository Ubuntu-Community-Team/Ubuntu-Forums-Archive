---
title: "command line"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by antidartan on 2007-05-21
Hello, 
   This is my first day with linux. I keep reading about how I simply have to enter something in the command line for this that or the other thing , but I have no idea how to get to the command line.
Thanks for any help on what I'm sure will be a long list of SNAFU's

Antidartan

---

### Post by Happy_Man on 2007-05-21
Applications --> Accessories --> Terminal.

---

### Post by juxtaposed on 2007-05-21
It's the Terminal, and I think its Applications - Accessories - Terminal.

EDIT: Got beat to it.

---

### Post by starcraft.man on 2007-05-21
> **Happy_Man said:**
> Applications --> Accessories --> Terminal.

Alternatively you can also push Alt+F2 (opens a run box) and then you can type in "gnome-terminal" its a quick way to get there :). Not to mention you'll probably have to open it often enough....

---

### Post by skyhopper88 on 2007-05-21
For ease of use, right click the icon in the Apps list and add it to your gnome panel somewhere.

---

### Post by ruy_lopez on 2007-05-21
Locate the taskbar at the top of the screen:

Taskbar-->Applications-->Terminal.

You just type the commands at the prompt. There are other terminals faster than this one. For starters try typing this (i know its long):

xterm -ls -fn 9x15 -sb 1000 -bg black -fg green &

Now, if you right click on the task bar, a dialogue will pop up. Choose "add to panel." Then from the button at the top choose "Custom Application Launcher." For the name of this launcher enter "Xterm". For the command field, enter "xterm -ls -fn 9x15 -sb 1000 -bg black -fg green &" Next, choose a funky icon, by clicking the "no icon" button. When your done choosing the icon, and you've confirmed everything, you should have a new icon at the top.

Whenever anyone tells you to enter something into the command line, click on the icon you placed on the toolbar. Cool, eh?

---

### Post by ruy_lopez on 2007-05-21
I should have mentioned, try Googling "command line basics" and "bash shell commands", for an introduction. The command line is a very powerful tool, most people who learn the command line never go back. Its worth putting in the time to learn the commands. Then you can come back here and help us out, too, when we're having trouble.

---

### Post by aysiu on 2007-05-21
Applications > Accessories > Terminal works only for Ubuntu. It is possible the OP is using Kubuntu or Xubuntu.

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) will show you where the terminal is, regardless of desktop environment.

---

### Post by houstonbofh on 2007-05-21
I guess I ain't "most people."  I have been in computers a long time and have used everything from Amiga, to MAC, to Windows, to Solaris, to Xerox Star, to several flavors of Linux.  I like the GUI as it is intuitive.  The CLI is constantly typing 'ipconfig' when I need 'ifconfig' or something similar.  It is easy to forget what CLI command works with what OS.  It is a handy tool often, but it is just a tool.

---

