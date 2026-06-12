---
title: "Screen Distorted Help!!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by inthecurrent on 2007-11-06
I am new to linux.  I down loaded a driver for my video card ( Radeon 200 express ) and applied it by rebooting.  Ubuntu started as normal but the screen is completely distorted.  I can't see to set my drivers back.  What do I do now?  Do I need to reinstall Ubuntu?

---

### Post by SpiritIsReality on 2007-11-06
howdy
you could try Ctrl-Alt-F2 (press and hold both Ctrl and Alt keys, and tap F2 key)
to see if you can get a login prompt.
log in, then type 
sudo dpkg-reconfigure xserver-xorg
then answer the questions best you can, usually the defaults will work.
then once that's done, type
sudo shutdown -r now
to restart the computer.
trails

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=video&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=video&titlesearch=Titles)
[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29)

---

### Post by digital_sabotage on 2007-11-06
...what i've done when i mess up my graphics is to boot with the live cd

...then from terminal do
```
sudo nautilus
```

then navigate to your file system  ...go to "etc/X11/xorg.conf.1"  ...that should have the original configuration  ...copy and paste in "etc/X11/xorg.conf"  ...then reboot

...make sure you aren't going to the etc/X11 folder that the live cd has created ...you want the one off your hard disk

...has worked for me ...good luck:-)

---

