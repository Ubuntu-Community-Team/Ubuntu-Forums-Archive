---
title: "Gnome visual effects not working?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by User #0001 on 2008-02-23
hello all,

i recently installed, and am now dual-booting, Ubuntu gutsy gibbon on an intel Macbook.

the visual effects were working fine.
i installed a driver for the wireless, and it was still working fine.
i turned it off, then turned it back on, and still no problems.
i setup evolution mail, then turned it off again.
the next time i turned it on, there were no menubars.
i turned off the visual effects and they came back
it appears when i turn on the visuals, the menubars disappear.

any ideas?

please help, i miss my superfluous effects!

oh and according to lspci, this is my graphics thing
Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by RedRat on 2008-02-23
You know when I attempted to install Evolution I had a similar problem and decided it wasn't worth the hassle so I installed Thunderbird, which I used for many years in the Windows world. The machine I installed Evolution on could not support fancy graphics, but I saw some other odd behavior. Might want to try Thunderbird if you can't troubleshoot it.

---

### Post by sailor2001 on 2008-02-23
in your terminal, type: metacity --replace.........now in your home folder, , ctrl/h for hidden files.. click on gnome2 and look for your config files. delete them and reboot via ctrl/alt/backspace to write new configuration...have no idea why it corrupts from time to time

---

### Post by User #0001 on 2008-02-23
which files are the config files?

---

