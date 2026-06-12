---
title: "How can I switch to console mode?"
date: 2007-05-01
forum: Apple Intel Users
---

### Post by michaels on 2007-05-01
Hi, buddy!

After installing Feisty, my macbook pro works really well except a minor defect on keyboard mapping: Because the "Fn" key can't be detected, the keys from "F1" to "F10" work as function keys, for example, adjusting the sound or keyboard backlight. As a result, I cannot switch to console mode with "Ctrl + Alt +F2". Does some one knows how to switch to console mode from command line in a Terminal? And how to switch back?

Thank you!:KS

---

### Post by Zelut on 2007-05-10
the fn keys are swapped if you press fn (bottom left) so you should be able to use:

ctrl-alt-fn-F1 to toggle that.  I have actually disabled the default fn setup so I now need to press fn to get the volume keys, etc.

---

### Post by The_Giver on 2007-05-17
and how would i do that?

---

### Post by Nakah on 2007-05-20
Just create a file in /etc/modprobe.d/ name it like you want
And write into it : 

options hid pb_fnmode=2 #(for kernel >= 2.6.20)

or

options usbhid pb_fnmode=2 #(for kernel < 2.6.20)

---

