---
title: "remote access software"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-04-17
ok, i am having a bit of a problem, an online friend of mine is having trouble with her Windows machine and has asked for help. i'm more than willing to lend a hand, but none of my advice seems to be working. so my only option is to access her machine remotely, but i can't seem to find any remote access software that will do the trick, so if anyone can tell me a program that will do it it would be greatly appreciated. thaks

---

### Post by sharks on 2008-04-17
This will really help you:
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

---

### Post by atomkarinca on 2008-04-17
Have you tried terminal server client?

```
sudo apt-get install tsclient
```

---

### Post by rockerphil on 2008-04-17
sorry, i guess it might have helped if i said that i'm running Fluxbuntu Gutsy Gibson and am trying to access a Windows XP (ugh) machine

---

### Post by hyper_ch on 2008-04-17
install realvnc on your friends computer and then use krdc or krfb to connect to it.

---

### Post by timcredible on 2008-04-17
do not install vnc.  just use the rdp that's already built-in to windows.  tsclient is the gui frontend of rdesktop on linux that will let you access a windows  machine..  you'll have to turn on remote access on the windows machine first by right-clicking on the 'my computer' icon -> properties -> remote -> 'allow users to connect remotely to this computer'.

---

