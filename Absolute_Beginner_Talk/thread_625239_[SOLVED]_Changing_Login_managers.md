---
title: "[SOLVED] Changing Login managers"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-11-27
So, say if I wanted to test and try xdm out temporarily, how would I go about disabling gdm and getting xdm to take over it's place ?

---

### Post by PeterJS on 2007-11-27
This will bring up a menu that will allow you to select with display manager you want to use.
```

sudo dpkg-reconfigure gdm

```

---

### Post by Dr Small on 2007-11-27
That worked, but now at bootup, I have no Login Manager loading, and I have to login via the command line and type:
```
sudo /etc/init.d/xdm start
```

Isn't it supposed to start automatically ?

---

### Post by PeterJS on 2007-11-27
> **Dr Small said:**
> Isn't it supposed to start automatically ?
Yes it is, which display manager did you chose from the menu when you ran dpkg-reconfigure?

---

### Post by Dr Small on 2007-11-27
xdm. Well actually, after I installed xdm it prompted me to configure it, and to choose which login manager I wanted to use. So I selected xdm from there. Then I tried restarting X (CTRL + ALT + SHIFT + BACKSPACE), and it restarted and took me to GDM!!

So, I went to vt1, logged in, and stopped gdm:
```
sudo /etc/init.d/gdm stop
```

It stopped it, and then I started xdm:
```
sudo /etc/init.d/xdm start
```

It worked perfect. So I rebooted, and it sat on the progress bar at the end for a little while and then took me to vt8 with all of the startup entries. So I went to vt1, logged in and started xdm again..

Any way to make xdm start at bootup ?

---

### Post by Dr Small on 2007-11-27
My apologies. I just tried again, and it worked. But, it was slow, because it was at the very end of the bootup process, and sendmail takes a looonnng time to load, so that is why it never came up at first.

Is there any way to change the startup order ? Because I saw GDM was at the top (close to it), and it said it was disabled... Went through the rest of the startup stuff... and finally started xdm at the very end.

Dr Small

---

### Post by jordanmthomas on 2007-11-27
I think the numbers on the scripts in /etc/rc*.d/ tell which order they are started in.  A lower number means something is started sooner.
This link may be of interest to you:
[http://www.linux.com/articles/53613](http://www.linux.com/articles/53613)
[https://help.ubuntu.com/community/InitScriptList](https://help.ubuntu.com/community/InitScriptList) (near the bottom, it says this:
> these numbers determine the order in which the various scripts get executed. S35mountall.sh is executed before S40hotplug.

In Arch, it's a lot simpler (as most things are :) )
```
DAEMONS=(syslog-ng network crond hal alsa @samba @sshd @mysqld @httpd @dhcdbd @networkmanager)
```
They're started in the order they are listed here, and ones with an @ are started in the background so other things can start up.

---

### Post by Dr Small on 2007-11-27
I figured it out.
I went into /etc/rc2.d and found S99xdm and saw S13gdm in there too, so I knew this was the startup, and the numbers were the order. So, I renamed S99xdm to S13xdm and rebooted, and it started as normal and fast as GDM normally would :)

Yes, debian is a little confusing, and it looks like Arch would be somewhat simpler :D

Thanks for all of the help!

Dr Small

---

### Post by PeterJS on 2007-11-27
Ok, first thing to do is figure out where in the boot order gdm is:
```

ls /etc/rc2.d/ | grep gdm

```We're looking in rc2, because 2 is the default run level. On my system I get:
```

peter@Osirus:~$ ls /etc/rc2.d/ | grep gdm
S13gdm

```The S is for start up, and it's in the 13th position. Now we can remove xdm and re-insert it at the same position gdm used to occupy.

```

sudo update-rc.d -f xdm remove
sudo update-rc.d xdm defaults 13 01

```

---

### Post by jordanmthomas on 2007-11-27
Also, if you're looking for login managers try looking up slim.  It's fast and looks nice (I don't like xdm myself).

---

### Post by Dr Small on 2007-11-27
@ jordanmthomas, thanks for the tip. I will try it out ;)
@ PeterJS, hey thanks :) I didn't know you could do it that way!

---

