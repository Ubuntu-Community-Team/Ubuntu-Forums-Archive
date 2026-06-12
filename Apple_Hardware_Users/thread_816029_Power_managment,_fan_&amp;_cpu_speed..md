---
title: "Power managment, fan &amp; cpu speed."
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by mariguango on 2008-06-02
I'm install all things like in wiki (applesmc), but noise from fans too high, on the same temp and about the same rpm - like in mac os (temp about 60C, and fans on about 2000 rpm).

Do you know good solution for make my macbook more quiet?

P.S. I post my questions in different posts, cause i think this is matter questions.

---

### Post by cyberdork33 on 2008-06-02
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

---

### Post by mariguango on 2008-06-03
> **cyberdork33 said:**
> [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

thank you, but it don't make my fan slower or more quiet.
And you know, i first look at wiki, and then ask here )

---

### Post by kosumi68 on 2008-06-03
I have a similar problem. I run powernowd and laptop-mode on my Macbook Air, and when the AC is unplugged, the temp-core-fan system seems to be well regulated, and the machine feels both cool enough and silent enough. However, when running on AC power, the fan quickly moves up to top speed and stays there. I have looked at the more complex cpufreqd, but setting it ups seems like a great deal of work. The bottom line is that with the default settings in hardy, the temp-core-fan system is working like so so on the macbooks.

---

### Post by mariguango on 2008-06-04
this problem is the most matter now for me - if someone have any ideas or any working example of quiet and silent and cold macbook - let me know how you make this possible. I'm tired hear fans all the time.

Thank you.

---

### Post by kosumi68 on 2008-06-29
Lowering the display brightness to something medium seems to make the MBA cool enough. I also use these settings for powernowd:

```

#default file for powernowd, see man 1 powernowd
# 
# Options
OPTIONS="-q -m 2"

```

---

### Post by cvasilak on 2008-06-29
Hi there,

I am using a MacBook Pro C2D 2nd Generation. The only method so far that allows me to work without the noisy sound of the fans is to manual adjust them. That is if I do some pretty heavy work I set them to 6000. For medium size work I set them to 4500(which is good and quite).

You can download the scripts from the Macbook Pro Wiki and adjust them accordingly:

[https://help.ubuntu.com/community/MacBookPro#Temperatures%20&%20Fan%20Speed](https://help.ubuntu.com/community/MacBookPro#Temperatures%20&%20Fan%20Speed)

Unfortunately, the "auto" way doesn't work quite good in the current release (at least for me). I am hoping for the future :)

Regards,
Christos

---

