---
title: "safe graphics mode (live cd)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Dinghe on 2008-04-02
since a while i changed my monitor into an lcd tv, now since this change i get a black screen after the loading screen (no login screen). now i want a fresh install of ubuntu, but the live cd also gives a black screen after the loading bar. I also tried safe graphics mode but it also wont work. 
What is the resolution that the safe graphics mode uses? is it still to big for my tv resolution? (1360 x 768 60Hz) Or lies the problem somewere else?

this is my setup:
intel pentium 4 3GHz
nvidia geforce 6200 agp card
old monitor: philips s107 (1024 x 1280 60Hz)
new monitor(tv): samsung 26" (1360 x 768 60Hz)

---

### Post by philinux on 2008-04-02
Boot up the pc as normal with new monitor plugged in. Then

Press ctrl-alt-f1 when you come to the "blank screen" Then log in to a console
then
sudo dpkg-reconfigure xserver-xorg

---

### Post by forrestcupp on 2008-04-02
And if the ctrl-alt-F1 doesn't work, boot to your recovery mode, which should be the 2nd option on your GRUB boot menu, and type the same command without sudo because you'll already be in root
```
dpkg-reconfigure xserver-xorg
```
Maybe in this setup, it would be wise to choose the vesa drivers to give yourself a better chance of getting a working desktop.  You can get the correct video drivers working after that.

---

### Post by Dinghe on 2008-04-02
thanks for the help.
but i wanted to da a fresh install, because my previous one was pretty messed up.
I cant start in normal mode, its hangs after the starting up, please wait loading prompts.
and recovery also won't work, at a certain moment it says dropping to command shel initramfs.
now i've tried to boot the live cd and hit ctrl-alt-f1, then i can configure xorg, but how can i then boot up into the live cd after the configuring? or am i configuring the xorg of my messed up install?
can tell me how i can boot the live cd? or chould i better use my old monitor and do a fresh install and then use the new lcd tv an do the command you told?

---

### Post by philinux on 2008-04-02
I'd be tempted either to burn the alternate cd. Or the live cd of Hardy 8.04 beta. It has improved hardware detection.

I'm on Hardy and its very stable.

---

### Post by Dinghe on 2008-04-02
thanks for the reply's i'm downloading hardy right now, and i hope to have more succes with it.

---

### Post by Duck2006 on 2008-04-02
> **Dinghe said:**
> thanks for the reply's i'm downloading hardy right now, and i hope to have more succes with it.

If you still have problems try the text base install, (alternate desktop CD).

---

### Post by Dinghe on 2008-04-02
I've been looking through the manual of my tv an I found this:
[IMG]http://img385.imageshack.us/img385/7523/tvreskp5.jpg[/IMG]
I don't know if this helps? maybe with this info I can still use 7.10 ?
Doesnt vesa has something to do with linux or am I wrong?

---

