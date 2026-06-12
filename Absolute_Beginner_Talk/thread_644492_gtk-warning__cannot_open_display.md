---
title: "gtk-warning **: cannot open display:"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by fourdigit on 2007-12-18
That's what I get whenever I run "gnome-session" from command prompt.

I'm not sure what could cause this error, but I'm trying to make gnome my default window manager.

Anyone know a way to fix this?

---

### Post by spiderbatdad on 2007-12-18
i believe gnome window manger is called metacity```
metacity --replace
```

---

### Post by fourdigit on 2007-12-18
> **spiderbatdad said:**
> i believe gnome window manger is called metacity```
metacity --replace
```

To that, I got "Window manager error: Unable to open X display :0"

---

### Post by spiderbatdad on 2007-12-18
ack!```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fourdigit on 2007-12-18
> **spiderbatdad said:**
> ack!```
sudo dpkg-reconfigure xserver-xorg
```

It wants me to select an X server driver. How do I know which one to choose?

---

### Post by spiderbatdad on 2007-12-18
what is your video card? ```
sudo lshw -C video
```

---

### Post by fourdigit on 2007-12-18
> **spiderbatdad said:**
> what is your video card? ```
sudo lshw -C video
```

Okay, I just configured xorg, but gnome still won't start up.

---

### Post by spiderbatdad on 2007-12-18
```
metacity --replace
```????

you may need GDM for some reason:```
sudo apt-get install gdm
```

---

### Post by fourdigit on 2007-12-18
> **spiderbatdad said:**
> ```
metacity --replace
```????

Yeah, same error.

"Window manager error: Unable to open X display :0"

---

### Post by spiderbatdad on 2007-12-18
> **spiderbatdad said:**
> ```
metacity --replace
```????

you may need GDM for some reason:```
sudo apt-get install gdm
```

gdm?

---

### Post by fourdigit on 2007-12-18
> **spiderbatdad said:**
> gdm?

Already installed.

---

### Post by spiderbatdad on 2007-12-19
ok. you never posted the output of```
sudo lshw -C video
```
so i still dont know what we're dealing with here

---

### Post by fourdigit on 2007-12-19
> **spiderbatdad said:**
> ok. you never posted the output of```
sudo lshw -C video
```
so i still dont know what we're dealing with here

decription: VGA compat controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corp
Physical Id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33 MHz
capabilities: pm vga cap_list
configuration: latency=0

---

### Post by spiderbatdad on 2007-12-19
ok this card should be working with no problem i believe. First check the restricted drivers manager in System--Administration--Restricted Drivers Manager..I doubt anything is listed. Then make sure you have xorg-driver-fglrx   xserver-xorg   xserver-xorg-core  xserver-xorg-input-all

once you know you have those packages try```
sudo dpkg-reconfigure xserver-xorg
``` again and metacity --replace

if none of that works...i'm stumped

---

### Post by fourdigit on 2007-12-19
> **spiderbatdad said:**
> ok this card should be working with no problem i believe. First check the restricted drivers manager in System--Administration--Restricted Drivers Manager..I doubt anything is listed. Then make sure you have xorg-driver-fglrx   xserver-xorg   xserver-xorg-core  xserver-xorg-input-all

once you know you have those packages try```
sudo dpkg-reconfigure xserver-xorg
``` again and metacity --replace

if none of that works...i'm stumped

Same damn error.

---

### Post by spiderbatdad on 2007-12-19
is reinstalling out of the question?

---

### Post by fourdigit on 2007-12-19
> **spiderbatdad said:**
> is reinstalling out of the question?

Yes. Otherwise I'd have done it already.

Is there any other way to make it load gnome?

Maybe I should try KDE?

---

### Post by spiderbatdad on 2007-12-19
try rebooting. at the login window select sessions from the lower left corner and select gnome session

---

### Post by fourdigit on 2007-12-19
> **spiderbatdad said:**
> try rebooting. at the login window select sessions from the lower left corner and select gnome session

I don't see that.

It just goes straight to prompt.

---

### Post by spiderbatdad on 2007-12-19
```
sudo apt-get install -f
```

---

### Post by fourdigit on 2007-12-19
> **spiderbatdad said:**
> ```
sudo apt-get install -f
```

Already installed.

---

### Post by spiderbatdad on 2007-12-19
last suggestion```
sudo dpkg --configure -a
```

---

### Post by fourdigit on 2007-12-20
> **spiderbatdad said:**
> last suggestion```
sudo dpkg --configure -a
```

That didn't help either.

I really need to figure out a way to solve this problem.

---

