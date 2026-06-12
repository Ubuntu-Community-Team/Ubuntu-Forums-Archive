---
title: "Manually install fonts Bitstream Vera fonts"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2007-05-13
I am trying to get google earth to stop complaining about missing Bitstream Vera fonts. It gave me a link from which to download the fonts. I have the fonts unpackaged, but I don't know how to install them.

I put the local.conf in my /etc/fonts directory according to
[http://www.gnome.org/fonts/](http://www.gnome.org/fonts/)
but that did nothing.

I looked at [http://ubuntuforums.org/showthread.php?t=275202](http://ubuntuforums.org/showthread.php?t=275202) and it seems to offer a script that installs fonts in /usr/share/fonts/truetype; what's the difference between /etc/fonts and /usr/share/fonts/truetype ? 

This site, [http://penguinfonts.com/howto/ubuntu.php](http://penguinfonts.com/howto/ubuntu.php), recommends donwloading some KDE application to isntall the fonts, but I don't use KDE nor do I want to start using KDE.

Any help or insight on font installing is much appreciated.

---

### Post by Bachstelze on 2007-05-13
That's weird, I was sure those fonts were installed in Ubuntu by default... Anyway, a low-hassle way to add them would be to create a .fonts subdir in your home dir and put your TTF files in it.

---

