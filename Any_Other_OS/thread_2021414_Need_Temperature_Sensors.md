---
title: "Need Temperature Sensors"
date: 2012-07-09
forum: Any Other OS
---

### Post by Deeplove on 2012-07-09
Hey all. With my failed attempt at Ubuntu, I managed to get Mint to work. Since I'm on a Folding@Home team, I usually have my PC running 24/7 as much as possible. So, I need programs for temperature readings. I'm totally new with Linux and I'm trying to grasp the whole download and run it off the terminal thing.

What's the best temperature sensor I can get and how to I go about downloading it, running it and do I always have to run them through the terminal for them to work?

Thanks.

---

### Post by Lars Noodén on 2012-07-09
There's the packae [lm-sensors](http://packages.ubuntu.com/precise/lm-sensors) in the repository.  I find that, for the most part, it works.  There are sometimes readings or sensors that are off, though.

---

### Post by Deeplove on 2012-07-09
nothing that works real time or do i just have to keep using sensor on the terminal?

---

### Post by buzzingrobot on 2012-07-09
> **Deeplove said:**
> nothing that works real time or do i just have to keep using sensor on the terminal?

Various applets/extension that display temperature readings at specified intervals are available. They will use lm_sensors behind the scene.

---

### Post by Habitual on 2012-07-09
> **buzzingrobot said:**
> Various applets/extension that display temperature readings at specified intervals are available. They will use lm_sensors behind the scene.

conky is one such program. This can put a sensors output right on the desktop and conky could update that once a min. or so.

Here's a conky snippet:
```

# Static and Variable Values used by Habitual/John Jones

# Static Values
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
draw_outline no
draw_borders no
uppercase no
draw_shades no
draw_shades yes
double_buffer yes
border_width 0
text_buffer_size 2048
default_color white
update_interval 1.0

# Variable Values # These values are the ONLY thing that change from widget to widget
alignment tm
gap_x 00
gap_y 40
minimum_size 100 1
maximum_width 200

TEXT
CPUTemp is ${execpi 1 [COLOR=Red]sensors[/COLOR] -f | tail -2 | head -1 | awk '{print $2}'}

```

the [COLOR=Red]sensors[/COLOR] binary may be 1-off here, (I don't have, or use Ubuntu/LinuxMint any more)

YMMV

---

### Post by Deeplove on 2012-07-10
Thanks guys. I'll check them out as soon as I'm done folding this one project.

---

### Post by pqwoerituytrueiwoq on 2012-07-10
which version of mint are you useing?

mate has a sensors applet that works in your panel
you will need to update mint's mate destkop for gpu sensors [[link]]("http://mate-desktop.org/install/#linuxmint")
if you are using the xfce release candidate there is a xfce4-sensors-applet
you can also use the mate version my using xf-applet
be sure to enable the xfce 4.10 ppa under software settings

i have had a issue in cinnamon with conky messing up my minimize and restore actions
you may want this
[http://cinnamon-spices.linuxmint.com/extensions/view/13](http://cinnamon-spices.linuxmint.com/extensions/view/13)

---

### Post by Lemuriano on 2012-07-10
Try

 ```
sudo apt-get install xsensors
```

---

### Post by Deeplove on 2012-07-10
Linux Mint 13 is what I'm using.

---

