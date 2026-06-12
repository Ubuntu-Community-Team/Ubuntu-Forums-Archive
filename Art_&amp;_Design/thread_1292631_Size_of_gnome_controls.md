---
title: "Size of gnome controls"
date: 2009-10-16
forum: Art &amp; Design
---

### Post by camini on 2009-10-16
I'm trying to make my Ubuntu UI look tighter and polished.

Overall, I find that the gnome controls that are delivered by defaultare somewhat clunky, old-fashioned and too big.

What surprises me is that when I browse through other themes (in Ubuntu or from the net), the styles and colors of controls varies greatly, but their size are constant.

Is there a reason for this?
Do you know of controls that are smaller and looking nice?

Don't get me wrong, I love everything else about ubuntu.

Cam

---

### Post by mcduck on 2009-10-16
Actually I'd say that small widgets are old-school, if something, as they are more fit for small resolutions while modern displays have so high resolutions that larger controls are almost a necessity to maintain usability.

Anyway, the padding in control widgets is defined in the theme, so if all the themes you use have too large controls that means that the theme's designer wanted they to be that large. Still, there are some themes around that are specifically made to be compact. Jut search for "compact" in gnome-look.org, for example.

Also there are some settings you can do yourself to reduce the amount of space your UI needs:

[LIST]
[*]Go to System/Preferences/Appearance, and on the Interface-tab change "Toolbar buton labels" to "Icons only".
[*]Use smaller font size. Smaller text in widgets will allow the widget itself to be smaller.
[*]Open Gconf-editor, browse to desktop/gnome/interface and set the "toolbar_icon_size" to "small-toolbar".
[/LIST]

edi: Also note that many programs also have their own settings for this kind of things. Firefox, Inkscape, Gimp and OpenOffice, for example.

---

