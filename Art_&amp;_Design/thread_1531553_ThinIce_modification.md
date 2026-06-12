---
title: "ThinIce modification"
date: 2010-07-15
forum: Art &amp; Design
---

### Post by bubulescu on 2010-07-15
Hello

 This may not be the absolute proper place to ask, but does anyone know how to change the ThinIce engine's source so that the radio and check buttons are as shown in the attachments? My interest is to replace the default ones which, IMO, are hard to distinguish, and make them a bit more like Mist/Redmond ones while keeping the general appearance - not with simple lines only, as in Mist, or as bevelled as in Redmond.
 I know I can change them in ~/.gtkrc-2.0 or <theme>/gtkrc, but that either only replaces the buttons in dialogs, leaving menus outside, or force the menus, too, with <engine "thinice" {}>, but that would change the appearance of (almost) the whole menu. Which leaves me with this choice.
 I am not a programmer, even if I understand a thing or two of the basic things but, from what I can see, there's really nothing else to change than a color (maybe a replacement of how a checked button looks with an unchecked one, then a color). I found the "offending" lines in gtk2-engines-2.20.0/engines/thinice/src/thinice_theme_draw.c , in thinice_style_draw_check and thinice_style_draw_option (true?) but, I'm afraid that I don't know what to change and where.
 The "wish_*.png" are modified in Gimp. Initially, I made them look like a combination between Mist and Redmond, but then I changed them as they are now; simply to be different, no need to mimic everything. Note that in the "wish_radio.png" I cheated a bit for the greyed-out entry just to give an idea of how it _may_ look like, but that's only because I couldn't find a disabled radio button as an example.
 As for the colors, the checked one (blueish, in example) is the fg[SELECTED] and the unchecked is the bg[NORMAL]; de gustibus et coloribus...
 These being said, can anyone help?


 Anticipated thanks.

---

### Post by bubulescu on 2010-07-22
Should I move this to another section? If so, can anyone tell me where?

---

### Post by bubulescu on 2010-07-29
In the mean time I found out there is a "cleanice" engine which, properly tweaked, works just fine.

---

