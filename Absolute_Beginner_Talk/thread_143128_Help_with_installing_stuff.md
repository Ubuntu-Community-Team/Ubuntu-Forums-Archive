---
title: "Help with installing stuff"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by hawksigns on 2006-03-11
Ok, I've tried to download a few things... Nvu, a couple of antivirus things... and I can't get most of them to open at all let alone get them to acutally install.  I'm really new to Linux and while not an idiot with computers, I'm having a lot of trouble with some of the complicated instructions I'm running into with this stuff.

---

### Post by mstlyevil on 2006-03-11
[QUOTE=hawksigns]Ok, I've tried to download a few things... Nvu, a couple of antivirus things... and I can't get most of them to open at all let alone get them to acutally install.  I'm really new to Linux and while not an idiot with computers, I'm having a lot of trouble with some of the complicated instructions I'm running into with this stuff.[/QUOTE]


Here are a few guides that might help you get started.

[Ubuntu Linux Resources]("http://www.psychocats.net/linux/index.php")

[Unofficial Ubuntu Guide]("http://easylinux.info/wiki/Ubuntu")

[Breezy Customization Guide]("http://doc.gwos.org/index.php/BreezyCust")

These should help to get you started.

---

### Post by hawksigns on 2006-03-11
Ok, I followed the instructions for the .deb stuff in the first link, and it did something, but I still don't see the program anywhere on my computer.  Can you tell me what I did wrong?

I downloaded BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.deb to my desktop.

I opened a Terminal

I typed cd Desktop <enter> sudo dpkg -i BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.deb

and it did something, then I closed the Terminal window to see if it worked...
Did I miss something somewhere???

---

### Post by aysiu on 2006-03-11
Not all applications are graphical applications.
Not all applications that are graphical create menu entries.
Not all applications that create menu entries create them right away--sometimes you have to "refresh" the panel to show the newly added entries.

Are you using Gnome or KDE?

---

### Post by hawksigns on 2006-03-11
Gnome

---

### Post by mstlyevil on 2006-03-11
Try typing bitdefender in the terminal and see if it opens the program. If it does then you can create a custom icon using that command.

---

### Post by hawksigns on 2006-03-11
Ok, I'll try that.

Also, while trying to install Nvu the same way I found it had some dependencies: Unpacking nvu (from nvu_1.0final-1_i386.deb) ...
dpkg: dependency problems prevent configuration of nvu:
 nvu depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.
 nvu depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 nvu depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 nvu depends on libpango1.0-0 (>= 1.10.3); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 nvu depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 nvu depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing nvu (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvu

how do I find what it is that I need out of all that???

---

### Post by hawksigns on 2006-03-11
I don't think bitdefender worked afterall...

erin@Hawkins:~$ bitdefender
bash: bitdefender: command not found
erin@Hawkins:~$

---

### Post by aysiu on 2006-03-11
A few things:

1. In Gnome, to refresh the panel, press Alt-F2 and type ```
killall gnome-panel
```

2. The kinds of dependency problems you're running into with Nvu usually stem from conflicting repositories. Follow the instructions here to get up-to-date and non-conflicting repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

3. The command for BitDefender may not actually be ```
bitdefender
``` Most of the time the way to start an application is just to type its name. That isn't always the case. Unfortunately, I know nothing about BitDefender.

You can try typing ```
whereis bitdefender
```

---

