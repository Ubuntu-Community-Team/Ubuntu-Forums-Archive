---
title: "Backlit Keyboard automatically on"
date: 2012-10-06
forum: Apple Hardware Users
---

### Post by alexferreirag on 2012-10-06
I have a macbook pro and am running Ubuntu 12.04. Every time I turn on my computer the backlit keyboard turns to the maximum automatically and I have to lower it to zero. This is not a big deal, but it is annoying... Anyone know how to configure ubuntu to not turn on the backlit keyboard when the computer turns on?

---

### Post by Sileem on 2012-10-06
It's not the best solution, but add
```
echo '1' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
```
to /etc/rc.local
This will lower the brightness to the lowest possible value at boot, from there you can leave it (its hardly noticable) or just hit the brightness down key once. For some reason, 0 doesn't work (at least for me)

---

### Post by alexferreirag on 2012-10-06
> **Sileem said:**
> It's not the best solution, but add
```
echo '1' > /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
```
This will lower the brightness to the lowest possible value at boot, from there you can leave it (its hardly noticable) or just hit the brightness down key once. For some reason, 0 doesn't work (at least for me)
I am not allowed to do that command, not even with sudo, so am I supposed to replace the '0' with a '1', a 'echo '1'', or to add a '1' or 'echo '1'' (I am editing the file through nano)?

---

### Post by nm_geo on 2012-10-06
> **alexferreirag said:**
> I am not allowed to do that command, not even with sudo, so am I supposed to replace the '0' with a '1', a 'echo '1'', or to add a '1' or 'echo '1'' (I am editing the file through nano)?

Try 
```
sudo su
```

Before the echo command

---

### Post by Sileem on 2012-10-06
> **alexferreirag said:**
> I am not allowed to do that command, not even with sudo, so am I supposed to replace the '0' with a '1', a 'echo '1'', or to add a '1' or 'echo '1'' (I am editing the file through nano)?

Whoops, sorry, I meant to say add that line to the file /etc/rc.local

---

### Post by will1982 on 2012-10-06
Solution seems to work for me. Thanks guys!

---

### Post by alexferreirag on 2012-10-07
> **Sileem said:**
> Whoops, sorry, I meant to say add that line to the file /etc/rc.local
Yep, now it works!

---

### Post by Sileem on 2012-10-08
However, there are some problems with this method, the backlight will turn on when you log out, and randomly when it wakes up.

---

