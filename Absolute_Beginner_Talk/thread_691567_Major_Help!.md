---
title: "Major Help!"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by SIXAXIS on 2008-02-08
I need help guys. In an attempt to get compiz working I disabled the restricted driver for the graphics card. Now when I boot up Linux I get a black screen and nothing happens. I do not want to reload everything. If I can enable the restricted driver in the recovery mode or open a gui in the recovery mode, it would be great. Can someone help me please? I cannot lose my files.

---

### Post by taurus on 2008-02-08
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by nynoah on 2008-02-08
I had this problem in the past.  Don't fret it can be fixed.  Let me look for an old post where someone helped me out and I will cut and paste that for you.

Noah

---

### Post by SIXAXIS on 2008-02-08
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

Thank you!

P.S. Is there a way that I can give you an extra bean or give you a rating?

---

### Post by nynoah on 2008-02-08
Glad to hear that worked for you.  Here is what I was going to paste.  



> Boot in Recovery Mode (select it from the GRUB menu)

type:
Code:

dpkg-reconfigure xserver-xorg

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
Code:

reboot

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

