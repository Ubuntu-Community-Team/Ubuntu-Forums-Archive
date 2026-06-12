---
title: "Login screen resolution issues on feisty upgrade"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by SSB on 2007-04-21
Since upgrading from Edgy to feisty, my login screen has been showing up quite strange. The screen flickers and the text is fuzzy while my monitor splays a blue rectangle in the center reading "out of range!" which means it's not a supported resolution. I did not have this problem on edgy. Upon logging in, the resolution is fine. My xorg.conf lists the proper resolution on all lines. I have an ATI Radeon x700 pro - i'm thinking the ATI drivers are probably doing this. When I upgraded, feisty started yelling at me about using restricted drivers for my ATI card, so I acquiesced and enabled the ATI restricted driver support, hoping my problem would be solved, however the problem displayed both before and after the restricted driver ordeal. This issue is really hard to deal with right now as I can't see the change session dialog boxes when trying to go between default and Xgl sessions.


Any ideas?

---

### Post by siciliancasanova on 2007-04-22
Bump 

I know this will let you edit your splash screen resolution in the current kernel version line...

```
sudo gedit /boot/grub/menu.lst
```

add this line in that paragraph ```
vga=791
``` if you want a 1024x768 resolution

Not really much help and more of a bump but if you are having issues on your splash screen also that would be a place to look.

---

### Post by SSB on 2007-04-22
What would I set it to if I need a 1680x1050 resolution?

err, wait, if that's for grub and not the actual login screen it won't do me much good.. my boot menu is fine.

---

### Post by SSB on 2007-04-22
not-so-stealthy bump

---

