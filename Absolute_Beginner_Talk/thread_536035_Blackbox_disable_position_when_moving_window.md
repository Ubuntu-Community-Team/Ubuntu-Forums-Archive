---
title: "Blackbox disable position when moving window"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-27
How would I disable the meter that is in the middle of the screen when moving a window on blackbox?

---

### Post by felicity on 2007-08-27
I don't use blackbox, but in openbox the display that shows the window position is in the config file (rc.xml) in this section:

<resize>
    <drawContents>yes</drawContents>
    <popupShow>Always</popupShow>
    <!-- 'Always', 'Never', or 'Nonpixel' (xterms and such) -->
    <popupPosition>Center</popupPosition>
    <!-- 'Center' or 'Top' -->
  </resize>

You may be able to find something similar in your blackbox config file.

---

