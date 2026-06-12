---
title: "Problem"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by exod40 on 2006-04-10
When i restart ot turn on my pc, when i logged in this message appear every time:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

What should i do to remove this message? I'm using Ubuntu.

---

### Post by Sef on 2006-04-10
I found this reply:

> On Wed, Nov 10, 2004 at 09:23:48PM +0100, Ruben Porras wrote:
> $ gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb
>  layouts = [es  es]

Try with just [es].

Your X config is probably not correct.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

If it's not like this, can you try it and log in again after doing
gconftool-2 --recursive-unset /desktop/gnome/peripherals/keyboard ?



Nore: es is a spanish keyboard.  

[http://lists.debian.org/debian-gtk-gnome/2004/11/msg00011.html]("http://lists.debian.org/debian-gtk-gnome/2004/11/msg00011.html")

---

### Post by Don_Toni on 2006-04-12
I have a same problem:
[IMG]http://dontoni.net/gallery/albums/userpics/10001/normal_Error.jpg[/IMG]
> toni@ubuntu:~$ > $ gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb
toni@ubuntu:~$ > layouts = [es es]
bash: =: command not found

My keyboard is bulgarian.

---

### Post by vitoko on 2006-04-14
i fixed with the next command
sudo apt-get install --reinstall xkeyboard-config

---

