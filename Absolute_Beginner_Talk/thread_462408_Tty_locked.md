---
title: "Tty locked?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by StillLearning on 2007-06-02
Hello, I just installed Ubuntu, and had no problem whatsoever. However, whenever I press "Ctrl-Alt-1-6", I cannot interact with the Tty. Tty1 still shows the messages from boot time, while Tty2 to Tty2 are black and unresponsive. Does anybody have a clue of what is going on?

Thanks in advance for the help...

---

### Post by ncappel1 on 2007-06-14
If you are using edgy, all the ttys are in one file, /etc/inittab find the lines that read:
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

and comment out the ones you want to disable, for example, to get rid of tty3:
2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4

In feisty, each tty is in its own file, navigate to /etc/event.d/ and find the files named ttyX where x is the number1-6. to disable them, you have to remane them to disabled.ttyX 
again, to disable tty 3, for example, you rename tty3 to disbled.tty3
reboot, then it should work!

---

