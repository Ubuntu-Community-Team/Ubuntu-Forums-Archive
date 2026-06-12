---
title: "[SOLVED] command for closing a program"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Carnivorum on 2008-03-25
Bs'd

Which command do I use for closing an unresponsive program?

---

### Post by hyper_ch on 2008-03-25
```

kill PID

```

PID --> process ID... you can find it by issuing

```

ps aux | grep firefox

```
or whatever program you want. It will list then all running processes that have "firefox" in it. As alternative you can install htop
```

sudo apt-get install htop

```
and run it by issuing "htop". You can then browse up and down with the arrow keys and press F9 for killing the process (with optional different sigs to set).

---

### Post by adi_das on 2008-03-25
First right click on the panel bar and select add to panel.
Then select Force Quit.
When an program becomes irresponsive click on the force quit applet and click the irresponsive program.

---

### Post by Carnivorum on 2008-03-25
Bs'd

Thanks, I have that force quit Icon now on the panel bar.

But where can I find the official thank you button?

---

### Post by Carnivorum on 2008-03-25
Bs'd

When I try to find the PID of Firefox, this is what I get: 

eliyahu@eliyahu-desktop:~$ ps aux | grep firefox
eliyahu  15529  0.0  0.1   1756   236 ?        S    12:06   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
eliyahu  15533  3.7 15.3 238380 29304 ?        Sl   12:06   1:15 /usr/lib/firefox/firefox-bin
eliyahu  16579  0.0  0.4   2980   768 pts/0    S+   12:39   0:00 grep firefox

So what is now the PID of firefox?

---

### Post by LaRoza on 2008-03-25
> **Carnivorum said:**
> Bs'd

Thanks, I have that force quit Icon now on the panel bar.

But where can I find the official thank you button?

[http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

---

### Post by hyper_ch on 2008-03-25
> **Carnivorum said:**
> Bs'd

When I try to find the PID of Firefox, this is what I get: 

eliyahu@eliyahu-desktop:~$ ps aux | grep firefox
eliyahu  15529  0.0  0.1   1756   236 ?        S    12:06   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
eliyahu  15533  3.7 15.3 238380 29304 ?        Sl   12:06   1:15 /usr/lib/firefox/firefox-bin
eliyahu  16579  0.0  0.4   2980   768 pts/0    S+   12:39   0:00 grep firefox

So what is now the PID of firefox?

There are several. You see that that two of them run the firefox binary and one is just your search for "firefox". So kill 15529 and 15533 - very likely the 15529 will also kill the 15533 one.

---

### Post by girishv on 2008-03-25
If you know the name of the program, you can use pkill as well
pkill firefox
In the rare case when it fails, you can find the PID of the program with the command
pgrep -l firefox
-l is just to spit out actual program name in addition to PID. Then use kill to kill the command
kill pid


Girish

---

### Post by munch3 on 2008-03-25
You can add a FORCE QUIT shortcut to the panel...

---

### Post by tad1073 on 2008-03-25
You don't even have to use the PID. For instance, if Fx has become unresponsive, then:
```
killall firefox-bin
```

---

