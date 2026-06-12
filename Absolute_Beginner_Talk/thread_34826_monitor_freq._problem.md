---
title: "monitor freq. problem"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by dislektik on 2005-05-16
hello

i've got my kubuntu linux (5.04 release) running with slovak localization. the problem is: every time computer boots up and starts kdm (xorg), i get message "freq. out of range" on my lcd. after killing xorg (pushing ctrl-alt-backspace), xorg and kdm restarts and everything is fine.

kdm starting manualy (not immediately after booting, but running /etc/init.d/kdm start) xorg starts properly.

i've tried not to load DDC module and ignore EDID (by editing xorg.conf), but that doesn't really help. looking into logs doesn't bring any light neither.

vga: nvidia geforce2 mx
drivers: standart kubuntu drivers installed (using [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver))

i'm clueless. any ideas?


Luboss

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=dislektik]
i'm clueless. any ideas?


Luboss[/QUOTE]

Remove the following from your config's **Monitor** section; they are not needed for LCDs:

[indent][i] HorizSync       31.47-83
VertRefresh     56.25-75[/i][/indent]

---

### Post by dislektik on 2005-05-16
thak's, but that doesn't solve the problem

---

