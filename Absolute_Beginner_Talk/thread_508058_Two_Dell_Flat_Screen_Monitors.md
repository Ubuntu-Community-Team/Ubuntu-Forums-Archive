---
title: "Two Dell Flat Screen Monitors"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by oconnor on 2007-07-23
Hello I just installed ubuntu (7.04) on my Dell Presion 340 that I used to run XP on and I have two flat screen monitors.   The issue is that I just get the same screen on both screens.  So how do I ask ubuntu to notice that I have two monitors and act accordingly?

---

### Post by EXCiD3 on 2007-07-23
You need to configure your /etc/X11/xorg.conf file to use both monitors.

I can only help you if you have an nvidia graphics card. In order do this with a GUI, start Terminal and type this:
```

sudo nvidia-settings

```
You need to do this from terminal in order to have rights to modify xorg.conf.

Next configure you monitors using the Nvidia-Settings and choose "Save to X Configuration File"

Nvidia-Settings should look like this, but have 2 monitors in the "Layout" section.
[IMG]http://nicomedia.math.upatras.gr/~oxy/shots/nvidia.png[/IMG]

Configure them to have one to the "Right of" the other monitor. This will also not modify the default settings, allowing correct settings if you decide to unplug one of the monitors.

If you are using the newest drivers, make sure you select "Merge" when saving to X Configuration File as this will not overwrite the file and erasing the current config, but add the sections needed.

---

### Post by oconnor on 2007-07-25
Thanks for the reply but it appears as if I do not have a nvidia video card because when I run:
"sudo nvidia-settings" it says  "command not found".

So how do I figure out what type of video card is in there? 

Thanks!

---

### Post by bodhi.zazen on 2007-07-25
First since it is a graphical app you should : ```
gksudo nvidia-setings
```

You need to install the nvidia driver first.

---

### Post by oconnor on 2007-07-25
Ok, when I type:
gksudo nvidia-settings I don't get an error but nothing seems to happen.  I just get the $ prompt back.  I was expacting to get that GUI in the screen shot that EXCiD3 posted.
?

---

### Post by jaffamuffin on 2007-07-25
apt-get install nvidia-settings

---

### Post by EXCiD3 on 2007-07-26
Yes, you need to install the nvidia driver first. i would recommend using ENVY to install it, as the repositories can be out-of-date with these things: [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Install this and use it to install the newest Nvidia driver, then ```
gksudo nvidia-settings
```
will be usable. ;)

---

### Post by dagrump on 2007-07-26
let's start over, open a terminal & try "lspci" to see what's lurking (I didn't notice anything in your post that you had a nvidia card).

Oh post it here.

---

### Post by EXCiD3 on 2007-07-26
I expressly stated in my little howto that it was specifically for **nvidia** cards only:
> **EXCiD3 said:**
> I can only help you if you have an nvidia graphics card.

I assumed that he had nvidia when he attempted to do what i previously posted.

however he may not have noted that...If it detects a nvidia card, do the above steps...if not...find someone who knows how to do that with an ATI card...Thanks for thinking of that, as i completely forgot about that command at the moment ;)

**EDIT: READ THIS!!!**

I just google his model and PC World stated that it comes with a Dell Quadro4 700 XGL graphics card, Quadro4 being a NVIDIA card. All the stuff previously posted is relevant to oconnor's problem. Please see my last post for installing the NVIDIA driver through ENVY, after which you can configure dual monitors as i previously posted.

---

### Post by oconnor on 2007-07-27
Ok so I did the "lspci" command and there's no mention of a NVIDIA anything.  But there is this:
VGA compatible controller:  ATI Technologies Inc Radeon RV100 QY

?? (Thanks a lot btw - I'm certainly learning a lot.)

---

### Post by EXCiD3 on 2007-07-28
Ok so you need to install the ATI driver instead. You can still use ENVY to install it. Just go here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Envy will download and install both the Nvidia and ATI drivers, however i have never used Ubuntu on an ATI card so I can help you no further. Hopefully there will be some graphical configuration that is pretty simple to use. Sorry i cant help anymore! ;) Good luck!

---

