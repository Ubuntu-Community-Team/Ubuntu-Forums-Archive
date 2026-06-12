---
title: "will not shut down"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by radj2 on 2006-08-24
I just installed ubuntu and all is so far so good,except when I try to shut down. I get all the usual info on shuting down but when it gets to "will now halt" nothing more happens. The only way out is shut down using reset button.

---

### Post by Ziox on 2006-08-24
> **radj2 said:**
> I just installed ubuntu and all is so far so good,except when I try to shut down. I get all the usual info on shuting down but when it gets to "will now halt" nothing more happens. The only way out is shut down using reset button.

It's been a persistant problem, I think it's a bug, try checking the bug reports for ubuntu....but you can try shutting down from the command line:

sudo poweroff

for some people that shuts down complete.

Don't ask why though, because I just don't know...:D

---

### Post by mssever on 2006-08-24
Could also be a hardware issue. At any rate, when it says, "will now halt" it's perfectly safe to hit the power button.

---

### Post by akniss on 2006-08-24
> **radj2 said:**
> I just installed ubuntu and all is so far so good,except when I try to shut down. I get all the usual info on shuting down but when it gets to "will now halt" nothing more happens. The only way out is shut down using reset button.

At the terminal type:
```
sudo shutdown now
```
and tell us what happens.  To reboot rather than shutdown, try:
```
sudo shutdown now -r
```

---

### Post by radj2 on 2006-08-24
Nope, none of that works . I found a thread at launchpad that indicates it's a common problem.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

### Post by Cubiq on 2006-08-26
Same problem here with latest 686 kernel.

I'm afraid the problem is in the kernel that is not perfectly compatible with certain hardware (mobo+cpu?). Anyway the only way around it that I found is recompiling the kernel using a debian config as a base.

I didn't do a parm-per-parm comparison of the two kernels to find out where the issue is, but probably it's somewhere around "power managment" :)

I can do a step by step tutorial if needed but probably it's not a "absolute beginner" task ;)

---

### Post by Frank Golden on 2006-08-26
> **Cubiq said:**
> Same problem here with latest 686 kernel.

I'm afraid the problem is in the kernel that is not perfectly compatible with certain hardware (mobo+cpu?). Anyway the only way around it that I found is recompiling the kernel using a debian config as a base.

I didn't do a parm-per-parm comparison of the two kernels to find out where the issue is, but probably it's somewhere around "power managment" :)

I can do a step by step tutorial if needed but probably it's not a "absolute beginner" task ;)
The bad part is in my case it only happens occasionly. No rhyme
or reason.

---

