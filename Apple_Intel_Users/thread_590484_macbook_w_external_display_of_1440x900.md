---
title: "macbook w/ external display of 1440x900"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by hohllp on 2007-10-24
Hi all,

I've read through some posts on how to setup a 1440x900 external display for a macbook, however I did not find a port relating to the most recent version of Ubuntu 7.10.  Anyone know if there is a easy solution to getting my external display to work at 1440x900.  I'm not new to linux, so passing along an Xorg.conf file is acceptable, but I would also like to know if 7.10 has a more user-friendly fix that I may have missed.

Thanks a bunch,

Vince

---

### Post by cyberdork33 on 2007-10-24
> **hohllp said:**
> Hi all,

I've read through some posts on how to setup a 1440x900 external display for a macbook, however I did not find a port relating to the most recent version of Ubuntu 7.10.  Anyone know if there is a easy solution to getting my external display to work at 1440x900.  I'm not new to linux, so passing along an Xorg.conf file is acceptable, but I would also like to know if 7.10 has a more user-friendly fix that I may have missed.

Thanks a bunch,

Vince
there is a much better utility in Ubuntu 7.10 for setting that up.... Now whether it ends up actually working for you is another story.

---

### Post by hohllp on 2007-10-27
Hi all,

After a little research I fixed my problem using the info from this thread: 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Ubuntu_7.10_with_Intel_Graphics_Media_Accelerator_950")

Turns out the 'xrandr' is the holy grail of screen config.  First I reset my xorg.conf file:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

Then ran

```
xrandr -q
```

to get the code for my external display (TMDS-1 is this case)

Then:

```
xrandr --output TMDS-1 --mode 1440x900 --output LVDS --off

```

To set the external display to the desired resolution, and shut off the laptop display.  Works like a charm!

Hope this helps someone else out there :)

Vince

---

