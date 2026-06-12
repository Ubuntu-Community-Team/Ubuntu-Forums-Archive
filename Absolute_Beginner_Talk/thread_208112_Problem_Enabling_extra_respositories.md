---
title: "Problem Enabling extra respositories"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-07-03
I wanted to Enable Extra respositories. For which i opened a terminal and typed.

```
avinash@avinash:~$ gksudo gedit /etc/apt/sources.list

(gedit:8256): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:8256): CRITICAL **: gedit_cmd_edit_paste: assertion `active_view' failed

```

Then Nothing happened. Neither gedit opened . Neither anything appened. 

What do i do to enable extra respositories.?

---

### Post by nanotube on 2006-07-03
[QUOTE=hardfire_avk]I wanted to Enable Extra respositories. For which i opened a terminal and typed.

```
avinash@avinash:~$ gksudo gedit /etc/apt/sources.list

(gedit:8256): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:8256): CRITICAL **: gedit_cmd_edit_paste: assertion `active_view' failed

```

Then Nothing happened. Neither gedit opened . Neither anything appened. 

What do i do to enable extra respositories.?[/QUOTE]
well, you could try using the commandline editor "nano" instead. use command
```
sudo nano /etc/apt/sources.list
```

that, for a quick workaround. don't know what's wrong with your gedit...

---

### Post by rickmans on 2006-07-03
gksudo you normally use when you are in a GUI, when you are in the terminal you could use sudo instead and probably you will notice there are no issues.

To edit via gksudo (don't ask why you would like to to do this explicitely via gksudo instead of sudo ;)). You press alt+F2  in ubuntu and a "Run application" window will popup, enter your command, and you will notice you are able to edit.

---

### Post by aysiu on 2006-07-03
*gksudo* in the terminal is just fine. Those "error" messages are a bug that the developers are well aware of.

I would never recommend using *sudo* for a graphical application. Some of the time it can be harmless, but it can also do serious damage to your system.

More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Gedit not opening--now that's a problem.

---

### Post by Apple 101 on 2006-07-03
If you're already in a GUI, just use Synaptic to edit the sources list.

---

### Post by bikeboy on 2006-07-03
[QUOTE=aysiu]*gksudo* in the terminal is just fine. Those "error" messages are a bug that the developers are well aware of.
[/QUOTE]
Glad you added that aysiu, I knew about gksudo's purpose but was also having the error that the OP has.

When I have it, gedit will open but no file will be opened. However I can browse (with gedit) to the file I wanted to edit and open it, root privalages intact. I guess this is what it *should* be doing for the OP, but obviously it's not.

---

