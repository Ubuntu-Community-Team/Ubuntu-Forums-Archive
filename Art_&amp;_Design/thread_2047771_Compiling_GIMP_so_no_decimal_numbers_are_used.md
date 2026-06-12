---
title: "Compiling GIMP so no decimal numbers are used"
date: 2012-08-25
forum: Art &amp; Design
---

### Post by Cæncel on 2012-08-25
Gimp 2.8 series has this ridiculous  way to handle the values of the scrollbars with decimal numbers when they are not even required, there is no difference between the size of a brush with 1.05  or 1.40 whatsoever, so:

How can i achieve this?

[IMG]http://img692.imageshack.us/img692/8017/nodecimals.png[/IMG]

what files do i need to modify in the source to disable decimal values?

---

### Post by prokoudine on 2012-09-01
> **Cæncel said:**
> Gimp 2.8 series has this ridiculous  way to handle the values of the scrollbars with decimal numbers when they are not even required, there is no difference between the size of a brush with 1.05  or 1.40 whatsoever, so:

If there is no difference, then why bother?

---

### Post by Cæncel on 2012-09-02
> **prokoudine said:**
> If there is no difference, then why bother?
cause well, you can scroll 10 times with your mouse wheel to reach from 1 to 1.10 or you can scroll 10 times to go from 1 to 10, so just guess what would be more practical for the size of brushes ans stuff

---

### Post by prokoudine on 2012-09-06
> **Cæncel said:**
> cause well, you can scroll 10 times with your mouse wheel to reach from 1 to 1.10 or you can scroll 10 times to go from 1 to 10, so just guess what would be more practical for the size of brushes ans stuff

Mmmh... You know, there's such a thing as a minimum step. If you remove decimals, the step doesn't magically become larger. You just lose precision. It's all down to math, mate :)

By the way, you can drag fast depending on  position of the pointer above the slider.

That slider will be reworked in the future anyway.

---

### Post by prokoudine on 2012-09-12
And here we are: [http://git.gnome.org/browse/gimp/commit/?id=2c3a046d832e245aed8883424d0951b006ffc7e6](http://git.gnome.org/browse/gimp/commit/?id=2c3a046d832e245aed8883424d0951b006ffc7e6)

Expect in 2.8.4.

---

