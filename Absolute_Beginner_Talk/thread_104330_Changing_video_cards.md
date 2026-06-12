---
title: "Changing video cards"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by steelaz on 2005-12-15
Well after couple days of using my first linux installation I decided to upgrade my box and install new video card. I looked up in the forum that I shoul run these commands:

sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

But after I run first command (and enter my password), 'Ubuntu Configuration' starts. At first it asked about my video card and such so I thought it was normal, but then it started asking about my keyboard, mouse, locale etc. and I don't even know how to get out of it.

Help please.

---

### Post by Arktis on 2005-12-15
cntrl + c at a terminal will quit the command line application, if that's what you are asking.

You don't need to do the reconfigure step.  Just "sudo gedit /etc/X11/xorg.conf" and make the appropriate changes to your device section manually.  This way you'll preserve all your other settings.

---

### Post by steelaz on 2005-12-15
gedit gives me error: Gtk-WARNING **: cannot open display

---

### Post by Arktis on 2005-12-16
Strange gtk warning error...  try restarting X, that might resolve it.

Of course, you can always use nano instead.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by steelaz on 2005-12-16
well i'm totaly new to linux (4 days and counting)...

I think X is messed up, because I change my video cards and it needs new drivers or smth. so if 'gedit' needs X it probably won't run. is nano text-based?

---

### Post by Mustard on 2005-12-16
Nano is text based, yep.

Strictly speaking you shouldn't even need to edit your xorg.conf, as when you install the nvidia-glx drivers and then do the config enable command you have shown above, it will alter the xorg.conf to enable the nvidia drivers.  From reading your above posts, I am assuming you have gone past that point, edited something and now find yourself unable to load X at all.

sudo dpkg-reconfigure xserver-xorg will enable you to reconfigure xorg.conf, IF you totally stuff it up.  With regards to the questions it asks that you don't know the answers to, you simply choose the default answer that is highlighted at the time.  If you can't get the nvidia drivers going using dpkg-reconfigure, switch it back to VESA so you can at least get back into gdm login screen and use gnome again.  From there you can attempt to do the installation again.

I take it you are doing all this from terminal because X isn't working anymore?

That would explain the error when trying to use gedit.

A good habit to get into is to backup these types of files before playing with them.

A command like this will create a backup of xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```

---

### Post by steelaz on 2005-12-17
Problem fixed. Turned out all I had to do was go through first step completely (I rebooted before in fear of all the questions, lol)

All good now, my ubuntu running with geforce fx5200.

Thanks for all your help.

---

