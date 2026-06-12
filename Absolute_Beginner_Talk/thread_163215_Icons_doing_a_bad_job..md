---
title: "Icons doing a bad job."
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-04-20
I recently did a dist-upgrade to Dapper. The whole thing went swimmingly as far as I'm concerned with only two exceptions (that I've found so far). Firstly, it broke the driver for my video card, but I've already fixed that. Second, however, it uninstalled the old Open Office (1.whatever) but never replaced it with the new one citing a conflict.

I looked into it and the conflict had something to do with the new braille tty software which I don't care about as I am a sight-enabled individual.

Long story short, I grabbed openoffice.org from apt-get and it installed. The only trouble is that the icons are not set up. They show up on the menu as the ugly default icon Ubuntu uses when a program doesn't have an icon specified. Did I do something wrong? What's the best way to fix it? I should mention that the icons DO show up as set in SMEG, though, my experience with SMEG tells me I should take anything it tells me worth a grain of salt. At the very least, where would I find the .desktop entries for these so I can try to fiddle with it myself?

That's enough questions for now. Thanks.

Oh, and when I do find the .desktop files, where would the icons be located so that I can map it to point there?

---

### Post by Qrk on 2006-04-20
Make sure that you have openoffice.org-gnome installed. It makes sure that openoffice responds to your Gnome theme and uses gnome dialogs.

```
sudo apt-get install openoffice.org-gnome
```

It should have been installed when you upgraded, but you might have missed it. In fact, I don't believe it is an official part of ubuntu-desktop, so you very easily could have missed it. 

I'm not sure it if will fix your problem, but it may.

---

### Post by pbaehr on 2006-04-20
Awesome. I'll give this a shot right now. Thanks!

---

### Post by pbaehr on 2006-04-20
That fixed it right off. Thanks again.

---

