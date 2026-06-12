---
title: "Conky can't fetch sensor information"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Kossu on 2007-02-25
I get the error Conky: can't open '/sys/bus/i2c/devices/0-0050/temp2_input': No such file or directory

However I looked into it and noticed that the sensor information doesn't exist in that folder but in
/sys/bus/i2c/devices/9191-0290/

I tried making a symlink between the file in /sys/bus/i2c/devices/9191-0290/ and /sys/bus/i2c/devices/0-0050/temp2_input but I get access denied even when using root.


Is there a way to make conky read from /sys/bus/i2c/devices/9191-0290/ instead?

I greatly appreciate all help,
thank you very much in advance.

---

### Post by taurus on 2007-02-25
Have you tried looking into ~/.conkyrc?

---

### Post by Kossu on 2007-02-25
> **taurus said:**
> Have you tried looking into ~/.conkyrc?

No option there, however I noticed  that the folder containing the right info is also as a sub folder inside the directory where conky fetches the information. Tho for some reason the temperature is presented as 31000, instead of 31C. Is there a way to divide it with 1000 in order to get it look nicer?

Thank you very much

---

### Post by Kossu on 2007-02-25
mmk got it fixed, anyone with same problem, don't use i2c use this instead in conky
${execi 90 sensors | grep "CPU Temp:" | cut -c12-16 ;}C

edit grep and cut to fit yours.

---

### Post by lethu on 2007-05-23
Thank you for sharing : D! I had the same issue as you but got it fixed thanks to your method.

---

### Post by lethu on 2007-05-23
After searching and reading conky's config sample, I found a way better solution (actually the proper solution) : D.

By default Conky looks for the device files ("temp2_input" in this case) in "/sys/bus/i2c/devices/0-0050/" if you don't pass the "dev" parameter.

So what you have to do to make it work is just to add the right "dev" parameter, which is the device directory containing the "temp2_input" file, which in my case is "/sys/bus/i2c/devices/[COLOR="Red"]**1-002d**[/COLOR]/", thus my Conky's temperature variable should look this way : ```
${i2c [COLOR="Red"]**1-002e**[/COLOR] temp 2}C
```
Now it works like a charm : ).

---

