---
title: "Is there a &quot;Dvorak-Qwerty&quot; layout for linux?"
date: 2007-06-02
forum: Assistive Technology &amp; Accessibility
---

### Post by Cris987 on 2007-06-02
Macs offer a "dvorak-qwerty" layout that allows qwerty shortcuts when the apple-shortcut key is pressed. Is there something similar for linux, in which case the system would revert to qwerty when the ctrl key is pressed?

---

### Post by frafu on 2007-06-04
Hello

There is a dvorak-layout under the U. S. English layouts. 
(Open the Keyboard preferences by using the menu System->Preferences; then go to the Layouts tab and scroll down to the U. S. English, where you have to click on the triangle at the left.) 

However, I don't know whether it can be used as in MacOSX. 

Regards

Francesco

---

### Post by nanotube on 2007-06-05
> **Cris987 said:**
> Macs offer a "dvorak-qwerty" layout that allows qwerty shortcuts when the apple-shortcut key is pressed. Is there something similar for linux, in which case the system would revert to qwerty when the ctrl key is pressed?

no there isn't. and why would you want it anyway? just use the shortcuts in dvorak. it takes but a few days to get used to it. :)

---

### Post by scorchgeek on 2009-07-31
Actually, there is, although you have to use the right Ctrl key. Open the keyboard layouts window as described above, then click Layout Options-->Keys to change layout, then enable the appropriate option.

---

### Post by Kenton Varda on 2010-02-05
Turns out you can't implement this as a keyboard layout in X without causing all kinds of bugs to start coming out of the woodwork.  It seems each X client is responsible for interpreting the keyboard layout, and most GUI frameworks simply have not accounted for layouts that change when a modifier key is held.

You can, however, implement it as a program that intercepts events via XGrabKey(), rewrites them, and then XSendEvent()s them on to the app window.  I have done so!  Here you go:

[http://dvorak-qwerty.googlecode.com](http://dvorak-qwerty.googlecode.com)

(There's also a Windows version.  Not that you would care, of course.  ;))

---

### Post by nanotube on 2010-02-06
> **Kenton Varda said:**
> Turns out you can't implement this as a keyboard layout in X without causing all kinds of bugs to start coming out of the woodwork.  It seems each X client is responsible for interpreting the keyboard layout, and most GUI frameworks simply have not accounted for layouts that change when a modifier key is held.

You can, however, implement it as a program that intercepts events via XGrabKey(), rewrites them, and then XSendEvent()s them on to the app window.  I have done so!  Here you go:

[http://dvorak-qwerty.googlecode.com](http://dvorak-qwerty.googlecode.com)

(There's also a Windows version.  Not that you would care, of course.  ;))

hey, looks cool! i like my ctl-shortcuts to stay in dvorak, myself... but i'm sure the dvorak-qwerty lovers will enjoy. :)

---

### Post by damiannz on 2010-07-05
actually, i've had this enabled for the past 6 months and it's been pissing me off no end. i just figured out how to get rid of it (for me at least). 

perhaps if you reverse what i've done you'll end up with ctrl-qwerty like i had too :-)

so -- under Keyboard Preferences -> Layout, I had two maps: USA (first) and USA Dvorak International (second). Somehow it was always defaulting to Dvorak when i logged in, but when i opened a terminal window, for example, under the Dvorak layout Ctrl-C would show up as Ctrl-I. so i had QWERTY for ctrl and Dvorak normally.

i moved USA Dvorak International so that it was the first in the list, and suddenly it all seems to work fine.

hope this helps!
d

---

