---
title: "xubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by lalena on 2007-02-19
I just installed Xubuntu 6.10 alternate on a Dell gx150 w/ 256MB RAM, PIII, 10GB hard drive.  I know all hardware is good because I had windows 98 installed and working fine on it before.

I ran the Text install wiped drive and installed ext3 partition.  After it says it's completed the install and it's time to restart all I get is a login and then a unix prompt.  How do I get the graphical interface?:confused: 

I have nothing on this hard drive that can't be nuked.

---

### Post by Bachstelze on 2007-02-19
Are you sure you did a complete install and not a "Server" install ? What happens when you run *startx* ?

---

### Post by doobit on 2007-02-19
> **lalena said:**
> I just installed Xubuntu 6.10 alternate on a Dell gx150 w/ 256MB RAM, PIII, 10GB hard drive.  I know all hardware is good because I had windows 98 installed and working fine on it before.

I ran the Text install wiped drive and installed ext3 partition.  After it says it's completed the install and it's time to restart all I get is a login and then a unix prompt.  How do I get the graphical interface?:confused: 

I have nothing on this hard drive that can't be nuked.

At the command line prompt run:  sudo dpkg-reconfigure xserver-xorg
and follow the directions that show on the screen.

---

### Post by lalena on 2007-02-21
OK the problem seems to be that it failed on the step to install software.  So it seems like I've just got the base system installed.  The network setup seemed to work.  Is there a way I can try installing the software again from the CD or the network?

---

### Post by Maestro23 on 2007-02-21
> **lalena said:**
> OK the problem seems to be that it failed on the step to install software.  So it seems like I've just got the base system installed.  The network setup seemed to work.  Is there a way I can try installing the software again from the CD or the network?

At the command prompt, type: startx

---

### Post by lalena on 2007-02-21
get a lot of errors with startx.  Don't know how to get them off the machine.  But the isuse seems to be that a /dev/wacom doesn't exist and a bunch of lines of

Could not init font path element /user/share/fonts/x11/<somethingorother>

---

### Post by lalena on 2007-02-21
the last thing it says before bringing me back to a command prompt is 

Fatal server error:
could not open default font 'fixed'
X10: fatal IO error 104 (Connection reset by peer) on X server "0:0"
after 0 requests (0 known processed) with 0 events remaining.

---

### Post by lalena on 2007-02-21
OK.  I think the first CD I burned was bad.  Reinstalled, the Software Install portion worked this time.  :)

---

