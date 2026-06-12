---
title: "How to activate external monitor hooked up to laptop?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-10
I'm running Ubuntu 7.04 on my laptop, and trying to get an external monitor (a Dell) to work. I have it plugged into the monitor port in the rear of my laptop. My laptop's own screen works fine but I need a second monitor connected as well.

I have a dual boot with Win98, and when I boot to Win98 the second monitor automatically. But when I boot to Ubuntu, the external monitor's screen remains blank. Is there some special command I need to give to activate the external monitor?

The external monitor is an old one-- not one of these new flat panels, but one of those old very heavy ones that is around 1.5 feet (~.4 meter) deep. It's a Dell Trinitron monitor, model "UltraScan P780".

---

### Post by Nikron on 2007-06-10
You have to modify xorg =/

they easiest way is if you have an nvidia card, you can just do "sudo nvidia-xconfig --twinview"

---

### Post by Tux Aubrey on 2007-06-10
I too haven't been able to get my external monitor working properly (on a Compaq Presario 900).  I can have one monitor or the other but not both.  The external monitor over-rides the built-in one when it is plugged in.

The laptop's fnF4 monitor selection worked properly with Edgy (I could have either or both) but the upgrade to Feisty killed it (the working screen shudders but comes straight back as it was).

This machine has an older ATI graphics card and I have tried Xinerama but while it "stretches" the desktop to cover two screens, only one of them works.

Any other suggestions?

---

### Post by steveneddy on 2007-06-10
```
gksudo nvidia-settings
```

Look under X Server Display Configuration

You can set it up there to whatever your specs are.

---

### Post by abn91c on 2007-06-10
on most laptops just press the fn and f3 or f5 keys together, depending on the brand of laptop i t will work, the OS has nothing to do with that.

---

### Post by swarup on 2007-06-11
> **abn91c said:**
> on most laptops just press the fn and f3 or f5 keys together, depending on the brand of laptop i t will work, the OS has nothing to do with that.

Yes, on my laptop it is the fn + F3 key. But what this does is toggle between the laptop's own monitor, and the external monitor. It will not allow you to have both working at the same time, which is what I need. 

There must be some way to get both the laptop's own monitor and an external monitor working at the same time. I read through the comments of various people above, but this seemed only to relate with NVIDIA cards, which I do not have. 

I have a dual boot with Win 98-- and in Win 98 both monitors automatically work as soon as you boot up. 

So in Ubuntu 7.04, how can one get both the laptop internal monitor AND an external monitor working at the same time?

---

### Post by swarup on 2007-06-11
I just figured out how it works. Hopefully this may solve the problem for others as well: the fn + F3 key on my laptop is a toggle between having the internal monitor on, and having the external monitor on. Hit the key once, and one monitor goes off and the other on. Hit the key again, and it reverses which monitor is on and which off. Hit the key a third time and BOTH monitors go on. So here, for me at least, this problem is solved. Hope it may help for others as well.

---

### Post by gabrielrodriguez81 on 2007-06-12
Would any of you guys know how to have the second monitor's resolution be modified?

---

