---
title: "Macbook pro - santa rosa, dual monitor?"
date: 2007-11-27
forum: Apple Intel Users
---

### Post by nebhead on 2007-11-27
Hello, I am completely new to Ubuntu and linux in general. I have a Santa Rosa MacBook Pro with a Nvidia 8600 GT with 128MB VRAM and a 24-inch Samsung SyncMaster 245B monitor and I would like to use dual display with this monitor. I am using a DVI cable to connect my monitor with my MacBook Pro.
When I plugged it into my MacBook Pro it completely messes my resolution up on my MacBook Pro and nothing worked properly.
I tried going through all the dual monitor settings and my monitor was not listed. I tried selecting "Generic" then "1920x1200" and it still would not work.
So I reinstalled. I would really, really like to get this to work as I play a lot of games and do a lot of editing so I need a big display.
What have I done wrong/what should I do?

Thanks in advance.

---

### Post by nielsb on 2007-11-28
> **nebhead said:**
> Hello, I am completely new to Ubuntu and linux in general. I have a Santa Rosa MacBook Pro with a Nvidia 8600 GT with 128MB VRAM and a 24-inch Samsung SyncMaster 245B monitor and I would like to use dual display with this monitor. I am using a DVI cable to connect my monitor with my MacBook Pro.

When you say you want to use dual display, do mean that you want to have the output mirrored or that you want an extended display?

> **nebhead said:**
> 
When I plugged it into my MacBook Pro it completely messes my resolution up on my MacBook Pro and nothing worked properly.
I tried going through all the dual monitor settings and my monitor was not listed. I tried selecting "Generic" then "1920x1200" and it still would not work.
So I reinstalled

When you selected "Generic" as per above, where did you do that - through the UI Scrrens and Graphics or what? If you did it through any of the UI screens, you should be aware they have a tendency of messing up everything.

If you from command line executed this with your external screen connected (never mind that it probably doesn't show anything) what is the output:

```
xrandr -q
```


Niels

---

### Post by Saeonate on 2007-11-29
I went through a lot of unnecessary pain in getting a similar config to work on my MPB SR.  basically, thanks to nvidia's drivers, it is very simple.

-enable restricted drivers.
-run sudo nvidia-settings & configure accordingly.
-save & overwrite existing xorg.conf (unless you made some changes you want to keep, then at your discretion)

---

