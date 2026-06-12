---
title: "Ubuntu not logging in"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by djstarrock on 2007-01-14
Hi Ubuntu won't let me log into my computer I put in my user name  and password the screen goes black then it goes back to the login screen. Could anyone help me. Its version 6.06

---

### Post by bodhi.zazen on 2007-01-14
Sounds like a problem with X.

You can Ctrl-Alt-F1 to get to a terminal and log in to the command line.

Did you do anything to change your kernel, X, etc ?

If not perhaps you could try to re-configure X:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.cong.bak
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

To get back to your gui - Ctrl-Alt-F7

??

---

### Post by wpshooter on 2007-01-14
Has it always done this or is this something new that just started.  And if just started what was the last thing you installed/changed before it started ?

You probably just need to reconfigure your Xserver.

---

### Post by djstarrock on 2007-01-14
Well i did go into the terminal to change the screen size to 1280x800.

---

### Post by floke on 2007-01-14
I'd try the reconfiguration as mentioned above. 
Can you log in as the root user (I think the username and the password are 'root')? If you can then it's something to do with the settings in your home directory. If not, then its a larger problem.

---

### Post by djstarrock on 2007-01-14
I can get into fail safe terminal.

---

### Post by djstarrock on 2007-01-14
How do you log into the root.

---

### Post by djstarrock on 2007-01-14
When I try to do that it asked for my password then it says login incorrect.

---

### Post by bodhi.zazen on 2007-01-14
Ubuntu does not allow root logins.

If you boot to fail safe you are root.

Otherwise use sudo

type your log-in password when prompted. You will not see text on the terminal as you type ...

To log in as root 

sudo su

---

### Post by djstarrock on 2007-01-14
What do I do when I am in the root.

---

### Post by bodhi.zazen on 2007-01-14
Try to reconfigure X

See my first post ...

If you are root you will not need sudo ...

---

### Post by djstarrock on 2007-01-14
How do you go on the next line without pressing enter.

---

### Post by bodhi.zazen on 2007-01-14
Not following you there ...

Enter each command (line) one at a time.

If you are talking about the configuration process, use the arrow keys to go up and down, space bar to select ....

---

### Post by rius09 on 2007-01-14
> **djstarrock said:**
> Well i did go into the terminal to change the screen size to 1280x800.

Well.... can your comp handle that resolution?

---

### Post by djstarrock on 2007-01-15
Yea its a MacBook Im running Ubuntu under parallels.

---

