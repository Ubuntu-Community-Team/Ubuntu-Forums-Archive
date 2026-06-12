---
title: "Removing GNOME, etc."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by TexasBob on 2006-07-07
Greetings Ubuntulings,

Just installed Ubuntu on a small wireless-only Thinkpad, Pentium III, 750 MHz, 256 MB RAM. Eveything works fine, but GNOME is too resource intensive, so installed Xfce and like it just fine. Is there some safe way to remove GNOME and other resource intensive components? If so, what should I remove? I see some of the apps I run in Xfce have the GNOME footprint and suppose these need GNOME something or other to run, hopefully just libraries that are easy to identify and protect from deletion. I basically use a text editor, TeX (which I installed from TeXLive 2005 rather than teTeX, since teTeX is no longer supported), GIMP and Inkscape, plus Thunderbird and Firefox, and Open Office now and then. So what can I uninstall without hurting the system? Thanks.

Oh, BTW, I searched google and the forums and found nothing but instructions for minimizing installation during initial set up. What I want to do is post installation removal of things I don't use and never will.

Thanks.

\Tex asBob
(a \TeX\ joke) [http://www.tug.org/](http://www.tug.org/)

---

### Post by RavenOfOdin on 2006-07-07
As to apps in XFCE "having the GNOME footprint", you should be able to turn off GNOME program compatibility from inside the XFCE settings menu. I think its inside "Window Manager Tweaks" - someone correct me if I'm wrong.

Don't know what to remove, except maybe try gnome-desktop.

---

### Post by nalmeth on 2006-07-07
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

This is a guide to removing gnome or kde, leaving you with your installed xfce.

I know someone who had an issue with it, it removed LAMP and it's configuration, also when I tried it recently, removing gnome removed a whole lot of KDE stuff too for some reason, and changed around a lot of my fonts and settings.

At least it may be a guide to what gnome consists of on your system. How you procede is in your hands.

---

### Post by TexasBob on 2006-07-07
Thanks for your responses. My solution--and so far, so good, but not very pretty--is:

(1) using the Synaptic Package Manager, 
(2) going to the Gnome Desktop Environment section, 
(3) deleting the desktop which takes out a lot of other things, 
(4) leaving alone anything that starts with "lib" because someone wrote someplace to not delete the gnome libraries, 
(5) also leaving alone anything that comes back saying it's also going to remove something related to xubuntu and 
(6) not touching the gnome rey-ring or mime-data. 

I just read some of the "howtos" plus the descriptions in Synaptic and try to devine whether it will kill something else to remove an item. 

Realistically, I am probably going to start over and reinstall using the server CD and then add in Xfce and other things need. We'll just see what the server installs and what the application packages also install. 

Again I just use TeX (from TeXLive at [http://www.tug.org/)](http://www.tug.org/)), Inkspace, Gimp, Firefox and Thunderbird, plus a text editor for TeX and for that I might just use vi or vim. I tried emacs and found the key-binding thing to be too difficult. I may add Scribus to do page layout, maybe, but Inkspace does that also, sort of, and TeX does this too, through ConTeXt and some of the LaTeX packages.

---

