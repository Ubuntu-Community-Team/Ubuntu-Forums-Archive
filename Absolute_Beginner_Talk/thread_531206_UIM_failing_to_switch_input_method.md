---
title: "UIM failing to switch input method"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Natume on 2007-08-21
As of yesterday, I've gotten UIM along with its dependencies installed on my new computer, which happens to be running Feisty.  I've never had problems with UIM on Edgy, which is currently running on my other computer, but despite the settings being exactly the same on this and the other, I can't get UIM to switch to the Anthy input method from direct input (or anything, really).  

The odd part about this is that if I place the UIM applet for gnome in the menu bar, I can manually switch from one IM to the other with my mouse and have no problems whatsoever : the functionality is completely normal in that respect.  I'd like to get the <shift>space key combination working for toggling input methods (which is what I use on the Edgy computer), but I have no idea where to start.

Just for reference, I installed using the following command (from a presumably blank slate) :

```
sudo apt-get install uim uim-anthy uim-gtk2.0 uim-qt uim-applet-gnome
```

Also, my en_US file (referenced by a link in ~/.xinput.d/) looks like such :

```
XIM=uim
XIM_PROGRAM=/usr/bin/uim-xim
XIM_ARGS=
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="uim-xim,uim-gtk2.0|uim-qt,uim-anthy|uim-canna|uim-prime|uim-skk|uim-m17nlib"
```

This is just about identical to the one that I use on the Edgy laptop.  I did try changing the IM_MODULE= for both GTK and QT to uim, but nothing different has happened, even after restarting the computer.

And it may not matter much, but Feisty is being run on a Dell D630 laptop with the keyboard type set to 'pc105' with a 'us' layout.  I've actually been surprised at how well everything else has gotten up and running on the Dell, all things considered, so I tend not to think that it's something about the keyboard / computer that's preventing me from changing the input mode, but I haven't completely ruled it out.

Any help is appreciated.

~Natume

---

