---
title: "the whining noise"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by Dale Cooper on 2007-10-25
Hello,

this is a known problem on MacBooks and other Core Duo machines, and there is a known solution :

I've added the line

```
echo 2 > /sys/module/processor/parameters/max_cstate
```

in the file /etc/init.d/acpid. I've tried to put it at the very end of the file, just before the exit statement, as seen in the wiki, and also at the end of the load_module() function as seen anywhere else, tehn rebooted

Guess what? My dear MacBook is still whining. Again and again.

Can anyone help me with that?

MacBook C2D 2.16 with Gutsy

Thanks in advance

---

### Post by volanin on 2007-10-25
If it is still whining, then remove that line!
It will make your macbook reach only C2 and never C3, increasing battery consumption.

By the way, I got the same computer as you.
And yes, the whining is always there, and even louder when the CPU load is low.
Setting the governor to performance instead of ondemand helped a little, but not completely.

---

### Post by Dale Cooper on 2007-10-25
> **volanin said:**
> If it is still whining, then remove that line!
It will make your macbook reach only C2 and never C3, increasing battery consumption.

Excellent suggestion, thank you, didn't even thought about that :lolflag:

> **volanin said:**
> By the way, I got the same computer as you.
And yes, the whining is always there, and even louder when the CPU load is low.
Setting the governor to performance instead of ondemand helped a little, but not completely.

Actually, the simple fact of moving the mice makes the whining noise disappear, but it comes back as soon as the mouse is inactive...
Also, the noise is louder when on charge than when on battery.
I'm going to try your governor idea, thanks.

It may be low, that little noise makes me mad after 10 minutes, I really need to get rid of it.

---

### Post by volanin on 2007-10-25
Give it a try indeed.
If it does not solve the whining... at least (by my experiments) the performance governor
consumes less power on the macbook while making your computer faster.

The instructions to enable it (and return to default case necessary) are here:
[Save your watts!]("http://ubuntuforums.org/showthread.php?t=590867")

Good luck.
:)

---

### Post by cyberdork33 on 2007-10-25
You might check that the mine doesn't come from a GPU cooler. Someone else was complaining of fan noise, and found that it was a fan on the video card, not the cpu. I don't know if you machine even has both, but it worth investigating.

---

