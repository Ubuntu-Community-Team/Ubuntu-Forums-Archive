---
title: "Installed Sound Drivers Now won't login"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-05-28
hi, 

wonder if you can help...

I just installed AC97 sound drivers on my sys, but after rebooting I get an error stating that the session lasted less than 10 seconds and that I should try failsafe...

failsafe does the same...

I can get to log into the terminal though, but the problem is that I have no idea what I would change...I guess the simplest way of solving this would be to disable the soundcard maybe?  or perhaps that's using a sledgehammer to crack a nut?

any help very gratefully received...thanks guys

HG

---

### Post by taurus on 2007-05-28
The first thing I would do is to check for disk space to make sure it's not 100% full.

```
df -h
```

---

### Post by Her Ghost on 2007-05-28
checked that - got plenty of room free.

I think it is related to the soundcard, because I don't get the drumroll ubuntu sound when it boots anymore..

---

### Post by Her Ghost on 2007-05-28
error message:

```

Your session lasted less than 10 seconds...etc etc

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: Running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "leigh"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared file: No such file or directory



```

anyone help?

---

### Post by Her Ghost on 2007-05-29
can anyone help at all with this, please?

I can't log into Ubuntu anymore, and it's starting to look like I'm going to have to reinstall, which will cost me all my settings because I can't back up my /home directory!

The drivers I installed were from Realtek, and the instructions were to run ./install  this I did, and it went through a huge installation script (I can't post it, cos I can't get on the net from ubuntu to copy/paste).  When I rebooted, I get the error message in the above post about libasound.so.2

I've searched the forums and there doesn't appear to be anything similar.

What I need, I guess, is:

1. Can I uninstall the Realtek drivers and undo the damage?  If so, how?
2. Could I just install the original sound drivers that worked back over the Realtek ones?  Again, how? :)
3. Does anyone know of a cunning way of getting my /home folder on a usb stick - it mounts when I plug it in under x, but I don't know how to do it on the command line - there are hundreds of entries in the /dev folder :(

Thanks for any help

---

### Post by Her Ghost on 2007-05-30
last bump now...

---

### Post by si_harp on 2007-06-11
Hi, Im having a similar problems too.

[http://ubuntuforums.org/showthread.php?t=470589](http://ubuntuforums.org/showthread.php?t=470589)

Anyone got any ideas?

Thanks. si

---

