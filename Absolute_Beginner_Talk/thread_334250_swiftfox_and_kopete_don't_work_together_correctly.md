---
title: "swiftfox and kopete don't work together correctly"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by hazillow on 2007-01-08
I changed my default web browser (in control panel>kde components>default applications) to swiftfox. When someone sends me a link in kopete it opens into the cache and shows me an offline version of the page. E.g. [http://www.google.com](http://www.google.com) opens in swiftfox to file:///var/tmp/kdecache-joe/krun/11947.0. I've tried to change the file associations of everything that I can think of involving viewing web pages, html, php, etc. to open with swiftfox, but no such luck. Anyone got any ideas?

---

### Post by Bachstelze on 2007-01-08
Please paste the output of

```
ls -l /etc/alternatives
```

If you see a x-www-browser symlink that doesn't point to your swiftfox executable, that's the problem. Just delete it and create a new one instead, pointing to swiftfox.

---

### Post by hazillow on 2007-01-08
Hey -

ln -l doesnt exist, according to the output on the terminal. is that the qualifier you actually meant, or was it a typo? Thanks in advance.

---

### Post by hazillow on 2007-01-09
bump

---

### Post by Bachstelze on 2007-01-09
Yes, typo, it's ls, not ln, sorry :p

---

### Post by hazillow on 2007-01-09
This is the output of that command. I'm not sure what it exactly is I'm looking for. Of course, I'm not asking you to go through this entire thing, just to point me in the right direction (huge newb). Thanks for the help you've provided thus far and hopefully the help you provide in the future.


```
joe@computer:~$ ls -l /etc/alternatives
total 48
lrwxrwxrwx 1 root root  13 2007-01-05 14:51 awk -> /usr/bin/gawk
lrwxrwxrwx 1 root root  29 2007-01-05 14:51 awk.1.gz -> /usr/share/man/man1/gawk
.1.gz
lrwxrwxrwx 1 root root  33 2007-01-06 06:03 btcompletedir -> /usr/bin/btcomplete
dir.bittorrent
lrwxrwxrwx 1 root root  49 2007-01-06 06:03 btcompletedir.1.gz -> /usr/share/man
/man1/btcompletedir.bittorrent.1.gz
lrwxrwxrwx 1 root root  36 2007-01-06 06:03 btdownloadcurses -> /usr/bin/btdownl
oadcurses.bittorrent
lrwxrwxrwx 1 root root  52 2007-01-06 06:03 btdownloadcurses.1.gz -> /usr/share/
man/man1/btdownloadcurses.bittorrent.1.gz
lrwxrwxrwx 1 root root  38 2007-01-06 06:03 btdownloadheadless -> /usr/bin/btdow
nloadheadless.bittorrent
lrwxrwxrwx 1 root root  54 2007-01-06 06:03 btdownloadheadless.1.gz -> /usr/shar
e/man/man1/btdownloadheadless.bittorrent.1.gz
lrwxrwxrwx 1 root root  32 2007-01-06 06:03 btlaunchmany -> /usr/bin/btlaunchman
y.bittorrent
lrwxrwxrwx 1 root root  48 2007-01-06 06:03 btlaunchmany.1.gz -> /usr/share/man/
man1/btlaunchmany.bittorrent.1.gz
lrwxrwxrwx 1 root root  38 2007-01-06 06:03 btlaunchmanycurses -> /usr/bin/btlau
nchmanycurses.bittorrent
lrwxrwxrwx 1 root root  54 2007-01-06 06:03 btlaunchmanycurses.1.gz -> /usr/shar
e/man/man1/btlaunchmanycurses.bittorrent.1.gz
lrwxrwxrwx 1 root root  34 2007-01-06 06:03 btmakemetafile -> /usr/bin/btmakemet
afile.bittorrent
lrwxrwxrwx 1 root root  50 2007-01-06 06:03 btmakemetafile.1.gz -> /usr/share/ma
n/man1/btmakemetafile.bittorrent.1.gz
lrwxrwxrwx 1 root root  32 2007-01-06 06:03 btreannounce -> /usr/bin/btreannounc
e.bittorrent
lrwxrwxrwx 1 root root  48 2007-01-06 06:03 btreannounce.1.gz -> /usr/share/man/
man1/btreannounce.bittorrent.1.gz
lrwxrwxrwx 1 root root  28 2007-01-06 06:03 btrename -> /usr/bin/btrename.bittor
rent
lrwxrwxrwx 1 root root  44 2007-01-06 06:03 btrename.1.gz -> /usr/share/man/man1
/btrename.bittorrent.1.gz
lrwxrwxrwx 1 root root  34 2007-01-06 06:03 btshowmetainfo -> /usr/bin/btshowmet
ainfo.bittorrent
lrwxrwxrwx 1 root root  50 2007-01-06 06:03 btshowmetainfo.1.gz -> /usr/share/ma
n/man1/btshowmetainfo.bittorrent.1.gz
lrwxrwxrwx 1 root root  27 2007-01-06 06:03 bttrack -> /usr/bin/bttrack.bittorre
nt
lrwxrwxrwx 1 root root  43 2007-01-06 06:03 bttrack.1.gz -> /usr/share/man/man1/
bttrack.bittorrent.1.gz
lrwxrwxrwx 1 root root  38 2007-01-03 23:38 builtins.7.gz -> /usr/share/man/man7
/bash-builtins.7.gz
lrwxrwxrwx 1 root root  16 2007-01-03 23:38 c89 -> /usr/bin/c89-gcc
lrwxrwxrwx 1 root root  32 2007-01-03 23:38 c89.1.gz -> /usr/share/man/man1/c89-
gcc.1.gz
lrwxrwxrwx 1 root root  16 2007-01-03 23:38 c99 -> /usr/bin/c99-gcc
lrwxrwxrwx 1 root root  32 2007-01-03 23:38 c99.1.gz -> /usr/share/man/man1/c99-
gcc.1.gz
lrwxrwxrwx 1 root root  12 2007-01-03 23:38 cc -> /usr/bin/gcc
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 cc.1.gz -> /usr/share/man/man1/gcc.1
.gz
lrwxrwxrwx 1 root root  24 2007-01-04 11:51 civ -> /usr/games/civclient-gtk
lrwxrwxrwx 1 root root  38 2007-01-04 11:51 civ.6.gz -> /usr/share/man/man6/civc
lient-gtk.6.gz
lrwxrwxrwx 1 root root  24 2007-01-04 11:51 civclient -> /usr/games/civclient-gt
k
lrwxrwxrwx 1 root root  13 2007-01-06 06:12 cli -> /usr/bin/mono
lrwxrwxrwx 1 root root  29 2007-01-06 06:12 cli.1.gz -> /usr/share/man/man1/mono
.1.gz
lrwxrwxrwx 1 root root  32 2007-01-06 06:13 cli-gacutil.1.gz -> /usr/share/man/m
an1/gacutil.1.gz
lrwxrwxrwx 1 root root  48 2007-01-04 15:21 ControlPanel -> /usr/lib/jvm/java-1.
5.0-sun/jre/bin/ControlPanel
lrwxrwxrwx 1 root root  12 2007-01-03 23:38 cpp -> /usr/bin/cpp
lrwxrwxrwx 1 root root  42 2007-01-08 18:19 desktop-splash -> /usr/share/pixmaps
/splash/gnome-splash.png
lrwxrwxrwx 1 root root   9 2007-01-03 23:38 editor -> /bin/nano
lrwxrwxrwx 1 root root  29 2007-01-03 23:38 editor.1.gz -> /usr/share/man/man1/n
ano.1.gz
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 ex -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 ex.1.gz -> /usr/share/man/man1/vim.1
.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 ex.fr.1.gz -> /usr/share/man/fr/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 ex.fr.ISO8859-1.1.gz -> /usr/share/m
an/fr.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 ex.fr.UTF-8.1.gz -> /usr/share/man/f
r.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 ex.it.1.gz -> /usr/share/man/it/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 ex.it.ISO8859-1.1.gz -> /usr/share/m
an/it.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 ex.it.UTF-8.1.gz -> /usr/share/man/i
t.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 ex.pl.1.gz -> /usr/share/man/pl/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 ex.pl.ISO8859-2.1.gz -> /usr/share/m
an/pl.ISO8859-2/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 ex.pl.UTF-8.1.gz -> /usr/share/man/p
l.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  38 2007-01-03 23:38 ex.ru.KOI8-R.1.gz -> /usr/share/man/
ru.KOI8-R/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 ex.ru.UTF-8.1.gz -> /usr/share/man/r
u.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  59 2007-01-06 06:11 firefox-homepage -> /usr/share/doc/k
de/HTML/en/kubuntu/about-kubuntu/index.html
lrwxrwxrwx 1 root root  68 2007-01-04 15:21 firefox-javaplugin.so -> /usr/lib/jv
m/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root  31 2007-01-05 04:48 freecraft-data -> /usr/share/games/f
reecraft/fcmp
lrwxrwxrwx 1 root root  19 2007-01-03 23:38 ftp -> /usr/bin/netkit-ftp
lrwxrwxrwx 1 root root  35 2007-01-03 23:38 ftp.1.gz -> /usr/share/man/man1/netk
it-ftp.1.gz
lrwxrwxrwx 1 root root  20 2007-01-04 08:14 gconftool -> /usr/bin/gconftool-2
lrwxrwxrwx 1 root root  36 2007-01-04 08:14 gconftool.1.gz -> /usr/share/man/man
1/gconftool-2.1.gz
lrwxrwxrwx 1 root root  16 2007-01-06 06:13 global-assembly-cache-tool -> /usr/b
in/gacutil
lrwxrwxrwx 1 root root  14 2007-01-06 06:10 gnome-text-editor -> /usr/bin/gedit
lrwxrwxrwx 1 root root  30 2007-01-06 06:10 gnome-text-editor.1.gz -> /usr/share
/man/man1/gedit.1.gz
lrwxrwxrwx 1 root root  32 2007-01-04 08:53 gnome-video-thumbnailer -> /usr/bin/
totem-video-thumbnailer
lrwxrwxrwx 1 root root  16 2007-01-06 06:11 gnome-www-browser -> /usr/bin/firefo
x
lrwxrwxrwx 1 root root  32 2007-01-06 06:11 gnome-www-browser.1.gz -> /usr/share
/man/man1/firefox.1.gz
lrwxrwxrwx 1 root root  15 2007-01-03 23:38 gs -> /usr/bin/gs-esp
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 gs.1.gz -> /usr/share/man/man1/gs-es
p.1.gz
lrwxrwxrwx 1 root root  13 2007-01-04 06:16 infobrowser -> /usr/bin/info
lrwxrwxrwx 1 root root  29 2007-01-04 06:16 infobrowser.1.gz -> /usr/share/man/m
an1/info.1.gz
lrwxrwxrwx 1 root root  35 2007-01-03 23:38 irc.protocol -> /usr/share/apps/kope
te/irc.protocol
lrwxrwxrwx 1 root root  40 2007-01-09 14:58 java -> /usr/lib/jvm/java-1.5.0-sun/
jre/bin/java
lrwxrwxrwx 1 root root  59 2007-01-09 14:58 java.1.gz -> /usr/lib/jvm/java-1.5.0
-sun-1.5.0.08/jre/man/man1/java.1.gz
lrwxrwxrwx 1 root root  43 2007-01-04 15:21 java_vm -> /usr/lib/jvm/java-1.5.0-s
un/jre/bin/java_vm
lrwxrwxrwx 1 root root  42 2007-01-04 15:21 javaws -> /usr/lib/jvm/java-1.5.0-su
n/jre/bin/javaws
lrwxrwxrwx 1 root root  61 2007-01-04 15:21 javaws.1.gz -> /usr/lib/jvm/java-1.5
.0-sun-1.5.0.08/jre/man/man1/javaws.1.gz
lrwxrwxrwx 1 root root  43 2007-01-04 15:21 keytool -> /usr/lib/jvm/java-1.5.0-s
un/jre/bin/keytool
lrwxrwxrwx 1 root root  62 2007-01-04 15:21 keytool.1.gz -> /usr/lib/jvm/java-1.
5.0-sun-1.5.0.08/jre/man/man1/keytool.1.gz
lrwxrwxrwx 1 root root  21 2007-01-04 06:59 lrelease -> /usr/bin/lrelease-qt3
lrwxrwxrwx 1 root root  37 2007-01-04 06:59 lrelease.1.gz -> /usr/share/man/man1
/lrelease-qt3.1.gz
lrwxrwxrwx 1 root root  15 2007-01-04 06:59 lua-compiler -> /usr/bin/luac50
lrwxrwxrwx 1 root root  31 2007-01-04 06:59 lua-compiler-manual -> /usr/share/ma
n/man1/luac50.1.gz
lrwxrwxrwx 1 root root  21 2007-01-04 06:59 lua-configuration -> /usr/bin/lua-co
nfig50
lrwxrwxrwx 1 root root  37 2007-01-04 06:59 lua-configuration-manual -> /usr/sha
re/man/man1/lua-config50.1.gz
lrwxrwxrwx 1 root root  14 2007-01-04 06:59 lua-interpreter -> /usr/bin/lua50
lrwxrwxrwx 1 root root  30 2007-01-04 06:59 lua-manual -> /usr/share/man/man1/lu
a50.1.gz
lrwxrwxrwx 1 root root  20 2007-01-04 06:59 lupdate -> /usr/bin/lupdate-qt3
lrwxrwxrwx 1 root root  36 2007-01-04 06:59 lupdate.1.gz -> /usr/share/man/man1/
lupdate-qt3.1.gz
lrwxrwxrwx 1 root root  16 2007-01-04 06:59 moc -> /usr/bin/moc-qt3
lrwxrwxrwx 1 root root  32 2007-01-04 06:59 moc.1.gz -> /usr/share/man/man1/moc-
qt3.1.gz
lrwxrwxrwx 1 root root  16 2007-01-06 06:03 mozilla -> /usr/bin/firefox
lrwxrwxrwx 1 root root  32 2007-01-06 06:03 mozilla.1.gz -> /usr/share/man/man1/
firefox.1.gz
lrwxrwxrwx 1 root root  68 2007-01-04 15:21 mozilla-javaplugin.so -> /usr/lib/jv
m/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root  68 2007-01-04 15:21 mozilla-snapshot-javaplugin.so -> /u
sr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx 1 root root  20 2007-01-04 07:02 mp3-decoder -> /usr/bin/mpg123-alsa
lrwxrwxrwx 1 root root  36 2007-01-04 07:02 mp3-decoder.1.gz -> /usr/share/man/m
an1/mpg123-alsa.1.gz
lrwxrwxrwx 1 root root  20 2007-01-04 07:02 mpg123 -> /usr/bin/mpg123-alsa
lrwxrwxrwx 1 root root  36 2007-01-04 07:02 mpg123.1.gz -> /usr/share/man/man1/m
pg123-alsa.1.gz
lrwxrwxrwx 1 root root  11 2007-01-03 23:38 mt -> /bin/mt-gnu
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 mt.1.gz -> /usr/share/man/man1/mt-gn
u.1.gz
lrwxrwxrwx 1 root root  13 2007-01-05 14:51 nawk -> /usr/bin/gawk
lrwxrwxrwx 1 root root  29 2007-01-05 14:51 nawk.1.gz -> /usr/share/man/man1/gaw
k.1.gz
lrwxrwxrwx 1 root root  40 2007-01-04 15:21 orbd -> /usr/lib/jvm/java-1.5.0-sun/
jre/bin/orbd
lrwxrwxrwx 1 root root  59 2007-01-04 15:21 orbd.1.gz -> /usr/lib/jvm/java-1.5.0
-sun-1.5.0.08/jre/man/man1/orbd.1.gz
lrwxrwxrwx 1 root root  43 2007-01-04 15:21 pack200 -> /usr/lib/jvm/java-1.5.0-s
un/jre/bin/pack200
lrwxrwxrwx 1 root root  62 2007-01-04 15:21 pack200.1.gz -> /usr/lib/jvm/java-1.
5.0-sun-1.5.0.08/jre/man/man1/pack200.1.gz
lrwxrwxrwx 1 root root  13 2007-01-04 06:16 pager -> /usr/bin/less
lrwxrwxrwx 1 root root  29 2007-01-04 06:16 pager.1.gz -> /usr/share/man/man1/le
ss.1.gz
lrwxrwxrwx 1 root root  46 2007-01-04 15:21 policytool -> /usr/lib/jvm/java-1.5.
0-sun/jre/bin/policytool
lrwxrwxrwx 1 root root  65 2007-01-04 15:21 policytool.1.gz -> /usr/lib/jvm/java
-1.5.0-sun-1.5.0.08/jre/man/man1/policytool.1.gz
lrwxrwxrwx 1 root root  18 2007-01-04 06:59 qmake -> /usr/bin/qmake-qt3
lrwxrwxrwx 1 root root  12 2007-01-03 23:38 rcp -> /usr/bin/scp
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 rcp.1.gz -> /usr/share/man/man1/scp.
1.gz
-rw-r--r-- 1 root root 100 2006-10-03 13:40 README
lrwxrwxrwx 1 root root  16 2007-01-03 23:38 rename -> /usr/bin/prename
lrwxrwxrwx 1 root root  32 2007-01-03 23:38 rename.1.gz -> /usr/share/man/man1/p
rename.1.gz
lrwxrwxrwx 1 root root  15 2007-01-03 23:38 rlogin -> /usr/bin/slogin
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 rlogin.1.gz -> /usr/share/man/man1/s
login.1.gz
lrwxrwxrwx 1 root root  40 2007-01-04 15:21 rmid -> /usr/lib/jvm/java-1.5.0-sun/
jre/bin/rmid
lrwxrwxrwx 1 root root  59 2007-01-04 15:21 rmid.1.gz -> /usr/lib/jvm/java-1.5.0
-sun-1.5.0.08/jre/man/man1/rmid.1.gz
lrwxrwxrwx 1 root root  47 2007-01-04 15:21 rmiregistry -> /usr/lib/jvm/java-1.5
.0-sun/jre/bin/rmiregistry
lrwxrwxrwx 1 root root  66 2007-01-04 15:21 rmiregistry.1.gz -> /usr/lib/jvm/jav
a-1.5.0-sun-1.5.0.08/jre/man/man1/rmiregistry.1.gz
lrwxrwxrwx 1 root root  17 2007-01-04 06:14 rmt -> /usr/sbin/rmt-tar
lrwxrwxrwx 1 root root  32 2007-01-04 06:14 rmt.8.gz -> /usr/share/man/man8/rmt-
tar.8.gz
lrwxrwxrwx 1 root root  12 2007-01-03 23:38 rsh -> /usr/bin/ssh
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 rsh.1.gz -> /usr/share/man/man1/ssh.
1.gz
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 rview -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 rvim -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  46 2007-01-04 15:21 servertool -> /usr/lib/jvm/java-1.5.
0-sun/jre/bin/servertool
lrwxrwxrwx 1 root root  65 2007-01-04 15:21 servertool.1.gz -> /usr/lib/jvm/java
-1.5.0-sun-1.5.0.08/jre/man/man1/servertool.1.gz
lrwxrwxrwx 1 root root  34 2007-01-06 06:10 ssh-askpass -> /usr/lib/openssh/gnom
e-ssh-askpass
lrwxrwxrwx 1 root root  42 2007-01-06 06:10 ssh-askpass.1.gz -> /usr/share/man/m
an1/gnome-ssh-askpass.1.gz
lrwxrwxrwx 1 root root  17 2007-01-04 12:58 tclsh -> /usr/bin/tclsh8.4
lrwxrwxrwx 1 root root  33 2007-01-04 12:58 tclsh.1 -> /usr/share/man/man1/tclsh
8.4.1.gz
lrwxrwxrwx 1 root root  22 2007-01-03 23:38 telnet -> /usr/bin/telnet.netkit
lrwxrwxrwx 1 root root  38 2007-01-03 23:38 telnet.1.gz -> /usr/share/man/man1/t
elnet.netkit.1.gz
lrwxrwxrwx 1 root root  45 2007-01-04 15:21 tnameserv -> /usr/lib/jvm/java-1.5.0
-sun/jre/bin/tnameserv
lrwxrwxrwx 1 root root  64 2007-01-04 15:21 tnameserv.1.gz -> /usr/lib/jvm/java-
1.5.0-sun-1.5.0.08/jre/man/man1/tnameserv.1.gz
lrwxrwxrwx 1 root root  16 2007-01-04 06:59 uic -> /usr/bin/uic-qt3
lrwxrwxrwx 1 root root  32 2007-01-04 06:59 uic.1.gz -> /usr/share/man/man1/uic-
qt3.1.gz
lrwxrwxrwx 1 root root  45 2007-01-04 15:21 unpack200 -> /usr/lib/jvm/java-1.5.0
-sun/jre/bin/unpack200
lrwxrwxrwx 1 root root  64 2007-01-04 15:21 unpack200.1.gz -> /usr/lib/jvm/java-
1.5.0-sun-1.5.0.08/jre/man/man1/unpack200.1.gz
lrwxrwxrwx 1 root root  41 2007-01-06 06:11 usplash-artwork.so -> /usr/lib/uspla
sh/usplash-theme-kubuntu.so
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 vi -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 vi.1.gz -> /usr/share/man/man1/vim.1
.gz
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 view -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  28 2007-01-03 23:38 view.1.gz -> /usr/share/man/man1/vim
.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 view.fr.1.gz -> /usr/share/man/fr/ma
n1/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 view.fr.ISO8859-1.1.gz -> /usr/share
/man/fr.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 view.fr.UTF-8.1.gz -> /usr/share/man
/fr.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 view.it.1.gz -> /usr/share/man/it/ma
n1/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 view.it.ISO8859-1.1.gz -> /usr/share
/man/it.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 view.it.UTF-8.1.gz -> /usr/share/man
/it.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 view.pl.1.gz -> /usr/share/man/pl/ma
n1/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 view.pl.ISO8859-2.1.gz -> /usr/share
/man/pl.ISO8859-2/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 view.pl.UTF-8.1.gz -> /usr/share/man
/pl.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  38 2007-01-03 23:38 view.ru.KOI8-R.1.gz -> /usr/share/ma
n/ru.KOI8-R/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 view.ru.UTF-8.1.gz -> /usr/share/man
/ru.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 vi.fr.1.gz -> /usr/share/man/fr/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 vi.fr.ISO8859-1.1.gz -> /usr/share/m
an/fr.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 vi.fr.UTF-8.1.gz -> /usr/share/man/f
r.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 vi.it.1.gz -> /usr/share/man/it/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 vi.it.ISO8859-1.1.gz -> /usr/share/m
an/it.ISO8859-1/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 vi.it.UTF-8.1.gz -> /usr/share/man/i
t.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 vim -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 vimdiff -> /usr/bin/vim.tiny
lrwxrwxrwx 1 root root  31 2007-01-03 23:38 vi.pl.1.gz -> /usr/share/man/pl/man1
/vim.1.gz
lrwxrwxrwx 1 root root  41 2007-01-03 23:38 vi.pl.ISO8859-2.1.gz -> /usr/share/m
an/pl.ISO8859-2/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 vi.pl.UTF-8.1.gz -> /usr/share/man/p
l.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  38 2007-01-03 23:38 vi.ru.KOI8-R.1.gz -> /usr/share/man/
ru.KOI8-R/man1/vim.1.gz
lrwxrwxrwx 1 root root  37 2007-01-03 23:38 vi.ru.UTF-8.1.gz -> /usr/share/man/r
u.UTF-8/man1/vim.1.gz
lrwxrwxrwx 1 root root  22 2007-01-06 05:59 vncpasswd -> /usr/bin/realvncpasswd
lrwxrwxrwx 1 root root  38 2007-01-06 05:59 vncpasswd.1.gz -> /usr/share/man/man
1/realvncpasswd.1.gz
lrwxrwxrwx 1 root root  23 2007-01-06 06:02 vncviewer -> /usr/bin/xrealvncviewer
lrwxrwxrwx 1 root root  39 2007-01-06 06:02 vncviewer.1.gz -> /usr/share/man/man
1/xrealvncviewer.1.gz
lrwxrwxrwx 1 root root  17 2007-01-03 23:38 w -> /usr/bin/w.procps
lrwxrwxrwx 1 root root  33 2007-01-03 23:38 w.1.gz -> /usr/share/man/man1/w.proc
ps.1.gz
lrwxrwxrwx 1 root root  16 2007-01-04 12:58 wish -> /usr/bin/wish8.4
lrwxrwxrwx 1 root root  32 2007-01-04 12:58 wish.1 -> /usr/share/man/man1/wish8.
4.1.gz
lrwxrwxrwx 1 root root  18 2007-01-03 23:38 write -> /usr/bin/bsd-write
lrwxrwxrwx 1 root root  34 2007-01-03 23:38 write.1.gz -> /usr/share/man/man1/bs
d-write.1.gz
lrwxrwxrwx 1 root root  12 2007-01-04 06:16 www-browser -> /usr/bin/w3m
lrwxrwxrwx 1 root root  28 2007-01-04 06:16 www-browser.1.gz -> /usr/share/man/m
an1/w3m.1.gz
lrwxrwxrwx 1 root root  36 2007-01-06 06:11 x-cursor-theme -> /usr/share/icons/k
ubuntu/index.theme
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-all_ALL -> /etc/X11/xinit/xin
put.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-ja_JP -> /etc/X11/xinit/xinpu
t.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-ko_KR -> /etc/X11/xinit/xinpu
t.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-zh_CN -> /etc/X11/xinit/xinpu
t.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-zh_HK -> /etc/X11/xinit/xinpu
t.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-zh_SG -> /etc/X11/xinit/xinpu                                 t.d/scim
lrwxrwxrwx 1 root root  28 2007-01-06 06:13 xinput-zh_TW -> /etc/X11/xinit/xinpu                                 t.d/scim
lrwxrwxrwx 1 root root  22 2007-01-08 18:19 x-session-manager -> /usr/bin/gnome-                                 session
lrwxrwxrwx 1 root root  38 2007-01-08 18:19 x-session-manager.1.gz -> /usr/share                                 /man/man1/gnome-session.1.gz
lrwxrwxrwx 1 root root  31 2007-01-08 18:19 x-terminal-emulator -> /usr/bin/gnom                                 e-terminal.wrapper
lrwxrwxrwx 1 root root  39 2007-01-08 18:19 x-terminal-emulator.1.gz -> /usr/sha                                 re/man/man1/gnome-terminal.1.gz
lrwxrwxrwx 1 root root  23 2007-01-06 06:02 xvncviewer -> /usr/bin/xrealvncviewe                                 r
lrwxrwxrwx 1 root root  39 2007-01-06 06:02 xvncviewer.1.gz -> /usr/share/man/ma                                 n1/xrealvncviewer.1.gz
lrwxrwxrwx 1 root root  17 2007-01-06 06:10 x-window-manager -> /usr/bin/metacit                                 y
lrwxrwxrwx 1 root root  33 2007-01-06 06:10 x-window-manager.1.gz -> /usr/share/                                 man/man1/metacity.1.gz
lrwxrwxrwx 1 root root  18 2007-01-06 06:03 x-www-browser -> /usr/bin/konqueror
lrwxrwxrwx 1 root root  34 2007-01-06 06:03 x-www-browser.1.gz -> /usr/share/man                                 /man1/konqueror.1.gz

```

---

### Post by calvmari on 2007-01-09
I've got it!!

Here's how you do it, 

1) Go to System Settings (K-menu --> System Settings)
2) In the first row, go to "Default Applications"
3) From the left list, select: "Web Browser"
4) In the right field, select the second radio button: "in the following browser:"
5) In the text field, enter: /opt/swiftfox/swiftfox
6) Click apply

The problem is that when you select it from the list (the ... box on the right), it just enters "swiftfox" instead of the whole "/opt/swiftfox/swiftfox", which it needs. I'm not even going to pretend I know why it does the whole download thing, but this fix works!

Attached are a few images to help you along the way.

---

### Post by Uron on 2007-06-16
Thanks it really help me out

---

