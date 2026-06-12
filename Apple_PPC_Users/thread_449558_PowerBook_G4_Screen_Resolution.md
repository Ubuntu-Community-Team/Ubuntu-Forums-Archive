---
title: "PowerBook G4 Screen Resolution"
date: 2007-05-20
forum: Apple PPC Users
---

### Post by picosam on 2007-05-20
I tried a million xorg.conf files, none of them seem to work :(
I have a PowerBook 1.67 with a 15" screen and an ATI 9700 RV360 M11 video card.
Anyone can tell me the correct configuration?
The default installation works, all the xorg.conf files actually work, but the problem is the screen flickers horribly as if the refresh rate is not correctly set. I can only set it to 60Hz from the user interface.
I even tried setting it to 70-70 in the xorg.conf file with no success.

---

### Post by stmiller on 2007-05-20
Here's my xorg.conf with a 15" TiBook G4:

[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

You don't need to specify any refresh rates, and such. It will be autodetected by the ati driver.

---

### Post by picosam on 2007-05-21
No I tried this, it doesn't work; same flickering :(

---

### Post by pxwpxw on 2007-05-21
How fast does t flicker? Not your screen saver gone haywire is it?

---

### Post by picosam on 2007-05-21
No no, not my screensaver. The darker the color on the screen the clearer the flicker. I don't even know if I can call it flicker. It's like regular noise except not pixelated, but thin strips travelling diagonally very very fast through the screen. I guess I can take a picture of it and post it if my description is not adequate. It's exactly as if the refresh rate is not high enough or something like that. The picture is sharp however, there's nothing wrong with it there. On Mac OS X this problem doesn't exist.

---

### Post by stmiller on 2007-05-21
Are you running Feisty? What is your xorg.conf?

---

### Post by pxwpxw on 2007-05-22
Yes,  in your /etc/X11/xorg.conf file:

```

Section "Screen"
#other entries-----
	SubSection "Display"
		Depth		24
		Modes		"1280x854"
	EndSubSection
#------

```

If this is not exactly your LCD screen native resolution, can get some effects like you describe especially if its very close but not correct.

---

### Post by picosam on 2007-05-22
But that's the resolution reported by my Mac OS X and it's working over there perfectly fine. Should I be using a different driver than the one installed by default with the system?

---

### Post by stmiller on 2007-05-22
> **picosam said:**
> But that's the resolution reported by my Mac OS X and it's working over there perfectly fine. Should I be using a different driver than the one installed by default with the system?

Check out the PPCFAQs at the link below for info on video drivers.

For ati, there is only one driver available for PPC Linux. If your xorg.conf has the line

Driver "ati"

then you have enabled that driver. Or you can choose

Driver "radeon"

but that should not make any difference.

---

