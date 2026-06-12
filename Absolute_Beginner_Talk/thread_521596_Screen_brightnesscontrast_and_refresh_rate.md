---
title: "Screen brightness/contrast and refresh rate"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Ze MoreiRa on 2007-08-09
How do I adjust monitor brightness? I think it is too bright. and I need to decrease refresh rate from 75 Hz to 72.

Please keep in mind that I am an "absolute beginner" :D
thanks

---

### Post by fumduck on 2007-08-09
should be a button on desktop by places and applications

 System> Preferences> screen resolution

brightness...   I think that is on your monitor itself.. like physically

peace

---

### Post by afterwego on 2007-08-09
Monitor brightness is usually either adjusted within the monitor itself or by hotkeys on your keyboard. Usually laptops have brightness keys that will let you raise and lower it. I am not aware of something within Ubuntu for doing this. Maybe someone else has a suggestion on this matter.

For refresh rate you can check under System -> Preferences -> Screen Resolution. There is a drop down for refresh rate in there and you can see if it has your desired rate. Otherwise, if not you will most likely have to edit the /etc/X11/xorg.conf and change something within there to give it that option.

I have only changed resolutions with xorg.conf, so I am not 100% on changing the refresh rate.

---

### Post by Ze MoreiRa on 2007-08-09
When I first installed Windows I had exactly the same problem. monitor was too brigtht. I have a nasty onboard video card. Its default brightness/contrast/gamma is very bad. Ifter I installed driver for it on Windows, I could tune them manually. Isn't there a way to edit some values? when I adjust brightness within the monitor itself, almost black and white

---

