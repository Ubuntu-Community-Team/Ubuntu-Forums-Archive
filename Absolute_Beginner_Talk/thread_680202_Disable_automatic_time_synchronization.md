---
title: "Disable automatic time synchronization"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-27
Hey Guys
I have looked up a few posts here but I couldn't really find the solution to what I am looking for:

You see
I am used to my clock being excatly 28mins and 37 seconds fast (don't ask me why) so I thought all I have to do is to  adjust my time and date settings and switch configuration to "manual".

unfortunately I have always find my clock to be synchronized despite me choosing manual.

What do I have to do to completely disable this?

---

### Post by taurus on 2008-01-27
Did you install ntp and have ntpd running at boot?

```
ps -A
```

---

### Post by Majorix on 2008-01-27
Sorry I don't understand what "excatly 28mins and 37 seconds fast" means. If you mean it should be behind the official clock, then there is practically no reason for that, and it will only bring you trouble with software and hardware.

---

### Post by disappearedng on 2008-01-28
Ok when I do ps -a i do see that my ps is in fact running. How do I disable it?

I need it because I have sleeping disorder and the only way I could wake up is to have multiple alarm clocks set at different timing between that interval to the actual timing so that when I see what time it is I will not be sure by how much faster the clock is that actual timing so that I will wake up.

This is recommended by my personal therapist.

---

### Post by dcstar on 2008-01-28
> **disappearedng said:**
> Hey Guys
I have looked up a few posts here but I couldn't really find the solution to what I am looking for:

You see
I am used to my clock being excatly 28mins and 37 seconds fast (don't ask me why) so I thought all I have to do is to  adjust my time and date settings and switch configuration to "manual".

unfortunately I have always find my clock to be synchronized despite me choosing manual.

What do I have to do to completely disable this?

Check and adjust your **/etc/ntp.conf** file, or remove **/etc/rc2.d/S50ntp** and maybe also /etc/rcS.d/S11hwclock.sh (although removing this last one could stuff up your Ubuntu time totally).

---

### Post by disappearedng on 2008-01-28
BTW How do I do that in the command?

When I do: sudo gedit /etc/ntp.conf it's completely empty. Is that normal?

How do I perform the other instructions on the command prompt?

---

