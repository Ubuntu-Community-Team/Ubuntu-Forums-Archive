---
title: "How to alter the Floatng Ubuntu screensaver?"
date: 2007-05-27
forum: Art &amp; Design
---

### Post by exploder on 2007-05-27
I would like to change the Floating Ubuntu screen saver so it displays the new LinuxMint Logo. Fedora used their logo and so have other distributions. I am not sure this is the proper category to ask, but it is art related.

I can't even find a folder relating to the screen saver. Can someone point me in the right direction? I know this can be done, I just need some guidance.

I really like Feisty and the new Mint beta based on Feisty and would like to try and contribute to their efforts.

---

### Post by hikaricore on 2007-05-28
The screensaver config files are located at /usr/share/applications/screensavers

And the specific one you're asking about (ubuntu_theme.desktop) points to the image file /usr/share/pixmaps/ubuntu.svg

Hope this is what you needed.  ^_^

> ]$ cat /usr/share/applications/screensavers/ubuntu_theme.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Floating Ubuntu
Comment=Ubuntu logo floating around the screen
Exec=floaters /usr/share/pixmaps/ubuntu.svg
TryExec=floaters
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver
X-Ubuntu-Gettext-Domain=gnome-screensaver


---

