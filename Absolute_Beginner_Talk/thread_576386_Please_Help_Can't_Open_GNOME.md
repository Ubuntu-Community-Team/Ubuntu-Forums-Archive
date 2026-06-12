---
title: "Please Help Can't Open GNOME"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by lorsban on 2007-10-15
Hi guys,

I've been using Ubuntu 6.06 on my laptop for a month or so with no problems. Then I made the mistake of messing around with the login configuration so it never asks for a login. Right after that, I couldn't open anything and after restarting, I get an error message:

"Your session lasted less than 10 seconds. If you have not logged out yourself this could mean that there is some installation problem or you may be out of disk space (I've got 98% free). Try logging in with one of the failsafe sessions to see if you can fix this problem."

So, none of the other sessions worked except the terminal. Which I don't really know how to use. I've looked at the documentation and there's no command prompt/line that'll undo what I did. So, I'm stuck. The only other option I have is to re-install Ubuntu and start from scratch. 

I'd appreciate any advice you can give. 

regards,

lorsban

---

### Post by sayuki288 on 2007-10-15
sudo dpkg-reconfigure gnome-session

---

### Post by lorsban on 2007-10-15
Thank you very much for your speedy reply! I'll try that when I get to my pc at home. 

In case it's relevant, here's what shows up when I expand the error message:

/etc/gdm/presession/default: registering your session with wmtp and utmp
/etc/gdm/presession//default: running: /usr/bin/sessreg -a -w /var/logwtmp -u/var/run/utmp -x "var/lib/gdm/ :O.Xservers" -h "" -l ":O" "rob"
/etc/gdm/Xsession: beginning session setup

(x-session-manager:4778 ): gdk-warning**: locale not supported by xlib
(x-session-manager:4778 ): gdk-warning**: cannot set locale modifiers
(gnome-session:4778 ): libgnomevfs-warning**: unable to create ~/.gnome2 directory: permission denied
could not create per user gnome configuration directory `/home/rob/.gnome2/': permission denied

---

### Post by lorsban on 2007-10-16
Ok, I tried the suggestion and it gave me another error message: package gnome is not installed and no info is available. 

I did this with the terminal failsafe session.

---

### Post by lorsban on 2007-10-18
Decided to install Ubuntu again. Also got a backup program which I'm gonna keep a copy of on an external disk. Fortunately, it only takes a few minutes to install ubuntu.

---

### Post by SunnyRabbiera on 2007-10-18
hmm odd, if this happpens again you might want to check synaptic via the terminal to see if it messed up your gnome.

---

### Post by L0rd_D4rk on 2007-10-21
I have the same problem, I tried to make a **sudo dpkg-reconfigure gnome-session** and I get this error:
```
The generated cache was invalid.
```

any ideas? where is that cache and how can I repair it?

---

