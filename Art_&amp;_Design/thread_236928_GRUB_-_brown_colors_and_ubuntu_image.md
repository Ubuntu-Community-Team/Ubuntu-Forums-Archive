---
title: "GRUB - brown colors and ubuntu image?"
date: 2006-08-15
forum: Art &amp; Design
---

### Post by Garyu on 2006-08-15
When I start my computer the GRUB list comes up with Ubuntu, Ubuntu recovery mode and Windows XP. This is displayed with white text on black background. When I select Ubuntu I get the brown Ubuntu logo (usplash I think?) and brown text scrolling to let me know what is happening.

What I would want to do is to make the first list be either brown text on black background or maybe some brown background with lighter brown text, to fit the Ubuntu look. 

I once tried Kubuntu, and there they have blue text and even the Kubuntu logo in blue on the first GRUB menu list, so I know this can be done, but how do I do it?

I tried editing /boot/grub/menu.lst and found this:
```
# Pretty colours
#color cyan/blue white/blue

```
So if I uncomment that line I get a blue screen with white and cyan text. But it would be so much neater to get an Ubuntu logo at the bottom right of the screen, like Kubuntu had. Also, blue and cyan are far from the Ubuntu colors.

Anyone who knows anything about changing stuff like this? I searched the forums and found lots of stuff on usplash, but I don't think it is usplash I am talking about, it seems usplash is already running fine with the Ubuntu logo. What I want is the GRUB menu to look good. Also something to look at for Edgy Eft IMO.

---

### Post by will_in_wi on 2006-08-16
That is called grubsplash. If you look here:
[http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

