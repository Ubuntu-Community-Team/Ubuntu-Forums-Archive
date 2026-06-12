---
title: "PNG color changing issue, please help(gimp)"
date: 2010-04-03
forum: Art &amp; Design
---

### Post by googeek on 2010-04-03
Ok. Here's what I'm doing.
I'm making a png, from scratch, with transparency. Saving with all the defaults. When I upload it online and check it in my Kubuntu 9.10 with gimp's colorpicker it displays as the proper color 66cc00. When viewed on my friend's Mac, my boyfriends Ubuntu 9.10, and His Dad's Xp; the color comes out brighter, and more neon displaying aedxxx when checked with colorpicker.

Can someone please tell me what the heck is going on? I want to display the color I chose, not a different one. I would really like to use PNG as well, and I need transparency, so simply switching formats isn't going to do it for me.

Thanks in advance for any assistance.

---

### Post by mcduck on 2010-04-03
PNG image format includes gamma correction (basically how dark/bright the mid-gray is). If the display of the person viewing the image has his display configured to use different gamma value than what you are using the program used to view the image tries to adjust it to look the same as it looked like on your display.

The problem is that if either you, or the viewer, doesn't have the display gamma value configured properly, the image will look strange on the viewer's computer.

While everybody of course *should* configure their displays properly, that's just not the case usually, so you might just want to stop Gimp from saving the gamma value in PNG images. while saving a image as PNG file you get a dialog with options for the file, try toggling the "Save gamma" setting there. :)

---

### Post by googeek on 2010-04-07
bump

This didn't work. Gimp's default settings are to not include gamma. I toggled it, and it did work on my boyfriend's Ubuntu now, but not on Xp. We also tested in windows7 and it came out appropriate, but only after SAVING gamma values. Is this simply an Xp issue?  Should I not worry about it, since these folks must be used to funny colors, or is there something I can do?

---

