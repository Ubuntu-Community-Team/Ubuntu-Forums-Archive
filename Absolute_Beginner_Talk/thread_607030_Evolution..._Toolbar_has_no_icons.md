---
title: "Evolution... Toolbar has no icons"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by freakavoid on 2007-11-08
Hi,

I did a lot of searching and cannot figure out why my evolution toolbar looks like this. It's not an icon theme issue; I tried different ones. I recently did a fresh install of gutsy and that's when evolution mail started to appear without icons. No problems with another application.

Thanks in advance for your help.

[IMG]http://i46.photobucket.com/albums/f122/onReflection/evolution-toolbar.jpg[/IMG]

---

### Post by kyphi on 2007-11-08
Since you have a few icons properly formed on your toolbar it would seem that your installation of Evolution was incomplete.

You could try to reinstall Evolution via Synaptic or else enabling your CD in your repository index and reinstalling Evolution from there.

---

### Post by Incense on 2007-11-08
Are you in KDE? If so, try this. Works for me. 

From the term type:

```
$ chmod -R 0775 /usr/share/icons
$ echo gtk-icon-theme-name=\"gnome\" >> ~/.gtkrc-2.0
```

---

### Post by stchman on 2007-11-08
> **freakavoid said:**
> Hi,

I did a lot of searching and cannot figure out why my evolution toolbar looks like this. It's not an icon theme issue; I tried different ones. I recently did a fresh install of gutsy and that's when evolution mail started to appear without icons. No problems with another application.

Thanks in advance for your help.

[IMG]http://i46.photobucket.com/albums/f122/onReflection/evolution-toolbar.jpg[/IMG]

Try this:

Uninstall Evolution
```
sudo apt-get -y autoremove evolution
```

Go into Synaptic and remove all residual configuration files.

Reinstall Evolution
```
sudo apt-get -y install evolution
```

Let us know how it works out.

---

### Post by freakavoid on 2007-11-08
Sorry, I already tried uninstalling it and it didn't work even with the purge option of apt-get. And I'm using gnome. Thanks for the suggestions though.

---

