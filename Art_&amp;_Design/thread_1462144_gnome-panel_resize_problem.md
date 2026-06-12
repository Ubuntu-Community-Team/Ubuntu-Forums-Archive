---
title: "gnome-panel resize problem"
date: 2010-04-25
forum: Art &amp; Design
---

### Post by bohemistanbul on 2010-04-25
Hi everyone,

If i resize the gnome-panel above than 24, the panel is divided into two parts. It is not pretty because of the difference color tones. 
I dont want to see a divided gnome-panel even if its size is 40. Please look at the attachment. 

Does anybody know a solution for that?

Cheers.

---

### Post by Vish... on 2010-04-26
What you are noticing is [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532309](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532309)

---

### Post by mcduck on 2010-04-26
One way to solve it is to edit the GTK theme and remove the panel background image from it, and then assign the image directly in the panel's preferences. After that you can use gconf-editor to enable background image scaling on that panel to get the image to resize correctly as you resize the panel.

The same solution applies to using vertical panels, the Gnome-panel is able to scale and rotate background images if you just enable the settings in gconf, but this doesn't work for images defined in the GTK theme.

---

