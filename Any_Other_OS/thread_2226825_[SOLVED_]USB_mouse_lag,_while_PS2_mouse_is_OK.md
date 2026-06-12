---
title: "[SOLVED ]USB mouse lag, while PS2 mouse is OK"
date: 2014-05-29
forum: Any Other OS
---

### Post by pastet89 on 2014-05-29
[COLOR=#000000][FONT=Lucida Grande]Hi, [/FONT]

[FONT=Lucida Grande]I am getting occasional mouse lags (like seconds-lasting freezes) when running Debian Wheezy stable with default (Gnome 3 shell GUI). The mouse cursor just stays on one place for a second and after that moves to where I have pointed it. Same thing happened to scrolling a page with the middle mouse button - a lag of around a second. [/FONT]
[FONT=Lucida Grande]The problem is hard to reproduce and happen occasionaly. My mouse is wireless and I even suspected the battery is to blame, however, after replacing it with a fresh one the same thing happened.
[/FONT][FONT=Lucida Grande]Rplaced it with another USB mouse and after that with PS2 mouse. All USB mouses seems to have the lag but the PS2 is OK. Even stranger, in xinput --list it shows 2 mouses when I connect one USB mouse.[/FONT]
[FONT=Lucida Grande]My PS2 mouse is old and not good and I am still looking for a way to get my USB mouse working normaly.
Any ideas? [/FONT][/COLOR]:confused:

---

### Post by slickymaster on 2014-05-29
Moved to the **Other OS/Distro Support** sub-forum.

---

### Post by pastet89 on 2014-05-30
Solved. 
 
Add:
```

-r usbhid
usbhid mousepoll=2

```
to /etc/modules and reboot.


Actually this is setting the wireless mouse polling to 500Hz.

---

