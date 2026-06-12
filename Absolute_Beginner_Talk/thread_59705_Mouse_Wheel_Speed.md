---
title: "Mouse Wheel Speed"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by brainz on 2005-08-25
Can anyone help me in increase my mouse scroll more lines in all GTK-apps?

---

### Post by brainz on 2005-08-25
I figured it for firefox:

For convenience, I will summarize the process:

1) type about:config in Firefox's address bar
2) find the preference named "mousewheel.withnokey.numlines"
3) enter an integer (this is the number of lines scrolled per notch on the mouse wheel)
4) find the preference named "mousewheel.withnokey.sysnumlines"
5) change the value to "false" (this tells firefox not to use the system's setting for scroll-rate, which usually defaults to 3).

To make Firefox scroll at the same rate as IE, enter a value of 7 for "mousewheel.withnokey.numlines

---

