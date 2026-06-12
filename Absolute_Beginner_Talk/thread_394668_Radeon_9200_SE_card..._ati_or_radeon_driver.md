---
title: "Radeon 9200 SE card... ati or radeon driver?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-27
I'm on Feisty, and here's the current xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
```
Although my display isn't bad, there is occasionally a bit of drag that might be avoided. Also, shouldn't there be a few more options in xorg, regarding resolution, acceleration, rendering, etc.?

A few people in the forum with the same card recommended the radeon driver, but it's not listed as an option when I try reconfiguring. How do I get it to begin with, and what sort of special handling does it involve? Thanks in advance.

---

### Post by msak007 on 2007-03-27
I believe that package that contains it is **libgl1-mesa-dri**. Look for it in Synaptic, and if it's installed simply edit your xorg.conf to say "radeon" instead of "ati".

---

### Post by ricardisimo on 2007-03-27
It's installed, but radeon isn't a choice. I guess I'll keep looking. I would have thought that the Synaptic description would list it somewhere, but no.

Related issue came up while editing with ```
sudo dpkg-reconfigure xserver-xorg
``` - how do I mark, or select higher screen resolutions? I know from the XP on this comp that it can go higher than 1024x768, but I don't know how to tick the higher options. Thanks.

---

### Post by TonKi on 2007-03-28
to tick higher resolutions you have to use the "space-key"

and to activate the radeon driver - edit xorg.conf and replace ati with radeon

---

### Post by ricardisimo on 2007-03-28
Unless I'm mistaken, if I run ```
sudo dpkg-reconfigure xserver-xorg
``` I should see radeon listed if it's present at all. If it doesn't appear (and it doesn't) It's not installed.

---

