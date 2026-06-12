---
title: "Forcing scripts to start on login?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by bthomp01 on 2007-06-14
Hi all, I'm a brand new Ubuntu semi-user.  I've been tasked at work with rebuilding a hobbit server ([http://hobbitmon.sourceforge.com](http://hobbitmon.sourceforge.com)), as our previous install, which was on Ubuntu, completely died.  For some reason we couldn't restore the ghost image we had of the server and I've now finally got the entire thing working again.

It was much toil and a whole lot of internetting, but after a couple of weeks I was able to sort out all the kinks and install all the packages and all that... and it felt great, I learned a lot.  

But now I need to have the two hobbit scripts needed to run the server automatically start when the user logs in.  I tried adding symbolic links to the /etc/init.d/ directory but both scripts require the parameter of "start".

Is there a way to pass a parameter using a symbolic link, or is there some other way I can do this?

---

### Post by gerscht on 2007-06-14
what you're looking for are runlevels.
where are the two script? presumably in /etc/init.d/
All you need to do is make a link from the appropriate runlevel (3) to the initscript. The number in front defines in which order it will be started (in this example 90), the 'S' means that it should start ('K' is stop => kill)
```

sudo ln -s /etc/init.d/name-of-script /etc/rc3.d/S90-name-of-script

```
The runlevel will automatically add 'start' at the end, as all scripts in /etc/init.d/ have at least the options [start|stop|restart]

---

