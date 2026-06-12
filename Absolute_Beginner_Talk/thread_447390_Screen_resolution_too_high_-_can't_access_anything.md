---
title: "Screen resolution too high - can't access anything"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ChrisE on 2007-05-17
I just installed Feisty Fawn on a Toshiba laptop with a resolution of 1024x768.

The system indicated that there was a driver problem, and that clicking on the driver button would resolve it.

However, the screen resolution is currently much higher than 1024x768, which means that most of my desktop is off-screen, and I can't access my control panels or anything like that.

Is there a shortcut I can use to launch the terminal?  (Not that I'd know what to do once I got there)

I really don't know where to proceed from here.

---

### Post by n8bounds on 2007-05-17
hit ALT and CTRL and F5
you will be sent to to non graphical console

log in like you would normally (type username, hit enter, type password (silent on the screen), hit enter)

say this in the shell:
```

sudo dpkg-reconfigure xserver-xorg

```

answer all the questions, always choose simple over advanced
when you get to the part about resolutions uncheck (space bar) all but the one resolution you WANT to see
when its done questioning you either reboot or say in the shell:

```

sudo /etc/init.d/gdm restart

```

replace gdm with kdm if you're using kubuntu

let us know..

---

### Post by ChrisE on 2007-05-18
This fixed the problem.

Thanks a lot.

---

### Post by n8bounds on 2007-05-18
U da man, way to go!

---

