---
title: "When I fire up xubuntu my monitor says its &quot;out of range&quot;"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-04
I want to install xubuntu 7.10 on my donor computer but as soon as everything loads up from the live cd my monitor turns off and it says "out of range" What can I do to correct this so I can get this os installed?

I have an older monitor that came with the donor computer but its all fuzzy and the color is shot but it works all the way through. Its just this other monitor I like better has a problem with my xubuntu cd.

I tried to search other threads for a similar question but I really could not put my finger on the right posts.

Thanks, Neal

---

### Post by jmar71n on 2008-02-04
Try pressing Ctrl + Alt + F2, then login and edit the xorg.conf by;

# **sudo nano /etc/X11/xorg.conf**

then reduce the screen resolution to something like 800x600.


for more information do a search for "change screen resolution + xorg.conf"

---

### Post by pebo on 2008-02-04
Try adding ```
vga=normal
```to your /boot/grub/menu.lst. Refer to [this]("https://wiki.ubuntu.com/FrameBuffer") article in the wiki.
Edit: sorry, I see you are running the live cd. You can add the vga=normal line as a boot option I think.

---

### Post by Indy452 on 2008-02-08
> **pebo said:**
> Try adding ```
vga=normal
```to your /boot/grub/menu.lst. Refer to [this]("https://wiki.ubuntu.com/FrameBuffer") article in the wiki.
Edit: sorry, I see you are running the live cd. You can add the vga=normal line as a boot option I think.



I have the xubuntu installed and with one of the two monitors I switch back and forth the one I like the most goes into power save mode or something even when the computer seems to be running normally. This all happens after I login and provide my password. 

I read the article that pebo gave and I guess I should try to disable the framebuffer temporarily to see if it works then if it does, disable it permanently? Does this sound like a good assumption?

Neal

---

### Post by Indy452 on 2008-02-09
I've followed the exact instructions from the wiki about how to temporarily disable the framebuffer.  I still have no view when I plug the monitor I want to work with in.

What gives with this stuff? Are there any other suggestions? Do you need monitor info?

---

