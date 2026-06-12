---
title: "iMac G5 &amp;*fans"
date: 2010-12-15
forum: Apple Hardware Users
---

### Post by Lodbrok on 2010-12-15
Greetings.

The fans on my computer go full speed all the time.
The wiki page on my iMac G5 Rev C mentions that I should apply this ([http://bersace03.free.fr/pub/Linux/iMac%20G5/windfarm-pm121.patch](http://bersace03.free.fr/pub/Linux/iMac%20G5/windfarm-pm121.patch)) patch to the latest Linux 2.6.24 source.

I skimmed the Internet for a bit, and still have no idea what to do.

Help, please?

---

### Post by cascade9 on 2010-12-15
I'm just gettign a timeout on your link, and I'm hardly a mac expert so I could be wrong on the following- 

Kernel 2.6.24 is ancient. Anything that needed patching on 2.6.24 has probably been rolled into the kernel a long time ago....

---

### Post by Lodbrok on 2010-12-15
Well, having installed 10.10 and all updates, I guess it's still not fixed.

---

### Post by cascade9 on 2010-12-16
D'oh. I saw 'fanspeed' and 'patch' and misread the rest. I was think that yo didnt have fan speed control (which ironically normally ends up with the fans running at 100%). 

I assume you've tried software? 

If that fails, all I can think of is to set the fans at 12v usign hardware ( probably wont work for the CPU fan). 

Why do you want your fans running at 100% anyway?

---

### Post by Lodbrok on 2010-12-16
Well, I don't. That's the point :)
They run full speed all the time, makes the computer quite noisy.
I want them to run full speed only when necessary, a.k.a. How It Works Normally.

---

### Post by teejmya on 2010-12-16
Taking a shot in the dark here. I have a Macbook, and most have the SMC chip, which controls system hardware, like the webcam, various leds, and most importantly, the fans.

So, here's what works for me. Try it and see what happens.
```

sudo apt-get install applesmc-dkms
sudo modprobe applesmc
echo [fanspeed] > /sys/devices/platform/applesmc.768/fan1_min

```Taking a shot in the dark here. I have a Macbook, and most have the SMC chip, which controls system hardware, like the webcam, various leds, and most importantly, the fans.

So, here's what works for me. Try it and see what happens.
```

sudo apt-get install applesmc-dkms
sudo modprobe applesmc
echo [fanspeed] > /sys/devices/platform/applesmc.768/fan1_min

```
Where it says [fanspeed], give it a value in RPM. 2000 is quiet but there, and usually 7000 or so is freakin' loud.

So, if that works, then make it a script to change it when you want.

Open gedit (Alt - F2, type gedit.)
Paste this in:
```

#!/bin/bash
modprobe applesmc
echo $1 > /sys/devices/platform/applesmc.768/fan1_min

```
Save it as "fan.sh" in your home folder.
Next, open a terminal window, (Ctrl - Alt - T) and type:
```

chmod a+x fan.sh

```

***
From now on, to change your fan speed, open a terminal (Ctrl - Alt - T), and type:
```

sudo ./fan.sh [fanspeed]

```

And we all lived happily ever after.

---

### Post by Lodbrok on 2010-12-16
Hm, I believe applesmc-dkms is for Intel macs only.

---

