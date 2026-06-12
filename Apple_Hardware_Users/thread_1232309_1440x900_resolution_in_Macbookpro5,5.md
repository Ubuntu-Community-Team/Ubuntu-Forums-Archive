---
title: "1440x900 resolution in Macbookpro5,5"
date: 2009-08-05
forum: Apple Hardware Users
---

### Post by shivathreya on 2009-08-05
I got 1440x900 resolution for Macbookpro5,5 with nvidia 9400M.

However, I am getting only 1280x800 in Jaunty. I have the latest NVIDIA driver 190.xx.

Regards,

Shiva :confused:

---

### Post by m038 on 2009-08-07
I also have the MBP 5,5 13inch, but my maximum resolution in OS X is 1280 x 800, not bigger.

So it isn't that strange that Jaunty doesn't go higher.

---

### Post by rifak on 2009-08-07
@shivathreya: im still in hardy and i know that jaunty uses a more modern xorg but try this:

```
gtf 1440 900 60
```

you'll get something like this:

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline **"1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync**

whatever your Modeline outputs, copy and paste it into the next command. for example, mine would be:

```
xrandr --newmode **"1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync**
```

then the following commands
```

xrandr --addmode LVDS 1440x900_60.00

xrandr --output LVDS --mode 1440x900_60.00
```


like i said, im not sure if that will do much, but its worth a try. if it messes anything, just logout then back in and itll undo any changes made. just ask if you need clarification.


@m038:
i am pretty sure that in os x, there is an update just released yesterday that fixes the resolution issues...maybe try that update in os x.

---

