---
title: "[HOWTO] Apple Magic Mouse on 10.10 Maverick Meerkat"
date: 2010-11-03
forum: Apple Hardware Users
---

### Post by edmondt on 2010-11-03
This HOWTO was based on a fresh install of Ubuntu 10.10 on Lenovo T61. 

The Bluetooh GUI detected the mouse but nothing happened so I Removed the Mouse from Bluetooth Preference.

Open up Terminal:

```

sudo apt-get install bluez-compat

sudo hcitool scan

(turn your Apple Mouse Off and On to enable discovery)

	7C:6D:62:F6:C5:CE	Apple Wireless Mouse
	18:E7:F4:ED:87:CF	Edmond’s iPhone

Copy your mouse address and enter the following:

sudo hidd --connect 7C:6D:62:F6:C5:CE

```

Works better than with Windows 7 I must say... No tap to click or multi-touch tho, but scrolling works...

The following tweak is optional to make the mouse scroll a little better on firefox, enter about:config in the url, search for the following:

```
mousewheel.withnokey.sysnumlines false
mousewheel.withnokey.numlines 6
```

---

### Post by mybunche on 2010-11-27
Thanks this. Looking forward to give it a try.

---

### Post by avelez89 on 2010-11-29
Thank you so much. I just installed 10.10, giving Linux a serious try, and was struggling with my mouse. Ubuntu would recognise it but it would not use it.
Your instructions worked perfectly, thank you!

Ubuntu 10.10, HP dv2625la, Might Mouse.

---

### Post by spigolo on 2010-12-26
pretty cool guide, great job. mouse works: 3 buttons (left, middle, right), both vertical and horizontal scroll.

what's missing: multitouch, awake after idle (i have to restart the hidd command after every screen saver).

what's annoying: unbearable speed, even at the lowest settings.

any tip that i am missing?

thanks again!

---

### Post by wersdaluv on 2010-12-27
Not sure if there's one yet, but I'd recommend linking a wiki page to and from this post to share info

---

### Post by thinktyler on 2010-12-29
I can also confirm this to work in Natty. It might be important to distinguish which Mighty Mouse Rev A, or Rev B. 

Rev A, seems to be fairly simple. System > Preferences > Bluetooth

Adding a new connection, and selecting PIN Options, 0000 and unchecking "automatic" was reported to work by atleast one source.

I on the other hand had no such luck. This guide works with mine version, which is the Rev B. I've used both Mighty Mouses in the past, so both of them do in fact work. (No question here, really)

I was able to pair both of them with bluetooth manager installed from Ubuntu Software Center.

sudo apt-get install blueman

---

### Post by apakatt on 2011-01-18
I tried what was written in the first post but got the following error:
```
sudo hidd --connect D8:30:62:38:18:02
Can't get device information: Connection refused
```After trying a lot of things I got it working by creating a new file:
```
/var/lib/bluetooth/00\:10\:60\:A6\:19\:3B/pincodes
```(You need to replace the 00:10:60 etc... part with your own. The folder should already be there so you only have to create the file pincodes in the existing directory. Note that it is not the same as the Magic Mouse ID!)

In this file you should add:
```
D8:30:62:38:18:02 0000
```
Replace the D8:30:62... etc with the ID for you Magic Mouse and the 0000 is the default pincode for the Magic Mouse. The guide worked as described after creating that file.

---

### Post by 3demi on 2011-01-31
> **spigolo said:**
> 
what's annoying: unbearable speed, even at the lowest settings.

any tip that i am missing?

doing this:

```
$ xinput set-float-prop "Apple Magic Mouse" "Device Accel Velocity Scaling" 2.0
```helped a little bit for the speed problem.

---

