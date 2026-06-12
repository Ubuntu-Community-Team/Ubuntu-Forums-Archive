---
title: "2 Questions"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by vitalstatistix on 2007-03-12
Hey everyone I am new to ubuntu, and need help on these issues:

1) I've installed Limewire 4.12.11(free), and want to uninstall it now, but dont know how to.

2) What's Cedega and how do I install it?

Please help me out. Thanks

---

### Post by xyz on 2007-03-12
Hi,
See here: [CEDEGA]("https://help.ubuntu.com/community/Cedega")
How did you install Limewire?

---

### Post by siciliancasanova on 2007-03-12
You might be able to just go to **applications > add/remove...** depending on how you installed limewire

---

### Post by vitalstatistix on 2007-03-12
Thanks for the quick replies. Well I installed limewire by converting the rpm from their site to deb. Its not available in synaptic. About Cedega I have the following files with me:

cedega-engine-5.2.10-local-update.i386.cpkg
cedega-small-5.2.3.tgz
cedega-small-5.2.3-1.i386.rpm
cedega-small-mandriva-5.2.3-1.i386.rpm
cedega-small-suse-5.2.3-1.i386.rpm
Which do I use ? I got em from this [torrent]("http://torrents.thepiratebay.org/3634523/cedega-5.2.10__everything.3634523.TPB.torrent").

---

### Post by siciliancasanova on 2007-03-12
I haven't used checkinstall but it might work for you.  [This guide ]("http://www.psychocats.net/ubuntu/installingsoftware")is good for add/removal of software.

---

### Post by xyz on 2007-03-12
If you run the following command line, what does it say?
```
locate limewire
```

---

### Post by vitalstatistix on 2007-03-12
Sorry [siciliancasanova]("http://ubuntuforums.org/member.php?u=251590") 					 that link shows only hoe to install. XYZ here's the output:

```
locate limewire
/var/lib/dpkg/info/limewire-free.md5sums
/var/lib/dpkg/info/limewire-free.list
/softwares/Program Files/P2P/LimeWire/root/magnet10/limewire.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/limewire.props
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/01_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/02_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/03_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/04_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/05_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/chat.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/dir_closed.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/dir_open.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/forward_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/forward_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/kill.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/kill_on.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/lime.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/logo.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/notsearching.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/pause_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/pause_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/play_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/play_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/question.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/rewind_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/rewind_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/searching.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/splash.png
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/stop_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/stop_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/theme.txt
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme/warning.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewirePro_theme.lwtp
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/01_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/02_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/03_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/04_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/05_star.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/chat.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/dir_closed.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/dir_open.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/forward_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/forward_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/kill.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/kill_on.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/lime.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/logo.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/notsearching.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/pause_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/pause_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/play_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/play_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/question.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/rewind_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/rewind_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/searching.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/splash.png
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/splashpro.png
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/stop_dn.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/stop_up.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/theme.txt
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme/warning.gif
/windows/Documents and Settings/Administrator/Application Data/LimeWire/themes/limewire_theme.lwtp
/home/tatun/My Softwares/LimeWire/limewire-free_4.12.11-1_i386.deb
/home/tatun/My Softwares/LimeWire/limewire-pro_4.10.5-1_i386.deb
/home/tatun/.limewire
/home/tatun/.limewire/xml
/home/tatun/.limewire/xml/data
/home/tatun/.limewire/xml/data/delete_me
/home/tatun/.limewire/xml/data/audio.sxml
/home/tatun/.limewire/xml/misc
/home/tatun/.limewire/xml/misc/application.gif
/home/tatun/.limewire/xml/misc/audio.gif
/home/tatun/.limewire/xml/misc/image.gif
/home/tatun/.limewire/xml/misc/video.gif
/home/tatun/.limewire/xml/misc/document.gif
/home/tatun/.limewire/xml/schemas
/home/tatun/.limewire/xml/schemas/audio.xsd
/home/tatun/.limewire/xml/schemas/video.xsd
/home/tatun/.limewire/xml/schemas/application.xsd
/home/tatun/.limewire/xml/schemas/document.xsd
/home/tatun/.limewire/xml/schemas/image.xsd
/home/tatun/.limewire/themes
/home/tatun/.limewire/themes/GTK_theme.lwtp
/home/tatun/.limewire/themes/GTK_theme
/home/tatun/.limewire/themes/GTK_theme/01_star.gif
/home/tatun/.limewire/themes/GTK_theme/02_star.gif
/home/tatun/.limewire/themes/GTK_theme/03_star.gif
/home/tatun/.limewire/themes/GTK_theme/04_star.gif
/home/tatun/.limewire/themes/GTK_theme/05_star.gif
/home/tatun/.limewire/themes/GTK_theme/chat.gif
/home/tatun/.limewire/themes/GTK_theme/forward_dn.gif
/home/tatun/.limewire/themes/GTK_theme/forward_up.gif
/home/tatun/.limewire/themes/GTK_theme/kill.gif
/home/tatun/.limewire/themes/GTK_theme/kill_on.gif
/home/tatun/.limewire/themes/GTK_theme/logo.png
/home/tatun/.limewire/themes/GTK_theme/notsearching.png
/home/tatun/.limewire/themes/GTK_theme/pause_dn.gif
/home/tatun/.limewire/themes/GTK_theme/pause_up.gif
/home/tatun/.limewire/themes/GTK_theme/play_dn.gif
/home/tatun/.limewire/themes/GTK_theme/play_up.gif
/home/tatun/.limewire/themes/GTK_theme/question.gif
/home/tatun/.limewire/themes/GTK_theme/rewind_dn.gif
/home/tatun/.limewire/themes/GTK_theme/rewind_up.gif
/home/tatun/.limewire/themes/GTK_theme/searching.gif
/home/tatun/.limewire/themes/GTK_theme/splash.png
/home/tatun/.limewire/themes/GTK_theme/splashpro.png
/home/tatun/.limewire/themes/GTK_theme/stop_dn.gif
/home/tatun/.limewire/themes/GTK_theme/stop_up.gif
/home/tatun/.limewire/themes/GTK_theme/theme.txt
/home/tatun/.limewire/themes/GTK_theme/warning.gif
/home/tatun/.limewire/themes/black_theme.lwtp
/home/tatun/.limewire/themes/black_theme
/home/tatun/.limewire/themes/black_theme/01_star.gif
/home/tatun/.limewire/themes/black_theme/02_star.gif
/home/tatun/.limewire/themes/black_theme/03_star.gif
/home/tatun/.limewire/themes/black_theme/04_star.gif
/home/tatun/.limewire/themes/black_theme/05_star.gif
/home/tatun/.limewire/themes/black_theme/chat.gif
/home/tatun/.limewire/themes/black_theme/dir_closed.gif
/home/tatun/.limewire/themes/black_theme/dir_open.gif
/home/tatun/.limewire/themes/black_theme/forward_dn.gif
/home/tatun/.limewire/themes/black_theme/forward_up.gif
/home/tatun/.limewire/themes/black_theme/kill.gif
/home/tatun/.limewire/themes/black_theme/kill_on.gif
/home/tatun/.limewire/themes/black_theme/lime.gif
/home/tatun/.limewire/themes/black_theme/logo.gif
/home/tatun/.limewire/themes/black_theme/notsearching.gif
/home/tatun/.limewire/themes/black_theme/pause_dn.gif
/home/tatun/.limewire/themes/black_theme/pause_up.gif
/home/tatun/.limewire/themes/black_theme/play_dn.gif
/home/tatun/.limewire/themes/black_theme/play_up.gif
/home/tatun/.limewire/themes/black_theme/question.gif
/home/tatun/.limewire/themes/black_theme/rewind_dn.gif
/home/tatun/.limewire/themes/black_theme/rewind_up.gif
/home/tatun/.limewire/themes/black_theme/searching.gif
/home/tatun/.limewire/themes/black_theme/splash.png
/home/tatun/.limewire/themes/black_theme/splashpro.png
/home/tatun/.limewire/themes/black_theme/stop_dn.gif
/home/tatun/.limewire/themes/black_theme/stop_up.gif
/home/tatun/.limewire/themes/black_theme/theme.txt
/home/tatun/.limewire/themes/black_theme/warning.gif
/home/tatun/.limewire/themes/classic_theme.lwtp
/home/tatun/.limewire/themes/classic_theme
/home/tatun/.limewire/themes/classic_theme/01_star.gif
/home/tatun/.limewire/themes/classic_theme/02_star.gif
/home/tatun/.limewire/themes/classic_theme/03_star.gif
/home/tatun/.limewire/themes/classic_theme/04_star.gif
/home/tatun/.limewire/themes/classic_theme/05_star.gif
/home/tatun/.limewire/themes/classic_theme/chat.gif
/home/tatun/.limewire/themes/classic_theme/dir_closed.gif
/home/tatun/.limewire/themes/classic_theme/dir_open.gif
/home/tatun/.limewire/themes/classic_theme/forward_dn.gif
/home/tatun/.limewire/themes/classic_theme/forward_up.gif
/home/tatun/.limewire/themes/classic_theme/kill.gif
/home/tatun/.limewire/themes/classic_theme/logo.gif
/home/tatun/.limewire/themes/classic_theme/notsearching.gif
/home/tatun/.limewire/themes/classic_theme/pause_dn.gif
/home/tatun/.limewire/themes/classic_theme/pause_up.gif
/home/tatun/.limewire/themes/classic_theme/play_dn.gif
/home/tatun/.limewire/themes/classic_theme/play_up.gif
/home/tatun/.limewire/themes/classic_theme/question.gif
/home/tatun/.limewire/themes/classic_theme/rewind_dn.gif
/home/tatun/.limewire/themes/classic_theme/rewind_up.gif
/home/tatun/.limewire/themes/classic_theme/search.gif
/home/tatun/.limewire/themes/classic_theme/searching.gif
/home/tatun/.limewire/themes/classic_theme/splash.png
/home/tatun/.limewire/themes/classic_theme/splashpro.png
/home/tatun/.limewire/themes/classic_theme/stop_dn.gif
/home/tatun/.limewire/themes/classic_theme/stop_up.gif
/home/tatun/.limewire/themes/classic_theme/theme.txt
/home/tatun/.limewire/themes/classic_theme/warning.gif
/home/tatun/.limewire/themes/limewire_theme.lwtp
/home/tatun/.limewire/themes/limewire_theme
/home/tatun/.limewire/themes/limewire_theme/01_star.gif
/home/tatun/.limewire/themes/limewire_theme/02_star.gif
/home/tatun/.limewire/themes/limewire_theme/03_star.gif
/home/tatun/.limewire/themes/limewire_theme/04_star.gif
/home/tatun/.limewire/themes/limewire_theme/05_star.gif
/home/tatun/.limewire/themes/limewire_theme/chat.gif
/home/tatun/.limewire/themes/limewire_theme/dir_closed.gif
/home/tatun/.limewire/themes/limewire_theme/dir_open.gif
/home/tatun/.limewire/themes/limewire_theme/forward_dn.gif
/home/tatun/.limewire/themes/limewire_theme/forward_up.gif
/home/tatun/.limewire/themes/limewire_theme/kill.gif
/home/tatun/.limewire/themes/limewire_theme/kill_on.gif
/home/tatun/.limewire/themes/limewire_theme/lime.gif
/home/tatun/.limewire/themes/limewire_theme/logo.gif
/home/tatun/.limewire/themes/limewire_theme/notsearching.gif
/home/tatun/.limewire/themes/limewire_theme/pause_dn.gif
/home/tatun/.limewire/themes/limewire_theme/pause_up.gif
/home/tatun/.limewire/themes/limewire_theme/play_dn.gif
/home/tatun/.limewire/themes/limewire_theme/play_up.gif
/home/tatun/.limewire/themes/limewire_theme/question.gif
/home/tatun/.limewire/themes/limewire_theme/rewind_dn.gif
/home/tatun/.limewire/themes/limewire_theme/rewind_up.gif
/home/tatun/.limewire/themes/limewire_theme/searching.gif
/home/tatun/.limewire/themes/limewire_theme/splash.png
/home/tatun/.limewire/themes/limewire_theme/splashpro.png
/home/tatun/.limewire/themes/limewire_theme/stop_dn.gif
/home/tatun/.limewire/themes/limewire_theme/stop_up.gif
/home/tatun/.limewire/themes/limewire_theme/theme.txt
/home/tatun/.limewire/themes/limewire_theme/warning.gif
/home/tatun/.limewire/themes/other_theme.lwtp
/home/tatun/.limewire/themes/other_theme
/home/tatun/.limewire/themes/other_theme/01_star.gif
/home/tatun/.limewire/themes/other_theme/02_star.gif
/home/tatun/.limewire/themes/other_theme/03_star.gif
/home/tatun/.limewire/themes/other_theme/04_star.gif
/home/tatun/.limewire/themes/other_theme/05_star.gif
/home/tatun/.limewire/themes/other_theme/chat.gif
/home/tatun/.limewire/themes/other_theme/forward_dn.gif
/home/tatun/.limewire/themes/other_theme/forward_up.gif
/home/tatun/.limewire/themes/other_theme/kill.gif
/home/tatun/.limewire/themes/other_theme/kill_on.gif
/home/tatun/.limewire/themes/other_theme/logo.png
/home/tatun/.limewire/themes/other_theme/notsearching.png
/home/tatun/.limewire/themes/other_theme/pause_dn.gif
/home/tatun/.limewire/themes/other_theme/pause_up.gif
/home/tatun/.limewire/themes/other_theme/play_dn.gif
/home/tatun/.limewire/themes/other_theme/play_up.gif
/home/tatun/.limewire/themes/other_theme/question.gif
/home/tatun/.limewire/themes/other_theme/rewind_dn.gif
/home/tatun/.limewire/themes/other_theme/rewind_up.gif
/home/tatun/.limewire/themes/other_theme/searching.gif
/home/tatun/.limewire/themes/other_theme/splash.png
/home/tatun/.limewire/themes/other_theme/splashpro.png
/home/tatun/.limewire/themes/other_theme/stop_dn.gif
/home/tatun/.limewire/themes/other_theme/stop_up.gif
/home/tatun/.limewire/themes/other_theme/theme.txt
/home/tatun/.limewire/themes/other_theme/warning.gif
/home/tatun/.limewire/412splashfree.png
/home/tatun/.limewire/version.key
/home/tatun/.limewire/pub1.key
/home/tatun/.limewire/public.key
/home/tatun/.limewire/secureMessage.key
/home/tatun/.limewire/data.ser
/home/tatun/.limewire/limewire.props
/home/tatun/.limewire/installation.props
/home/tatun/.limewire/library.dat
/home/tatun/.limewire/gnutella.net
/home/tatun/.limewire/tables.props
/home/tatun/.limewire/spam.dat
/home/tatun/.limewire/responses.cache
/home/tatun/.limewire/fileurns.cache
/home/tatun/.limewire/createtimes.cache
/home/tatun/.limewire/update.xml
/home/tatun/.limewire/version.xml
/home/tatun/.limewire/simpp.xml
/home/tatun/.limewire/.NetworkShare
/home/tatun/.limewire/.NetworkShare/Incomplete
/home/tatun/.limewire/.NetworkShare/LimeWireWin4.12.6-fixed.exe
/home/tatun/.limewire/fileurns.bak
/home/tatun/.limewire/questions.props
/home/tatun/.limewire/filters.props
/home/tatun/.limewire/ttree.cache
/usr/bin/limewire
/usr/lib/LimeWire/root/magnet10/limewire.gif
/usr/lib/LimeWire/limewire-16.png
/usr/lib/LimeWire/limewire-32.png
/usr/lib/LimeWire/limewire-48.png
/usr/lib/frostwire/root/magnet10/limewire.gif
/usr/share/doc/limewire-free
/usr/share/doc/limewire-free/changelog.Debian.gz
/usr/share/doc/limewire-free/copyright
/usr/share/gnome/help/desktopguide/sample/runLime.sh_limewire
/usr/share/icons/hicolor/16x16/apps/limewire.png
/usr/share/icons/hicolor/32x32/apps/limewire.png
/usr/share/icons/hicolor/48x48/apps/limewire.png
/usr/share/pixmaps/limewire.png
```

---

### Post by Penguin Power on 2007-03-12
Hey, no help with installing/uninstalling software - but if you want to use the gnutella gnetwork (ha, puns!) you're better using Frostwire. It's almost identical to Limewire but it's completely open-source and free. Limewire wouldn't work for me but Frostwire did, and gtk-gnutella is just rubbish ;)

---

### Post by i.am.canadian on 2007-03-12
Hey there if you just converted the file from an rpm to a deb then you probably installed it by double clicking right?  Or did you enter dpkg -i?

If you did the dpkg route (or either way as far as I know) try entering this in the command line ```
dpkg -r limewire
```

If limewire doesn't work find out what you need to enter to call the program from the command line and/ore try typing in the whole file name.  I'm a bit of a noob myself, but this should work.

Cheers.

---

### Post by vitalstatistix on 2007-04-12
Thanks for helping our guys :) . I am checking back so late due to some exams of mine.
Anyway I wanted to uninstall Limewire precisely because of having Frostwire now. The method mentioned by i.am.canadian is exactly what I had done to remove Limewire ```
 dpkg -r limewire-free 
```

---

