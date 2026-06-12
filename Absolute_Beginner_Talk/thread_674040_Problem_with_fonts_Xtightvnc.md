---
title: "Problem with fonts Xtightvnc"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-21
Hi,

I installed TightVNC server and configured as described here:

[https://help.ubuntu.com/community/VNC#head-3c64771b3e130cde605dade8868ad840f5992be1](https://help.ubuntu.com/community/VNC#head-3c64771b3e130cde605dade8868ad840f5992be1)

The problem is that it does not find the fonts, thought defined like:

# Here is another example of setting the font path:
# $fontPath = "/usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/75dpi/";
# $fontPath =  "/usr/share/X11/fonts/misc";
# $fontPath =  "/usr/share/X11/fonts/100dpi/:unscaled";
# $fontPath =  "/usr/share/X11/fonts/75dpi/:unscaled";
# $fontPath =  "/usr/share/X11/fonts/Type1";
# $fontPath =  "/usr/share/X11/fonts/100dpic";
# $fontPath =  "/usr/share/X11/fonts/75dpi";

[B]$fontPath = join ',',qw(
/usr/share/X11/fonts/misc
/usr/share/X11/fonts/100dpi/:unscaled
/usr/share/X11/fonts/75dpi/:unscaled
/usr/share/X11/fonts/Type1
/usr/share/X11/fonts/100dpi
/usr/share/X11/fonts/75dpi
 );[/B]

any ideas?

Ben

---

### Post by ben22 on 2008-01-21
ok, I recongnized that the PATH was incorrect in the tutorial>

the fonts are in fonts/X11
not in X11/ fonts

HOWEVER, also with that configuration it is not working.


# $fontPath = "/usr/lib/fonts/misc/,/usr/lib/X11/fonts/75dpi/";
$fontPath =  "/usr/share/fonts/X11/misc";
$fontPath =  "/usr/share/fonts/X11/100dpi/:unscaled";
$fontPath =  "/usr/share/fonts/X11/75dpi/:unscaled";
$fontPath =  "/usr/share/fonts/X11/Type1";
$fontPath =  "/usr/share/fonts/X11/100dpic";
$fontPath =  "/usr/share/fonts/X11/75dpi";

---

