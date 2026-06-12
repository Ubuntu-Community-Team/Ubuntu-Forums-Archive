---
title: "opening terminal resarts xubuntu"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by iateshaggy on 2007-11-22
is there anything i can do to fix this?  i just installed xubuntu on a old hp pc.  i saw some threads about this version not working well w/ hp laptops, could this be related?

---

### Post by overdrank on 2007-11-22
> **iateshaggy said:**
> is there anything i can do to fix this?  i just installed xubuntu on a old hp pc.  i saw some threads about this version not working well w/ hp laptops, could this be related?

HI you can try and open with alt, F2 keys and type ```
gnome-terminal
``` See it that works.

---

### Post by iateshaggy on 2007-11-22
The command "gnome-terminal" failed to run:

Failed to execute child process "gnome-terminal" (No such file or directory)

---

### Post by Dr Small on 2007-11-22
Try "xterm"... I forget what xubuntu uses as it's terminal.

---

### Post by overdrank on 2007-11-22
> **Dr Small said:**
> Try "xterm"... I forget what xubuntu uses as it's terminal.

Dr small beat me too it lol ```
x-terminal-emulator
``` with the alt, F2 keys  :)

---

### Post by iateshaggy on 2007-11-22
same thing, i've also tried installing terminal and after the install i get the same thing.

---

### Post by mali2297 on 2007-11-22
It's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

See also this post:
[http://ubuntuforums.org/showthread.php?t=605869?post=#8](http://ubuntuforums.org/showthread.php?t=605869?post=#8)

---

### Post by santiagoward2000 on 2007-11-22
Hi! I have a question:
Does the problem occur when you try to open **xterm** o **xfce4-terminal**?

---

### Post by iateshaggy on 2007-11-22
xterm doesn't exist and the second one opens a terminal, then reboots.  if i just go to terminal in my applications, i don't see the terminal, it just reboots.

---

### Post by mali2297 on 2007-11-22
> **iateshaggy said:**
> xterm doesn't exist and the second one opens a terminal, then reboots.  if i just go to terminal in my applications, i don't see the terminal, it just reboots.

Press ALT-F2, and type
```

xterm

```

---

### Post by iateshaggy on 2007-11-22
i get an error message, it isn't there.

---

### Post by mali2297 on 2007-11-22
> **iateshaggy said:**
> i get an error message, it isn't there.

What kind of error message? xterm should be there unless you have uninstalled it yourself.

Anyhow, you can reinstall it via Synaptic.

---

### Post by iateshaggy on 2007-11-22
installed xterm and it works fine.  thanks a million.:guitar:

---

### Post by iateshaggy on 2007-11-22
xterm is working but the default terminal still reboots.  is there a way for me to make xterm the default and remove the current default?

---

### Post by doorknob60 on 2007-11-22
I'm not sure how it works in Xfce, but in Gnome you go to System->Prefrences->Prefered Applications. I'ts probably fairly similar in Xfce.

---

### Post by mali2297 on 2007-11-22
> **iateshaggy said:**
> xterm is working but the default terminal still reboots.  is there a way for me to make xterm the default and remove the current default?

Run 
```

sudo update-alternatives --config x-terminal-emulator

```
in the terminal and you will get to choose the default.

However, you can probably get xfce4-terminal working if you follow the advice given in the link I gave you.

---

### Post by iateshaggy on 2007-11-22
i did that, but it still shows xfce as the terminal in applications.  i have to alt f2 to run xterm.

---

### Post by santiagoward2000 on 2007-11-22
> **iateshaggy said:**
> xterm is working but the default terminal still reboots.  is there a way for me to make xterm the default and remove the current default?

Go to Applications/Settings/Preffered Applications, go to the Utilities tab and select it there.

---

### Post by iateshaggy on 2007-11-22
done that, still not the default.  i'll try again later.  thanks for all the help so far.

---

