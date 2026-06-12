---
title: "Boot gfx issue"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by wongdai on 2006-11-20
Hi there,

when I boot Ubuntu using onboard graphics controller, all is good (but slow).

However, when I add a gfx card (and I have tried two now) it get to a certain point, then all I see is an underline.

I have done a search and see others with a similar issue, but I don't understand the fix.

Can someone in simple 1,2,3 steps tell me how to boot up.

Thx in advance

Wongdai

---

### Post by Crooksey on 2006-11-20
Look in your grub.conf file

```
sudo gedit /boot/grub/grub.conf
```

If that displays a blank page, run:

```
sudo gedit /boot/grub/menu.lst
```

Under the colors section, put a # infornt of the word color.

Save, reboot.

---

### Post by wongdai on 2006-11-20
Thanks for that, but how do I do that, if I cannot boot past a certain point?

Is there a way to boot to a cli type interface?

Wongdai

---

### Post by wongdai on 2006-11-20
> **Crooksey said:**
> Look in your grub.conf file

```
sudo gedit /boot/grub/grub.conf
```

If that displays a blank page, run:

```
sudo gedit /boot/grub/menu.lst
```

Under the colors section, put a # infornt of the word color.

Save, reboot.

OK, there is a # in front of the color section.  Still no joy.  It gets passed the initial status screen, which is graphical, but still nothing past that little underlined cursor a bit later on.

I know the box hasn't hung, I just can't see it.

Any other ideas?

---

