---
title: "Error when trying to open a terminal window..."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Bwangster12 on 2007-07-31
Whenever I try to open a terminal window to try and type some commands the screen goes black and gives me the following message:

Fatal Server Error
Caught Signal 11... Server Aborting

xinit: connection to X server lost

I try to use the xfce terminal or the x terminal and none of them work.

---

### Post by asmoore82 on 2007-07-31
what commands are you typing :confused:

this seems like a real hardware problem

---

### Post by Bwangster12 on 2007-07-31
Well, this wasn't a problem until last night all of a sudden.  I hadn't really done anything and then I went to try and use a terminal and it kicked me back to that window.

---

### Post by Ek0nomik on 2007-07-31
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)

---

### Post by Ek0nomik on 2007-07-31
> **asmoore82 said:**
> what commands are you typing :confused:

this seems like a real hardware problem

It isn't a command that's being executed that's causing the problem.  It is merely opening the terminal that's causing the problem.

*From the link I posted earlier*;

```
Hi Morgan,

I think that this fix has worked for a few people:

As for X crashing when you open the terminal, I recommend the following:

To do this, you'll need to boot into an xterm session, so when the login
screen comes up, click on the Sessions icon, and select Terminal session or
something similar.
This will bring you into an xterm session - not an xfce4-terminal. It
should work. :)

* use the "cd" command to navigate to your /etc/X11 folder and make a backup
copy of your xorg.conf file. You can do this by entering:
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup

* edit your xorg.conf file, changing the default depth from 24 to 16. You
can
do this by entering:
sudo nano xorg.conf
. . . then scroll down to the Screen section, and find the DefaultDepth
option. Change that number to 16.

*press control-o (letter "O") to save the file, then press control-x to exit
the nano text editor.

Then exit from the xterm session, and it should bring you back to the login
window. Select an Xfce session from the session button, and proceed to login
as usual.

I hope this helps! Sorry it is kind of a non-pretty way to do things, but
it's hard to tell you to enter these changes into a regular terminal when
the
regular terminal crashes your X session! I think that this should work,
though . . .
Let us know if it doesn't work. Thanks!
```

---

### Post by Bwangster12 on 2007-07-31
Well the problem I appear to be having now is that I do not use a login manager.  I have been just logging in and entering the command Startx, so I do not know how to start an xterm session.

When I try that process from that screen that I get kicked too... which appears to be the same screen that I get when I first turn on my computer... it shows me that xorg.conf file but there is no text to edit.  I can't see anything in the file.

---

