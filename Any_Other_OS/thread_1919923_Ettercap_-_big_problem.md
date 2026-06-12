---
title: "Ettercap - big problem"
date: 2012-02-03
forum: Any Other OS
---

### Post by alcapony007 on 2012-02-03
Hi, everyone

I have big problem with ettercap..
I wanted to install ettecap but when I hit ./configure command i have:

checking for pkg-config... /usr/bin/pkg-config
checking for GTK... no
configure: error: Package requirements (gtk+-2.0 >= 2.0.0 pango >= 1.0 atk >= 1.0) were not met:

No package 'gtk+-2.0' found
No package 'pango' found
No package 'atk' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I tried to install gtk-3.0 but there is second problem. BackTrack wants another packeges...

I tried also .deb but it's also a problem:
 dpkg -i gir1.2-gtk-3.0_3.2.3-1_i386.deb
Zaznaczenie poprzednio niezaznaczonego pakietu gir1.2-gtk-3.0.
(Odczytywanie bazy danych ... 282136 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie gir1.2-gtk-3.0 (z gir1.2-gtk-3.0_3.2.3-1_i386.deb) ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 zale&#380;y od libgtk-3-common; jednak&#380;e:
  Pakiet libgtk-3-common not installed.
 gir1.2-gtk-3.0 zale&#380;y od gir1.2-atk-1.0; jednak&#380;e:
  Pakiet gir1.2-atk-1.0 nie jest zainstalowany.
 gir1.2-gtk-3.0 zale&#380;y od gir1.2-freedesktop; jednak&#380;e:
  Pakiet gir1.2-freedesktop nie jest zainstalowany.
 gir1.2-gtk-3.0 zale&#380;y od gir1.2-gdkpixbuf-2.0; jednak&#380;e:
  Pakiet gir1.2-gdkpixbuf-2.0 nie jest zainstalowany.
 gir1.2-gtk-3.0 zale&#380;y od gir1.2-glib-2.0; jednak&#380;e:
  Pakiet gir1.2-glib-2.0 not installed
 gir1.2-gtk-3.0 zale&#380;y od gir1.2-pango-1.0; jednak&#380;e:
  Pakiet gir1.2-pango-1.0 nie jest zainstalowany.
 gir1.2-gtk-3.0 zale&#380;y od libgtk-3-0 (>= 3.2.1); jednak&#380;e:
  Pakiet libgtk-3-0 nie jest zainstalowany.
dpkg: b&#322;&#261;d przetwarzania gir1.2-gtk-3.0 (--install):
 problemy z zale&#380;no&#347;ciami - not configured
errors during installation:
 gir1.2-gtk-3.0
root@:~# 


By the way if someone can help with ettercup send L3 error (message too long)
please help I can't figure it out,
regards,
Jack

---

### Post by coffeecat on 2012-02-03
Moved from Forum Feedback and Help to Other OS since this is a Backtrack problem.

---

