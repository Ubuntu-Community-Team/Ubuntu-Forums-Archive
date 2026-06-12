---
title: "Graphics card drivers?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-02-08
To download some drivers for my graphics card, I went to the website of the manufacturer of my laptop - Packard Bell. I got the specifications of my machine...Video, it says I have > The Intel® 855GM(E) and 852GM(E) chipsets ( does that sound right? )
So, assuming that I needed new drivers for this, hopped along to Intel's website to see what I could find...And it only came up with USB drivers for Linux, which just isn't right :S

So, if not here, where should I go to find drivers?

---

### Post by David Corrales on 2006-02-08
As you have already noticed, most hardware doesn't have vendor support for linux which can sometimes be a pain or a blessing.
Linux distributions come with lots of drivers for tons of devices built in. That's why your network and sound card worked without doing "anything".
As for your specific card, I don't know if there's an special driver to accelerate it (probably there is one).

---

### Post by nik on 2006-02-08
Probably works with the i810 driver :)

Check if you xorg.conf looks something like this...

Section "Device"
	Identifier	"Intel i915"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

---

