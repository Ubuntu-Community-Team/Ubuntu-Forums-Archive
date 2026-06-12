---
title: "mac_hid on intrepid"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by thouters on 2008-11-05
Hello,

I have used the folowing sysctl.conf configuration the past years to turn the option keys into right and middle click mouse buttons.  With Xorg 7.4 (intrepid macbook 1st gen and also my debian sarge iBook), this no longer works.

dev.mac_hid.mouse_button_emulation=1
dev.mac_hid.mouse_button2_keycode=126
dev.mac_hid.mouse_button3_keycode=125

Can anybody tip me to the reason this does not work anymore?  The mac_hid feature seems present in the kernel.

Thanks in advance

---

### Post by bsm117532 on 2008-11-07
I find that for some odd reasons the keycodes of these keys have changed to 95 and 96.

However, even with that change, the other mouse buttons still don't work!

---

### Post by tstraumann on 2009-01-22
I encountered the same problem but found that this
functionality is now governed by 'mouseemu'.
Editing '/etc/defaults/mouseemu' and restarting
(sudo /etc/init.d/mouseemu restart) did the trick for me.

HTH
-- Till

---

