---
title: "Blank screen - removed ATI drivers"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by lex on 2006-11-30
I removed ATI driver via Automatix, (installed same way). Now I have a blank screen with this square in it.
"ATTENTION-  Cannot display this video mode, change computer display to 1280 x 1024@60hz"](*,)
Guess I stuffed up good. I was just tring to see if they had installed. I thought if I removed them I might see a difference.
**[COLOR=Red]PLEASE [/COLOR]**[COLOR=Red][COLOR=Black]help!
Thanks
[/COLOR][/COLOR]

---

### Post by an.echte.trilingue on 2006-11-30
Boot your computer into a terminal by pressing esc right after you turn it on to get into the GRUB menu and select the recovery mode, which should be the second option.  Reconfigure your graphics card with the command ```
sudo dpkg-reconfigure xserver-xorg
``` and be prepared to answer some questions about your video configuration.  Select the vesa driver and a fairly conservative screen resolution.  Then reboot.  Then you should have a usable system, and you can mess around with installing and uninstalling drivers and changing resolution all you want.

My advice, stay away from things like automatix.  By installing things by hand, you will learn the processes to repaire things that get mugged up, and the community docs on the ubuntu wiki page contain instructions for almost everything you would want to do.

Good Luck!

-mat

Edit: By the way, the resolution you want to select is most likely 1280x1024.

---

### Post by lex on 2006-11-30
thanks an.echte.trilinge ill give that a go now.

---

### Post by lex on 2006-12-02
Thanks, an.echte.trilinge  it work a treat, once I figured out where vesa was.

---

