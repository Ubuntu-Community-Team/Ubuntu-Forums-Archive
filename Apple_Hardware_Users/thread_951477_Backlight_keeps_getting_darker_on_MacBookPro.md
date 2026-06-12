---
title: "Backlight keeps getting darker on MacBookPro"
date: 2008-10-18
forum: Apple Hardware Users
---

### Post by kjano on 2008-10-18
hi,

i am using a macbook pro 3.1 with intrepid beta and the nvidia driver. i finally managed to have the backlight keys F1 and F2 working but now i face another problem. when i change the backlight setting, it resets itself after some minutes to an average light level. then i use f2 to increase backlight again and some time later it goes down again.i have deactivated the shade setting in the gnome power management. the light is also turned down while moving the mouse or typing.

---

### Post by kosumi68 on 2008-10-18
I recognize this problem from my MBA, with comparable setup. I think the problem might be connected to the light sensor. What is the output of
```

hal-find-by-capability --capability light_sensor

```
on your system?

---

### Post by kjano on 2008-10-18
first of all thx for helping me:

/org/freedesktop/Hal/devices/macbook_pro_light_sensor

---

### Post by kosumi68 on 2008-10-18
Yep, this is connected to a bug in a fix to a bug in hal...

You need to edit (sudo) the file /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi, and remove MacBookPro3,1 from the list of matching keys for the light_sensor and keyboard_backlight.

After doing this and rebooting (or restart hal and X), the problem should not appear again.

---

The problem is that the fdi description is pointing to a device that does not get picked up. However, since it is listed (what you just showed), it will (most likely) still try to adjust the backlight based on the sensor reading. Assuming the error handling produces something like zero or -1 for the light sensor, it is consistent with what you experience.

Two LP bugs relevant to this problem: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894), [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918). I will create another bug for this problem.

---

### Post by kosumi68 on 2008-10-19
Bug report for this problem: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/285815)

---

### Post by kjano on 2008-10-19
thx again!

---

### Post by kjano on 2008-11-11
oh no! the problem is back again.....

---

### Post by transmition on 2008-11-11
Have you tried disabling the automatic brightness settings in the power manager?

---

### Post by kosumi68 on 2008-11-11
> **kjano said:**
> oh no! the problem is back again.....

If the problem is back again, i suspect you just updated the hal-applesmc package. Although turning the light sensor function off in g-p-m will work, as transmit suggests, another option is to also install the mactel version of gnome-power-manager, which will actually make the ambient light work as it should.

---

### Post by iva2k on 2009-01-17
Regular seemingly sporadic LCD backlight dimming on MacBookPro5,1 was driving me nuts too...

I have Intrepid and all drivers and packages from [MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA").
 
Here's how I solved the backlight problem for myself:

Configuration Editor > apps > gnome-power-manager > ambient
(You may need to enable Configuration Editor in your menus)
[LIST]
[*]correction_factor = 50
[*]correction_scale = 5000
[*]dim_policy = dark
[*]enable = yes
[*]poll_timeout = 1	//? this seems to have no effect, maybe after reboot?
[/LIST]

You can find some other numbers that will work for you. The important one is the correction_scale. It should be rather larger (5k..10k) to adjust for very small reading range from the light_sensor.

This fix should work until gnome-power-manager and/or drivers are patched to scale MacBookPro5,1 light_sensor to a reasonable range.

--
Ilya

---

