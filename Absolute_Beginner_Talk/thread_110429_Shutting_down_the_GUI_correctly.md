---
title: "Shutting down the GUI correctly"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Chipmunk on 2005-12-30
I have searched through the forums and not found any reference to the problem I am having. In short, I use the ubuntu box mainly remotely from my windows machine via PuTTY, and unless I am on it directly, I want to shut down gnome. The method I am using is this: Ctrl+Alt+F1 to bring up tty1, then ```
sudo /etc/init.d/gdm stop
```
Then I logout of the TTY, and turn off the monitor, when I want to use the machine locally again, I login, then ```
sudo /etc/init.d/gdm start
```
The problem is, once in a while (around once a week) shutting down gdm leaves the display completely messed up, or it stops responding altogether (even ctrl+alt+backspace won't fix it). It also won't respond to ctrl+alt+F1 through F6, and I end up having to login remotely and shudown -r now from the terminal. Is there some other way I should be going about this that would prevent this problem?

---

### Post by lleb on 2005-12-30
instead of shtudown -r now, you could try just pulling up ps ax or top and see what is running.  it is possible that gdm just did not exit cleaning.  i had that a lot under RH9 on one of my point of sale systems.  tis why i moved over to debian running KDE.  have not had that issue since.

once you pull up ps ax and see what is running you can then check to see what to kill -9 or killall.  even if that does not work you can force the system into runlevel 3 via:

sudo init3
then 
sudo init5

and that should bring the GUI back to life.  worst case go all the way to init2 or 1 as both of them completly kill anything to do with the GUI, but when you bring the system back to init5 you will be running in GUI mode and should be  able to gain controll loclally again without rebooting the system.

---

### Post by Chipmunk on 2005-12-30
Excellent, thank you. I will try that if and when it does it again. My only concern is it may be the graphics card itself getting confused, if that's the case I'd have to get a new one, but it certainly gives me a new line of attack on it:)

---

### Post by lleb on 2005-12-31
hope it helps.

---

### Post by kingsidy on 2006-01-01
or as sudo you can type in > init 6 which restarts the computer.

---

