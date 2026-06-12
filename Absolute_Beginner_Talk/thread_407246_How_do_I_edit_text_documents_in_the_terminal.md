---
title: "How do I edit text documents in the terminal?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by gogogo111 on 2007-04-11
Hey everyone, I am running 7.04 Beta right now, and I had everything working 100%. Then I decided when I was configuring xorg.conf for the custom resolution (1440x900), and I put HW191D (thats my monitors model number) as the monitor.

Well. Now when I boot up ubuntu I get a blue screen with a grey text box saying that x or gdm is broken because it doesnt know what HW191D is for the monitor name. I know how to use gedit for in gnome..but for editing in the terminal..what is the command?

If any one can help me, I would be very grateful. I told my friend to do the same thing..so I bet he is expeirencing the same thing as I am (He has the same monitor as me.)

Any replies would be great! :D

---

### Post by BarfBag on 2007-04-11
In my opinion, nano is the best terminal-based text editor.  It works the same way that GEdit does.  So, if you wanted to edit your xorg.conf:

> sudo nano /etc/X11/xorg.conf

---

### Post by meomike2000 on 2007-04-11
u use the command"sudo" to get root permission if u need it.
then i like to use "nano".

could look something like this:

sudo nano /etc/"filename"

hope this helps
mike

---

### Post by Iowa Dave on 2007-04-11
Roger that. Be sure to type "sudo" as the first thing on the command line, as shown. It makes you temporarily the "super user", which you have to be in order to edit xorg.conf.

When you press "enter" it might ask you for a password. It needs to be a password for an administrator-level user.

Good luck!

---

### Post by gogogo111 on 2007-04-11
Yup. Thanks guys, I got it working. nano rules!

---

