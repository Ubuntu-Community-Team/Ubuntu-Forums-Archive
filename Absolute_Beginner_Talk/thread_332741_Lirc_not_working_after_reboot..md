---
title: "Lirc not working after reboot."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by JayRoe on 2007-01-06
I have to run "make install" in "/usr/src/lirc-0.8.1pre2/" after each reboot to get lirc to work. How do I fix it?

Here's what the log returns if I write "lircd"
```
Jan  6 19:14:02 ubuntu lircd: lircd(realmagic) ready
```
And here's what I get if I run "irw" afterwards.
```
Jan  6 19:14:31 ubuntu lircd: accepted new client on /dev/lircd
Jan  6 19:14:31 ubuntu lircd: readlink() failed for "/dev/lirc"
Jan  6 19:14:31 ubuntu lircd: No such file or directory
Jan  6 19:14:31 ubuntu lircd: could not create lock files
Jan  6 19:14:31 ubuntu lircd: caught signal
```
After having run "make install", "lircd" returns this
```
Jan  6 19:21:34 ubuntu lircd: lircd(realmagic) ready
```
and "irw" returns this
```
Jan  6 19:22:00 ubuntu lircd: accepted new client on /dev/lircd
```

---

### Post by energiya on 2007-01-06
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=163496"). The start-up script doesn't work as it should (you still have to run "sudo lircd" in a terminal or make a script and run it), but it works.

---

### Post by JayRoe on 2007-01-06
Thanks for the reply, but that doesn't work for me. As you can see lircd keeps returning "readlink() failed for "/dev/lirc"" "No such file or directory". I have to type make install after each reboot before it works.

---

### Post by energiya on 2007-01-07
if you have a /dev/lirc0 try 
```
ln /dev/lirc0 /dev/lirc
```
and if it works, make a start-up script

---

### Post by burns1111 on 2008-02-10
Hey there,

  I had the same issue.  I am using a Realmagic remote with the infrared serial port receiver.  After doing the "make install" for lirc, it would work just fine, but would stop working after reboot.

  I found that by changing a line in /etc/lirc/hardware.conf to:

DEVICE="/dev/ttyS0"

  it worked fine after rebooting.  Maybe this will help you as well.

---

### Post by egroeg85 on 2008-02-20
Ok, so this really has nothing to do with this post, but I'm having a problem that would fit under the same title.  I had lirc working just fine, but today my computer froze (braid screensaver bug), and since hard rebooting I can't get lirc to work any more.  I have the lirc package installed from Synaptic and also IRKick so I could configure via GUI.  I'm using a Creative SB Live Drive 5.1 with a RM900 remote.  I've tried everything I can find and best I can tell is that there is some sort of driver issue.  lirc seems to be running ok but it doesn't recognize any input.  Does anybody have any ideas?

---

