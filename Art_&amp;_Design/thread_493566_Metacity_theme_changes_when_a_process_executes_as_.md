---
title: "Metacity theme changes when a process executes as another user"
date: 2007-07-05
forum: Art &amp; Design
---

### Post by VictorR on 2007-07-05
I made a custom Metacity theme based on Ubuntu Human. While testing found that if the process run under another credentials (like Update Manager as root or Firestarter) the theme temporary changed to something very basic for those particular windows. This did not happen with Ubuntu default Human theme.

The question is WHY and how to fix it.

---

### Post by VictorR on 2007-07-06
I have found the answer myself. The theme was located in my home folder rather than in /usr/share/themes. After I copied the stuff to the proper place all works fine.:D

By the way another question: where to put
<window_icon function="close" state="normal" draw_ops="menu_close_icon"/> into 'metacity-theme-1.xml'?

---

### Post by dilomo on 2008-12-20
> **VictorR said:**
> I have found the answer myself. The theme was located in my home folder rather than in /usr/share/themes. After I copied the stuff to the proper place all works fine.:D

By the way another question: where to put
<window_icon function="close" state="normal" draw_ops="menu_close_icon"/> into 'metacity-theme-1.xml'?

Same question here :)

---

