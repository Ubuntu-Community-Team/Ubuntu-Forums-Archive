---
title: "Accessibility for Colorblind?"
date: 2006-11-05
forum: Assistive Technology &amp; Accessibility
---

### Post by eilu on 2006-11-05
A friend is asking me to help him set up Ubuntu on his system, he's colorblind so I'd like to ask if Ubuntu has themes/skins/accessibility options specifically for this problem.

His colorblindess is not severe, he can see red, blue and yellow but if the shades/hues are too near in the spectrum, he can't tell them apart (eg, violet and blue; a yellow-orange-red gradient will probably appear as only one shade)

Thanks.

---

### Post by frafu on 2006-11-06
There are a few high contrast themes (under the menu System-Preferences-Theme) that are shipped with ubuntu. This might be a first step... 

frafu

---

### Post by Henrik on 2006-11-10
There is also a set of colour filters under development for the gnome magnifier (which can be run without magnification).

This is very promising because you can turn on the filter when you need to see something in better contrast, like a chart with poor colour choices.

See: [http://mail.gnome.org/archives/gnome-accessibility-list/2006-October/msg00040.html](http://mail.gnome.org/archives/gnome-accessibility-list/2006-October/msg00040.html)

---

### Post by eilu on 2006-11-11
Thanks! These might be the final push he needs to finally make the switch.

---

### Post by skipf on 2006-11-14
Just yesterday I was looking for utilities to help with colorvision deficiencies; some of the colors they use on weather maps escape me.
 Most noteably, WIKI had some good info under colorblindness, including
a link to a 24 plate diagnostic test- (I'm green insensitive)
 But the program I'd like is ColorWatch, a MS (unfortunately) color IDing
program, that posts the color value AND name in a toolbar utility.
  Could it be run with WINE?
 Thanks!
 Skip

---

### Post by cerdiogenes on 2007-01-12
> **Henrik said:**
> There is also a set of colour filters under development for the gnome magnifier (which can be run without magnification).

This is very promising because you can turn on the filter when you need to see something in better contrast, like a chart with poor colour choices.

See: [http://mail.gnome.org/archives/gnome-accessibility-list/2006-October/msg00040.html](http://mail.gnome.org/archives/gnome-accessibility-list/2006-October/msg00040.html)

This is already available in GNOME Magnifier. The next thing to do is distros start to support the libcolorblind, that is the library that implement the colorblind filters.

Best regards.

---

### Post by Henrik on 2007-01-12
Ah, thanks for the reminder!

I've added a bug task on it [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-mag/+bug/79003"). 

Is that all we need or do we need some config GUI as well?

---

### Post by cerdiogenes on 2007-01-13
> **Henrik said:**
> Ah, thanks for the reminder!

I've added a bug task on it [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-mag/+bug/79003"). 

Is that all we need or do we need some config GUI as well?

The support is done in gnome-mag, but a GUI configuratin is missing. This configuration must go into orca/lsr/gnopernicus.

I could do this work, but I will be busy enough in the next months to think about coding a prototype!

---

### Post by Henrik on 2007-01-13
Right, I'm sure the config GUI can wait until Feisty+1. It should be given some careful thought.

How is it configured in the meantime? A config file, gconf keys? Is there any documentation on this? If not we should write some for the Feisty release.

---

### Post by cerdiogenes on 2007-01-13
You have only an interface throw the bonobo property bag. If you download the gnome-mag source-code and look in the test/control-client.c code and find the "case 'B'" branch of the switch you will see how it can be changed.

I don't make anyway to the user change it since there are different color blind filters and from the discussion about this the use case was that an user will press a keystroke and the filter is activated, then it press it again and the filter is deactivated, since this permits color blind user active/deactive the filter easily, but since gnome-mag doesn't manage keystroke this must be implemented in orca, gnopernicus or lsr.

---

### Post by Icarosaurus on 2007-03-09
Thank you from the colorblind people :-D

---

