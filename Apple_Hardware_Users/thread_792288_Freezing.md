---
title: "Freezing?"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by DomnizkyDesign on 2008-05-12
For some reason, my install of 8.04 constantly freezes whenever I change something. These changes are:

removing the AC cord.
closing a program.
switching between spaces.
letting tooltips pop up.
waking up from screensaver.

What's going on? Should I just back up my data and reinstall 8.04?

---

### Post by DomnizkyDesign on 2008-05-14
I went and reinstalled my OS.

Still freezing.

Any ideas?

---

### Post by flaggh on 2008-05-14
Can you please provide more information on the computer you are running this on.  Also, it would help if you posted the contents of dmesg and dmesg.0 after a crash.

---

### Post by DomnizkyDesign on 2008-05-15
its:
Ubuntu 8.04 ppc running on an Apple iBook G3 (800MHz) with 638MB RAM and 30GB HDD.

It's not dual-booting or anything like that, it's a standard full-install.

Strangely, when the computer crashes, or freezes, whatever, the mouse still moves. But it's cursor is frozen. What I mean by that is:
If I was moving a window, it remains a grabbing-hand. If I was writing something, it'll stay an insertion point. If I was pointing at a link, pointing at empty space... you get it.


As for the console messages, how can I go about getting those messages?

Also... holding down FN and hitting F12 still ejects the disc, even when the system's locked up.

I have no idea what's going on.

---

### Post by flaggh on 2008-05-15
Try hitting Ctrl+Alt+F2 and see if this gets you to a console.  You could try typing:
```
/etc/init.d/gdm restart
```
to restart X.  I forget if you have to hit Ctrl+Alt+F7 after that to go back to your workspace.  If you can't figure out how to do this, but manage to get to a console, you could type
```
sudo shutdown -r now
```
to safely reboot.

To get dmesg, open a terminal by typing Alt+F2 and running
```
gnome-terminal
```
Then at the terminal you can just type
```
dmesg
```
and to get the other log file
```
cat /var/log/dmesg.0
```

---

