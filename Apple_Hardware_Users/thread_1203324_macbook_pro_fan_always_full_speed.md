---
title: "macbook pro fan always full speed"
date: 2009-07-03
forum: Apple Hardware Users
---

### Post by rangervert on 2009-07-03
Hi,  I've got an macbookpro intel (core2duo 2.16 ghz) 2.1 or 2.2 (I don't remember exactly) with ubuntu intrepid up to date.  I've got applesmc launched;  directory /etc/devices/applesmc.768 show fan1_min = 2000 fan1_max = 6000 fan1_output =6000 (same thing for fan2)   I'm diplaying my fan speed and my core temperature on desktop and it appears that my fan are always running at full speed even when my core are only 50 °C.   It is very noisy!  It 've read all possible forum thread and I did not find the solution :( ! Does anyone know this issue and best of all know how to solve it?  thanks a lot for your help

---

### Post by nathanid95 on 2009-12-05
The fan and power systems on a MacBook/Pro are controlled by Mac OS. There isn't any way I know of to slow it down from Ubuntu. 
This shouldn't be due to a problem as much as a result of the nature of the machine.

---

### Post by linuxopjemac on 2009-12-06
read the following, but please be careful with adjusting fans. It can ruin your laptop...

[https://help.ubuntu.com/community/MacBookPro2-1_2-2/Intrepid#Manual%20Fan%20Speed%20Control](https://help.ubuntu.com/community/MacBookPro2-1_2-2/Intrepid#Manual%20Fan%20Speed%20Control)

---

### Post by dennis123123 on 2009-12-06
> **nathanid95 said:**
> The fan and power systems on a MacBook/Pro are controlled by Mac OS. There isn't any way I know of to slow it down from Ubuntu. 
This shouldn't be due to a problem as much as a result of the nature of the machine.

@nathanid95 Please stop posting these BS replys about Macbooks... this is the second one i've seen today without actually looking for them.


@op:

applesmc should give you access to control the fan speeds. As root, try:
```
# echo 3000 >/sys/devices/platform/applesmc.768/fan1_min
```

(that line is taken straight from my Macbook, to set the minimum speed to 3000rpm instead of the default 2000)
and see if you get any errors returned.

Other things I could think of... is your /sys/devices/platform/applesmc.768/fan1_manual
set to 1? 0 is automatic (slows down when not needed) and 1 is manual (user sets speed)

---

