---
title: "I installed TightVNC via Synaptic and Dont See Where Its Installed"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-28
I have been trying to figure out the the best way remote my linux computers from wndows and decided to try TightVNC.  Since it was in Syaptic, I figured it would work out of the box.  I installed it using synaptic and now i can see where the program has been installed and I don't know how to activate.  Anyone with experience with this please point me in the right direction.

Thanks in advance,

VC

---

### Post by margori on 2007-10-28
If there is no icon when any program is installed, then it means that it migth to be run throug the terminal.

In properties of the packages, you can see all files installed. Those which installed in /usr/bin are the files to execute. So you have to launch a terminal and type the name of the file.

For example, for running de XVNC4Viewer:

~# xvnc4viewer 192.168.x.y

---

### Post by videocheez on 2007-10-28
> **margori said:**
> If there is no icon when any program is installed, then it means that it migth to be run throug the terminal.

In properties of the packages, you can see all files installed. Those which installed in /usr/bin are the files to execute. So you have to launch a terminal and type the name of the file.

For example, for running de XVNC4Viewer:

~# xvnc4viewer 192.168.x.y

Thanks man that was good advice.  it didn't work but when I browsed /usr/bin and found the file XVNC4Viewer and ouble clicked on it and it worked.  I was wondering do you know how to put a shortcut on my desktop so I don't have to dig trhough my directories to activate a file.

Thx,

VC

---

