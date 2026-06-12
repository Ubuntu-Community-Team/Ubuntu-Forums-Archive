---
title: "No right click?"
date: 2020-07-01
forum: Apple Hardware Users
---

### Post by roachbit on 2020-07-01
Howdy!

Wiped OSX from an old MacBook3,1 and installed Lubuntu 19.04 (LQXt desktop). Trouble is, I can't get my right-click working. Not with command(or control, or fn, etc.)+click, not with two-finger+click, not with F12. Nothin'. I've been searching for the answer, but most threads seem to be dealing with the later track pad with no physical button to click.

I'm completely new to Linux and terminal commands, and while I've managed the install and gotten my wifi and iSight working through the terminal, getting a right click and boot under several minutes has eluded me. Any help is appreciated.

I've maxed out the RAM, but everything else is standard for a [FONT=arial]Late 2007 - MB061LL/B - MacBook3,1 - A1181 - 2200.[/FONT]

---

### Post by gsahli on 2020-07-06
Have you tried Option/Alt + click?  (I don't have a macbook)

---

### Post by daniewicz on 2020-07-06
[COLOR=#000000]When you boot do you see a screen enabling you to select different options, or is the screen blank for a lengthy period of time?[/COLOR]

[COLOR=#000000]Older Macs have a 32-bit EFI and your linux install is 64 bit. This can cause issues.[/COLOR]

---

### Post by danish-bronco on 2020-08-27
Don't know about Lubuntu, but in Xubuntu (32-bit with the 5.36.x kernel), right-click works by tapping the lower right corner of the Trackpad on my early 2006 MacBook Pro. Since your MacBook is more recent, it should work on it too. Try and install XFCE as your desktop environment, open a session in it and check if it works. 

Otherwise, you can install Gnome Tweak Tools via sudo in Terminal or your app install GUI, launch it and choose an area for right-click instead of two fingers. 

You can also try the method depicted here: [https://www.void.gr/kargig/blog/2009/06/11/handling-right-clicks-on-a-macbook-running-linux/](https://www.void.gr/kargig/blog/2009/06/11/handling-right-clicks-on-a-macbook-running-linux/)

You can also install Touchegg: [https://www.addictivetips.com/ubuntu-linux-tips/get-macbook-touchpad-gestures-on-linux/](https://www.addictivetips.com/ubuntu-linux-tips/get-macbook-touchpad-gestures-on-linux/)

There was also a Gnome utility I can't find trace of anymore that would allow you to long-press your Trackpad until the pointer completely changed color, and on depress, you'd see the contextual menu appear. I can't for the life of me remember how it's called... :-(

---

