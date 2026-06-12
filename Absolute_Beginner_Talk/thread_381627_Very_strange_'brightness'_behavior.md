---
title: "Very strange 'brightness' behavior"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-03-11
Hi everyone,
This is quite strange.
I compiled my kernel and all went fine. The thing is that when I turn my box on, brightness is very low. I can see what's on the screen but not much more!

About 1 hour later *-and this happens without my doing anything at all-* my brightness level goes up all by itself.

As far as I know, there are no ghosts in the house...
Thanks for reading.

---

### Post by xyz on 2007-03-11
Back under Dapper (and all the previous versions), I used to be able to adjust the brightness of my Toshiba Datellite A 40 by running:
```
sudo echo "brightness:1" > /proc/acpi/toshiba/lcd
```
I'd set it to in between 1 and 8.
Now with Edgy, I don't even have acpi:
```
root@luser:/proc# cd /acpi
bash: cd: /acpi: No such file or directory

```

---

### Post by xyz on 2007-03-11
Looks like there's a [BUG]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77026")

---

### Post by xyz on 2007-03-15
This is driving me nuts!
Well ...I compile my kernel [using this HowTo - Master Kernel Thread.]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=compile%2Ckernel")
As I wrote in an earlier post, brightness was very low for an hour or so and then, all of a sudden, simply 'brightened up' all by itself. This was the situation for a few days with the 2.6.20.1 - no way to set brightness there!

Now today, been working with the computer 2-3h. and no brightening in sight!

So I rebooted on kernel 2.6.17-11-386 and there's that good old brightness slider in Power Management. Too bad I compiled my kernel to end up seeing hardly anything on my screen!

I'll no doubt post on the Master Kernel Thread but, in the meantime, if anyone can give hand, I'd appreciate.

---

