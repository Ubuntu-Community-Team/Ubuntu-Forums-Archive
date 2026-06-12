---
title: "Display driver problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ssharish on 2007-04-29
Hi,

I got down to this problem for second time now. My display driver has corrupted. I use envy. Today in the morning i switch on my system my default resolution is just 640 * 480. Thats the maximum, I tried reinstalling the envy (Nvedia), no success still it 640 * 480.

Does anybody know the solution for this please. 

thank you

ssharish

---

### Post by lepz on 2007-04-29
You will probably need to change your xorg. type.....................

sudo gedit /etc/X11/xorg.conf

go to monitor section

and add your resolutions at the beginning of each mode line

save and exit

log out/in and you should have your new settings.

---

### Post by ahaslam on 2007-04-29
Failing that, post the file here along with more details on your hardware.

---

