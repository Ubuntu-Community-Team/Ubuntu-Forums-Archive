---
title: "Problem loading KDE"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by sideburnz17 on 2007-04-22
I'm absolutely new to running Ubuntu or any Linux dist. on my machine, so bear with me.

When I turned on my computer today, X didn't start (I think the default is KDE, not GNOME?) and went straight to a command prompt.  when i ran

start_kdeinit --new-startup +kcminit_startup

it said 

DISPLAY not set.

So I looked around online and tried

exec xterm -geometry +0+0

Which apparently wasn't the right thing to do, because I got the same error (sort of - xterm Xt error: Can't open display)

startx works fine, but I prefer KDE to GNOME.  What's going on, and how can I get KDE to work again, and how do I set it so that it takes me straight there instead of a command prompt (which happens every time now)?

Thanks in advance.

---

### Post by bobplano on 2007-04-22
ubuntu's default is gnome so if you want kde only you need to run
```
sudo aptitude install kubuntu-desktop
sudo aptitude remove ubuntu-desktop
```
then you can run kde only. also you might need to change the default session to kde which you can do before you log in. just click the options, go to change session then choose kde. once you type in your password choose to set kde to default

---

### Post by sideburnz17 on 2007-04-22
Fair enough - if i was using GNOME before then i'll just keep using it.  However, it looks different (I had to mess with the themes to get it close to what it was before), and I don't have the same options as before under the logoff command (I assume this is a side effect of it not starting X by default).  How do I get it to start up in X as opposed to having to do startx when it loads the command prompt?  the login process used to be from X.

---

