---
title: "Configuring Display at Terminal"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by fecalites on 2007-02-03
help please. My display resolution at home is 1280 x 1024 at a 17 inch monitor. Then I decided to bring my desktop pc at a friends place who has a 14 inch monitor which can only support 1024 x 768. The problem is the desktop manager won't load because the monitor is small. But if I press ctrl+alt+f2 I can go to a terminal. Can I configure the resolution while in a terminal?

---

### Post by ed-j on 2007-02-03
You can! I hope this is the right command: sudo dpkg-reconfigure xserver-xorg. Press enter, enter your password, press enter again. Some way through the options you will find resolution.

Hope this helps.

---

