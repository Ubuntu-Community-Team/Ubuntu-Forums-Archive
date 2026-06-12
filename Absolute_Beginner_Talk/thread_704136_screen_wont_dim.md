---
title: "screen wont dim"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-22
i have a gateway laptop and i am running gutsy. I have just finished setting everything up the way i like it but now i have noticed that when i switch to battery mode the screen does not dim. 
I have set the screen to dim when on battery mode in the power management but it doesn't seem to do anything. 
the little window pops up saying the screen dimed but it does not dim.

is this a known problem?  is there anything that i can do to fix this?

it would not be such a big deal to me but it drains my battery in about two hours while in vista my battery lasts about three and a half to four hours.

---

### Post by spiderbatdad on 2008-02-22
There are a number of known bugs with gnome-power-manager...usually issues similar to yours refer to the screen going totally black. I think your screen is probably dimming by 5% of a large value and you cannot detect the dimming. See this bug report and read the whole thing. You may find what your looking for.[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833)

---

### Post by tjwoosta on 2008-02-27
thanks

---

### Post by tjwoosta on 2008-02-27
my problem seems to be quite a bit different from that one though,  for instance 

in my power management i set my  screen to dim to 50% when on battery


i get this when on battery
```

tj@tj-laptop:~$ cat /proc/acpi/video/VGA/LCD/brightness
levels:  100 37 12 25 37 50 62 75 87 100
current: 0

```
```

tj@tj-laptop:~$ cat /sys/class/backlight/acpi_video0/brightness
100

```
```

tj@tj-laptop:~$ cat /sys/class/backlight/acpi_video0/actual_brightness
50

```
```

tj@tj-laptop:~$ cat /sys/class/backlight/acpi_video0/max_brightness
100

```


theese guys are talking about there screen  totaly blanking out or switching dimness multiple times

i think my problem is completely different.

---

### Post by tjwoosta on 2008-02-29
can anybody help?

---

