---
title: "Data Incomplete in xorg.conf on boot up"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-25
When I try installing different drivers to get my ATI Radeon 9200 Se video card to stop freezing the screen or going blank, I get an error on boot up. 

Here is what I see on the problem during attempt to start Feisty's sign in screen, which BTW, I never see.

[B]Data incomplete in file /etc/X11/xorg.conf
Undefined "ATI Technologies, Inc. RV280[Radeon]" referenced by screen "Default Screen"
Problem parsing the config file
Error parsing the config file
Fatal server error
No screens found
[/B]
Any assistance in getting this resolved would be greatly appreciated.
kh

---

### Post by BoneKracker on 2007-04-25
That looks to me like a simple pointer error.  It tries to match screens, displays, monitors, devices, etc. based on their name.

If you've mistyped the name in one place, it won't match and you get that type of error.

Paste from one place to any other references that need to include the item
If they are identical, and you still have the error, then you might try eliminating any special characters.

---

### Post by kittyhawk63 on 2007-04-25
> **BoneKracker said:**
> That looks to me like a simple pointer error.  It tries to match screens, displays, monitors, devices, etc. based on their name.
If you've mistyped the name in one place, it won't match and you get that type of error.
Paste from one place to any other references that need to include the item
If they are identical, and you still have the error, then you might try eliminating any special characters.

I'll be sure to check this out. I do mistype more often than I wish to admit. Thanks for the tip.
kh

---

### Post by BoneKracker on 2007-04-25
With "eliminate any special characters", I should have added that the names can be whatever you want.  You can call it GPU or graphics_card for all X11 cares.

---

### Post by aberry5555 on 2007-04-25
if your using the fglrx drivers you can use

```
sudo ati-config
```

to set things straight, otherwise ( though you'll have to change any settings you made again) you can try

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by kittyhawk63 on 2007-04-25
aberry5555
Thanks for the input.
kh

---

