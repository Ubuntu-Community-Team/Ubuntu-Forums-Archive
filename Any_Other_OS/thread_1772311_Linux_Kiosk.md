---
title: "Linux Kiosk"
date: 2011-05-31
forum: Any Other OS
---

### Post by createdcreature on 2011-05-31
I am wondering if there is a way to make a Linux Kiosk for a shop/info point, that no-one will be able to tamper with, that will only have Firefox. It does not need to have a customised UI, because Firefox will be in full screen mode. I have tried stripping down Ubuntu with Synaptic, but I cannot remove some things without removing the entire Ubuntu shell. Do you have any suggestions? I do not like Tiny Core and Micro Core. The Kiosk can have as much RAM as you need it to, and it has a 256MB ATI Radeon and a 3.2GHz Pentium D. I am new to KDE and customising it.

---

### Post by wolfen69 on 2011-05-31
I've tried [Webconverger]("http://webconverger.com/") and it works good.

---

### Post by kk0sse54 on 2011-05-31
You could also just run X without a window manager and with Firefox fullscreen in which any distro will work. Otherwise poke around google as I'm sure there's a couple kiosk style distros.

---

### Post by createdcreature on 2011-06-01
How would I do that?

---

### Post by kk0sse54 on 2011-06-01
It depends on your setup for example if you're just starting X through your .xinitrc then all you would need is 

```
xsetroot -solid grey
firefox
```

Then in order to get firefox fullscreen you can manually specify the geometry using the -height -width options.

Ideally however you'd want to use one of the firefox plugins like R-Kiosk which unfortunately doesn't work on Firefox 4 yet. Furthermore this setup is extremely basic but won't allow any user to move windows or start anymore applications in X which sounds like what you want. You can also use a login manager if you prefer in addition to having the computer automatically login or start X.

---

### Post by createdcreature on 2011-06-03
So how would I edit that? Where is it?

---

### Post by lykwydchykyn on 2011-06-03
I've been doing kiosks like this for years.  My advice:

The .xinitrc (you can also use .xsession) is located in the user's home directory.  So if you have a user named "kiosk", you create /home/kiosk/.xinitrc or /home/kiosk/.xsession (don't remember the difference between the two, but it's subtle and probably irrelevant).

Here's a sample .xsession file from one of my kiosks:
```

xset -dpms
xset s off
matchbox-window-manager &

while true;do
	rsync -qr --delete --exclude='.Xauthority' /etc/profiles.d/kiosk/ $HOME/

	wcgbrowser -f	
done

```

What this does is:
  - The first two lines prevent the monitor from going blank after a time.
  - The next line launches the matchbox window manager, which is in the repositories.  You might not need a WM, but I've found that some programs don't fullscreen correctly without one; and, if you get any dialogs opening up or anything, it can be a little disorienting without a WM.  Matchbox is perfect for kiosks.  I've also used FLWM, ion3, XFWM, and others.
  - Then I start an infinite loop
  - First line in the loop refreshes the kiosk user's home directory from a read-only copy in /etc/profiles.d/
  - Next line launches my custom browser app fullscreen.

Since those last two are in a loop, closing the browser resets the kiosk user's home and relaunches the browser.  

I don't know what version of Firefox you plan on using, but I'll warn you that I've found it's getting harder and harder to use for kiosks.  Most of the plugins I used to use don't work with V4.  Chromium and Opera have much better built-in kiosk modes, though I eventually decided to write my own browser using PyQT and webkit than mess with locking down a full-featured browser.

---

### Post by psrdotcom on 2011-09-15
Thanks for sharing the info.
I am planning to have a KIOSK with Opera latest version in Ubuntu 10.10/11.04

I would like to have it on Live CD, I have done some modifications in the OS with my own scripts etc .. which should run before this KIOSK start ..

Can you please guide me?

---

