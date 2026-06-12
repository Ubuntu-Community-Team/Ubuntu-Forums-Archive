---
title: "NOOB doesn't understand the language"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by andamas on 2007-07-01
Hello,
I am trying to install and run feisty fawn. It failed to install the applications twice, but completed the install. The CD is fine and I used the alternate CD to install. When I reboot, it asks for the user name and password, which it accepts but then turns out the command line andrew@ubuntu:~$ (where andrew is my user name). What do I have to do to start the GUI?
Any and all help is appreciated. I am currently installing xubuntu on a second box to try that (from alternate CD as well).

---

### Post by @trophy on 2007-07-01
> **andamas said:**
> Hello,
I am trying to install and run feisty fawn. It failed to install the applications twice, but completed the install. The CD is fine and I used the alternate CD to install. When I reboot, it asks for the user name and password, which it accepts but then turns out the command line andrew@ubuntu:~$ (where andrew is my user name). What do I have to do to start the GUI?
Any and all help is appreciated. I am currently installing xubuntu on a second box to try that (from alternate CD as well).

type "startx" into the terminal.  If that doesn't work, let us know and you're going to have to configure X to get it to work.

---

### Post by andamas on 2007-07-01
OK, I typed startx at the end of the aforementioned line in terminal and got a bash error.
"-bash: startx: command not found"
I am ready and willing to learn!

---

### Post by oilchangeguy on 2007-07-01
did you install the server version, or the desktop version?

---

### Post by andamas on 2007-07-01
I am fairly certain that I downloaded the desktop version. The live CD was the desktop edition.

---

### Post by theredcross on 2007-07-01
I would guess that xserver-xorg didn't install, the first guess on a bad install is always to see if it burned properly. As I remember it when you bootup from the CD there should be an option to check the CD for errors. You said you used the alternate CD to install? Is there a reason you didn't install with the livecd?

---

### Post by andamas on 2007-07-01
Originally, the live CD stalled at installing applications, too. I have not yet figured out what is going on with that. I did check both CDs for consistency and the report came back positive. In another development, Xubuntu (from the alternate CD) installed great on my AMD K6 box! I appreciate the help.
andrew

---

