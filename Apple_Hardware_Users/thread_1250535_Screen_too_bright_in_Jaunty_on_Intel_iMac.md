---
title: "Screen too bright in Jaunty on Intel iMac"
date: 2009-08-26
forum: Apple Hardware Users
---

### Post by hoppings on 2009-08-26
I have Jaunty 64 bit installed on an alluminium Intel iMac 24 inch.
The screen is far too bright to use for any length of time without hurting the eyes.
I have searched in vain for information to correct this.
In Mac OS X there is an application called 'Window Shades' or something like it, to reduce the brightness of the screen but I cannot find anything like it in Jaunty.
Any ideas?

Success!
For the benefit of anyone else with this problem&#8211;
I just installed the new Ubuntu 9.10 on the 24 inch aluminium iMac using Boot Camp.
Have just discovered drivers for ATI graphics in Ubuntu and installed them - fantastic results. I could open the ATI settings and adjust the display to suit &#8211; exactly what I was looking for.

---

### Post by El Menda on 2009-08-26
Hi!
I have no idea if you can apply this to non netbooks, but give it a try.
Install xbacklight:
```
sudo apt-get install xbacklight
```

and after that try:
```
xbacklight -dec 15%
```
Execute it as many times or with the percent that you want.

If you went too far you can execute:
```
xbacklight -inc 15%
```

If it works for you maybe we can find a better solution.

---

### Post by hoppings on 2009-09-01
Thanks for the suggestion but it didn't work - Igot mesage saying "No outputs have backlight property".
It's a pity, but I cannot use Ubuntu with a screen as bright as it is.

---

### Post by hoppings on 2009-11-25
Success!
For the benefit of anyone else with this problem–
I just installed the new Ubuntu 9.10 on the 24 inch aluminium iMac using Boot Camp.
Have just discovered drivers for ATI graphics in Ubuntu and installed them - fantastic results. I could open the ATI settings and adjust the display to suit – exactly what I was looking for.
:D

---

