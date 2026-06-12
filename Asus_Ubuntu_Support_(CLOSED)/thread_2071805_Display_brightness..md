---
title: "Display brightness."
date: 2012-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by vinay_nadig on 2012-10-16
I have an Asus 1225C netbook and I can adjust the brightness through the power settings.

But the lowest setting in the brightness panel is still a bit too bright for me. So, I was wondering if there is a way to decrease the brightness even further.

I have tried the /usr/lib/gnome-settings-daemon/gsd-backlight-helper and even when I set the value to 0, the brightness does not go to the level that I am comfortable with.

Anyone know of a way to do this? Please feel free to ask any information needed.
Any help would be appreciated.

---

### Post by zezadas on 2012-10-16
try changing in /sys/class/backlight/"wherever you got hehre"/brightness

---

### Post by PowerBarry43 on 2012-10-16
you could try installing xbacklight

```
sudo apt-get install xbacklight
```

then you can set the backlights brightness as a percentage from the terminal e.g:

```
xbacklight -set 10
```

Barry

---

### Post by vinay_nadig on 2012-10-16
> **zezadas said:**
> try changing in /sys/class/backlight/"wherever you got hehre"/brightness
I checked the contents of the brightness file and it is already 0.
I am not sure if negative values will have any effect.

---

### Post by vinay_nadig on 2012-10-16
> **PowerBarry43 said:**
> you could try installing xbacklight

```
sudo apt-get install xbacklight
```

then you can set the backlights brightness as a percentage from the terminal e.g:

```
xbacklight -set 10
```

Barry
I tried this utility. But for some reason, it does not have any effect on my display.
Even```
xbacklight -get
``` does not give any output.
Tried the program with sudo too. no luck.

---

### Post by zezadas on 2012-10-16
maybe thats your minimum, on windows could you get lower?

in some more advanced way, maybe you can modify the drivers and edit the voltages

---

### Post by Toz on 2012-10-16
This might be of interest to you: [http://www.linux-support.com/cms/ubuntu-developers-rafal-cieslak-adventures-with-asus-netbook-1225c-gma500-drivers-and-unity-on-12-1012-04-1/]("http://www.linux-support.com/cms/ubuntu-developers-rafal-cieslak-adventures-with-asus-netbook-1225c-gma500-drivers-and-unity-on-12-1012-04-1/").

Note that this person had to use the **acpi_osi=Linux acpi_backlight=vendor** kernel parameters to get brightness to work properly.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
maybe this will show you something useful
```
ls /sys/class/backlight/*/{bl_power,power}
```

---

### Post by Meschi on 2012-10-16
Some kind of work around could be to install the package compiz. There you have the menu option  "Opacity, Brightness and Saturation".  There you can choose the key combination that u want and you can adjust the brightness of every window on its on. I am not sure wether this is good for you because I think this doesn't save any energy. However it has the effect to reduce the brightness inside the actual window (I am running ubuntu 12.04 LTS)

---

### Post by vinay_nadig on 2012-10-18
> **Toz said:**
> This might be of interest to you: [http://www.linux-support.com/cms/ubuntu-developers-rafal-cieslak-adventures-with-asus-netbook-1225c-gma500-drivers-and-unity-on-12-1012-04-1/]("http://www.linux-support.com/cms/ubuntu-developers-rafal-cieslak-adventures-with-asus-netbook-1225c-gma500-drivers-and-unity-on-12-1012-04-1/").

Note that this person had to use the **acpi_osi=Linux acpi_backlight=vendor** kernel parameters to get brightness to work properly.
Thank you! I tried this and now I can set it to a more comfortable (and lower) level.

Thanks everyone else for the help. Will mark the thread as solved.

---

