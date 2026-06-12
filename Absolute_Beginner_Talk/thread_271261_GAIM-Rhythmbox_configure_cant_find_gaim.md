---
title: "GAIM-Rhythmbox configure cant find gaim"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Anonii on 2006-10-04
Hello,

I'm using Gaim2.0.0beta3.1 for Edgy. I'm trying to ./configure the package "gaim-rhythmbox", not available in the reps. Get it here: [http://sourceforge.net/projects/gaim-rhythmbox/](http://sourceforge.net/projects/gaim-rhythmbox/)
The problem is, that the configure script cant find my GAIM.

```
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gaim... configure: error: Package requirements (gaim >= 2.0.0) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables gaim_CFLAGS
and gaim_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I have GAIM installed and its here:

```
$ dpkg -S gaim
tango-icon-theme-common: /usr/share/icons/Tango/24x24/apps/gaim.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_ooooh.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_smiley.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sheep.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/wink.png
gaim: /usr/bin/gaim
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_eyeroll.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_whistling.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_talktohand.gif
gaim-data: /usr/share/pixmaps/gaim-menu.xpm
gaim-data: /usr/share/pixmaps/gaim/smileys/default/theme
gaim-data: /usr/share/pixmaps/gaim/status/default/invisible.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_shhhh.gif
gaim: /usr/bin/gaim-send
gnome-orca: /usr/share/python-support/gnome-orca/orca/scripts/gaim.py
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_cake.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_yingyang.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/female.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_loser.gif
gaim: /usr/lib/gaim/dbus-example.so
gaim-data: /usr/share/pixmaps/gaim/status/default/simple.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_secret.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_cellphone.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_silly.gif
gaim: /usr/lib/gaim/timestamp_format.so
gaim: /usr/lib/gaim/notify.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_neutral.png
gaim-data: /usr/share/pixmaps/gaim/status-connect0.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_brb.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_eyeroll.gif
gaim-data: /usr/share/pixmaps/gaim/buttons/edit.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sleep.png
gaim-data: /usr/share/doc/gaim-data/AUTHORS
gaim-data: /usr/share/pixmaps/gaim/status/default/aim.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_think.gif
gaim: /usr/lib/gaim/iconaway.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/tongue.png
gaim-data: /usr/share/pixmaps/gaim/buttons/insert-image-small.png
gaim-data: /usr/share/pixmaps/gaim/status/default/pending.png
gaim-data: /usr/share/doc/gaim-data/changelog.Debian.gz
gaim: /usr/lib/gaim/liboscar.so
gaim: /usr/share/menu/gaim
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_devil.png
gaim-data: /usr/share/doc/gaim-data/FAQ.gz
gaim-data: /usr/share/pixmaps/gaim/buttons/send-im.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_coffee.png
gaim-data: /usr/share/doc/gaim-data
gaim-data: /usr/share/sounds/gaim/logout.wav
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sad.png
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_info.png
gaim-data: /usr/share/pixmaps/gaim/status/default/aol.png
gaim-data: /usr/share/sounds/gaim
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_glasses.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_laughloud.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_flag.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/notauthorized.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_car.png
gaim-data: /usr/share/pixmaps/gaim/buttons/about_menu.png
nautilus-sendto: /usr/lib/gaim/nautilus.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_nerd.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_shame.gif
gaim: /usr/lib/gaim/psychic.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/embarrassed.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/angel.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_silent.gif
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_error.png
gaim: /usr/lib/gaim/libyahoo.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_pumpkin.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_laugh.png
tango-icon-theme-common: /usr/share/icons/Tango/16x16/apps/gaim.png
gaim-data: /usr/share/pixmaps/gaim/status/default/bonjour.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_peace.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_fingerscrossed.png
gnome-accessibility-themes: /usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gaim.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_hypnotized.gif
gaim: /usr/lib/gaim/ssl-nss.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_cigarette.gif
gaim: /usr/lib/gaim/idle.so
gaim-data: /usr/share/pixmaps/gaim/typed.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_online.png
gaim-data: /usr/share/pixmaps/gaim/status/default/yahoo.png
gaim-data: /usr/share/man/man1/gaim.1.gz
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_turtle.png
gaim-data: /usr/share/pixmaps/gaim/status/default/napster.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_angry.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/smile.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_cow.gif
gaim-data: /usr/share/pixmaps/gaim/status
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_beer.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_away.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_party.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/founder.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/cool.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sick.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_tongue.gif
gaim: /usr/lib/gaim/statenotify.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yell.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_alien.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_soccer.png
gaim-data: /usr/share/pixmaps/gaim/status-typing0.png
gaim-data: /usr/share/pixmaps/gaim/status-connect1.png
gaim: /usr/lib/gaim/ssl-gnutls.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sweating.gif
gaim-data: /usr/share/sounds/gaim/receive.wav
gaim-data: /usr/share/pixmaps/gaim/smileys/default/luke.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_xbox.png
gaim: /usr/lib/gaim/gaimrc.so
gaim-data: /usr/share/pixmaps/gaim/status/default
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_computer.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_alien2.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_occ.png
gaim-data: /usr/share/doc/gaim-data/COPYRIGHT.gz
tango-icon-theme-common: /usr/share/icons/Tango/22x22/apps/gaim.png
gaim, nautilus-sendto: /usr/lib/gaim
gaim: /usr/lib/gaim/history.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_mean.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_plane.png
gaim-data: /usr/share/pixmaps/gaim/tb_drag_arrow_down.xpm
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_question.png
gaim-data: /usr/share/pixmaps/gaim/status/default/extended_away.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/mrt.png
gaim: /usr/lib/gaim/libzephyr.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_heart.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_kiss.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_think.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/download.png
gaim-data: /usr/share/doc/gaim-data/changelog.gz
gaim-data: /usr/share/pixmaps/gaim/smileys/default/sad.png
gaim-data: /usr/share/pixmaps/gaim/buttons/change-bgcolor-small.png
gaim-data: /usr/share/sounds/gaim/alert.wav
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_lightning.gif
gaim-data: /usr/share/doc/gaim-data/TODO.gz
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_drool.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_tired.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_youkiddingme.gif
gaim-data: /usr/share/pixmaps/gaim/buttons
gaim-data: /usr/share/pixmaps/gaim/buttons/text_normal.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_brheart.png
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_question.png
gaim-data: /etc/gaim
gaim: /usr/share/dbus-1/services/gaim.service
gaim-data: /usr/share/pixmaps/gaim/buttons/accounts.png
gaim: /usr/lib/gaim/libgg.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/think.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_smiley.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sunglasses.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_deadflower.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_nailbiting.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_drink.png
gaim: /usr/lib/gaim/timestamp.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_blush.gif
gaim: /usr/bin/gaim-client-example
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_waving.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/moneymouth.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/burp.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_dog.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_rotfl.gif
gaim: /usr/share/doc/gaim
gaim-data: /usr/share/pixmaps/gaim/icons/away.png
gaim-data: /usr/share/pixmaps/gaim.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_bigsmile.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/logout.png
gaim-data: /usr/share/pixmaps/gaim/tb_drag_arrow_right.xpm
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_chicken.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/cry.png
gaim-data: /usr/share/pixmaps/gaim/status-typing1.png
gaim-data: /usr/share/pixmaps/gaim/status-connect2.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_film.png
gaim-data: /usr/share/pixmaps/gaim/buttons/pause.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_island.png
gaim-data: /usr/share/pixmaps/gaim/status-online.png
gaim: /usr/lib/gaim/libnovell.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_dontknow.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_note.png
gaim-data: /usr/share/pixmaps/gaim/icons/stock_connect_16.png
gaim: /usr/lib/libgaim-client.so.0
gaim: /usr/share/applications/gaim.desktop
gaim-data: /usr/share/pixmaps/gaim/typing.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_angel.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_worship.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_teeth.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_waiting.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/halfop.png
gaim: /usr/lib/gaim/spellchk.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_pray.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_handcuffs.png
gaim: /usr/lib/gaim/perl.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_beatup.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/none/theme
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_cat.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_ooooh.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_plate.png
gaim-data: /usr/share/pixmaps/gaim/status/default/male.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/oneeye.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_monkey.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/login.png
gaim-data: /usr/share/pixmaps/gaim/status/default/freeforchat.png
gaim-data: /usr/share/pixmaps/gaim/status/default/offline.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/farted.png
gaim-data: /usr/share/pixmaps/gaim/status/default/nr.png
gaim-data: /usr/share/pixmaps/gaim/icons/connect.png
ubuntu-docs: /usr/share/ubuntu-docs/ubuntu/menus/C/gaim.xml
language-pack-en-base: /usr/share/locale-langpack/en_GB/LC_MESSAGES/gaim.mo
gaim-data: /usr/share/pixmaps/gaim/status/default/msn.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sad.gif
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_auth.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_bowl.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/bigsmile.png
gaim-data: /usr/share/pixmaps/gaim/status-away.png
gaim: /usr/lib/gaim/gevolution.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sleep.gif
gaim-data: /etc/gaim/prefs.xml
gaim: /usr/lib/gaim/gestures.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_malefighter1.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_idea.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_tongue.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_run.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_devil.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/admin.png
gaim-data: /usr/share/pixmaps/gaim/status-offline.png
gaim: /usr/lib/gaim/tcl.so
gaim: /usr/lib/gaim/ssl.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_eyebrow.gif
tango-icon-theme-common: /usr/share/icons/Tango/scalable/apps/gaim.svg
gaim-data: /usr/share/pixmaps/gaim/status/default/occupied.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_email.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_stormy.png
gaim-data: /usr/share/pixmaps/gaim/status/default/novell.png
gaim-data: /usr/share/pixmaps/gaim/status-typing2.png
gaim-data: /usr/share/pixmaps/gaim/status-connect3.png
gaim-data: /usr/share/pixmaps/gaim/icons/offline.png
app-install-data: /usr/share/app-install/icons/gaim.png
gaim-data: /usr/share/pixmaps/gaim/status/default/game.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_cowboy.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_brokenheart.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_moneyeyes.gif
gaim-data: /usr/share/pixmaps/gaim.svg
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_clown.gif
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_cool.png
gaim-data: /usr/share/pixmaps/gaim/tb_drag_arrow_up.xpm
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_thumbup.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/crazy.png
nautilus-sendto: /usr/lib/nautilus-sendto/plugins/libnstgaim.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_star.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/jabber.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_wink.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_worried.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_clock.png
gaim-data: /usr/share/pixmaps/gaim/status/default/wireless.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_weird.png
gaim-data: /usr/share/pixmaps/gaim/phone.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_cry.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sighing.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_hot.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_femalefighter.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_wink.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_snail.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_gift.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_flower.gif
gaim-data: /usr/share/pixmaps/gaim/buttons/music.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_kiss.png
gaim-data: /usr/share/pixmaps/gaim/buttons/insert-link-small.png
gaim-data: /usr/share/sounds/gaim/send.wav
gaim-data: /usr/share/pixmaps/gaim/smileys/default/crossedlips.png
gaim: /usr/lib/libgaim-client.so.0.0.0
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sleepy.gif
language-pack-en-base: /usr/share/locale-langpack/en_AU/LC_MESSAGES/gaim.mo
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_neutral.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/kiss.png
gaim: /usr/lib/gaim/musicmessaging.so
gaim: /usr/lib/gaim/libmsn.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_malefighter2.gif
gaim: /usr/lib/gaim/libsimple.so
gaim-data: /usr/share/pixmaps/gaim/icons/msgunread.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_girl.png
gaim-data: /usr/share/pixmaps/gaim/status/default/icq.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_huggs.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_angry.png
gaim-data: /usr/share/doc/gaim-data/CREDITS
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_highfive.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_frustrated.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/secure.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_donttell.png
gaim-data: /usr/share/pixmaps/gaim/status-typing3.png
gaim-data: /usr/share/pixmaps/gaim/icons/msgpend.png
gaim-data: /usr/share/pixmaps/gaim
gaim-data: /usr/share/pixmaps/gaim/logo.png
gaim-data: /usr/share/pixmaps/gaim/status/default/zephyr.png
gnome-accessibility-themes: /usr/share/icons/HighContrastLargePrint/48x48/apps/gaim.png
gaim: /usr/bin/gaim-send-async
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_rainbow.png
app-install-data: /usr/share/app-install/desktop/gaim.desktop
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_liar.gif
gaim: /usr/lib/gaim/ticker.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sarcastic.png
gaim-data: /usr/share/pixmaps/gaim/buttons/insert-smiley-small.png
gaim-data: /usr/share/pixmaps/gaim/smileys
gaim-data: /usr/share/pixmaps/gaim/tb_drag_arrow_left.xpm
gaim-data: /usr/share/pixmaps/gaim/status/default/hiptop.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_coffee.gif
gaim-data: /usr/share/pixmaps/gaim/buttons/change-fgcolor-small.png
gaim-data: /usr/share/pixmaps/gaim/dialogs/gaim_warning.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_madtongue.gif
gaim-data: /usr/share/doc/gaim-data/copyright
gaim-data: /usr/share/pixmaps/gaim/buttons/text_bigger.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_pig.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_sun.png
gaim-data: /usr/share/pixmaps/gaim/status/default/ignored.png
gaim-data: /usr/share/pixmaps/gaim/icons
gaim-data: /usr/share/pixmaps/gaim/status/default/blocked.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_embarrassed.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sick.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_coins.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_runback.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_icon.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_clap.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_boy.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_bat.gif
gaim-data: /usr/share/pixmaps/gaim/status-invisible.png
gaim-data: /usr/share/pixmaps/gaim/status/default/external.png
gaim-data: /usr/share/pixmaps/gaim/status/default/op.png
language-pack-en-base: /usr/share/locale-langpack/en_CA/LC_MESSAGES/gaim.mo
gaim: /usr/lib/gaim/docklet.so
gaim-data: /usr/share/pixmaps/gaim/status/default/irc.png
gaim-data: /usr/share/pixmaps/gaim/status/default/activebuddy.png
gaim: /usr/lib/gaim/relnot.so
gaim-data: /usr/share/pixmaps/gaim/icons/stock_disconnect_16.png
gaim-data: /usr/share/pixmaps/gaim/status/default/dnd.png
gaim-data: /usr/share/pixmaps/gaim/icons/online.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_angel.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/voice.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_cry.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_bye.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/gadu-gadu.png
gaim-data: /usr/share/pixmaps/gaim/status/default/silc.png
gaim-data: /usr/share/doc/gaim-data/README.gz
gaim: /usr/lib/gaim/libjabber.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_photo.png
gaim: /usr/lib/gaim/extplacement.so
gaim-data: /usr/share/pixmaps/gaim/buttons/info.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_thumbdown.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_shamrock.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_love.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_sunglas.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_idea.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_dance.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_doh.gif
gaim-data: /usr/share/pixmaps/gaim/status/default/away.png
gaim-data: /usr/share/pixmaps/gaim/dialogs
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_question.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_batting.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/scream.png
gaim-data: /usr/share/sounds/gaim/login.wav
gaim: /usr/lib/gaim/libirc.so
gaim-data: /usr/share/pixmaps/gaim/buttons/text_smaller.png
gaim-data: /usr/share/doc/gaim-data/NEWS.gz
gaim-data: /usr/share/pixmaps/gaim/smileys/none
gaim-data: /usr/share/pixmaps/gaim/status/default/meanwhile.png
gaim-data: /usr/share/pixmaps/gaim/status/default/unavailable.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_ghost.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_flower.png
gaim: /usr/lib/gaim/libgaimperl.so
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_star.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_umbrella.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_pizza.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_party.gif
gaim-data: /usr/share/pixmaps/gaim/smileys/default/msn_phone.png
gaim-data: /usr/share/pixmaps/gaim/smileys/default/yahoo_giggle.gif

```


Well, I have two scenarios in my head:
a) The beta version doesnt support that plugin.
But it still says that it cant find the "gaim >= 2.0.0" so I guess that it supports it...
b) The GAIM package is not where it is supposed to be, which I highly doubt.


Finally, I also tried the other versions for previous GAIMs, but I had the same error.

Any ideas?

Thanks!

---

### Post by m_gasior on 2006-10-04
Have you installed gaim-dev package?

---

### Post by Anonii on 2006-10-04
> **m_gasior said:**
> Have you installed gaim-dev package?
Hihi..
DIdnt know that..
Thanks!

---

### Post by Mark76 on 2006-10-07
I tried to install gaim-dev, first from the repositories and then from the terminal.

This is what I got

> sudo apt-get install gaim-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gaim-dev: Depends: gaim (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) but 1:1.9.99.is.2.0.0+beta3-1ubuntu1 is to be installed
            Depends: gaim-data (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) but 1:1.9.99.is.2.0.0+beta3-1ubuntu1 is to be installed
E: Broken packages


I'm using the gaim 2 beta available via Automatix.

---

### Post by baytuni on 2006-11-03
I had the same problem. I did the gaim-dev thing. Then another error has come: ```
checking for gtk2... configure: error: Package requirements (gtk+-2.0 >= 2.4) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables gtk2_CFLAGS
and gtk2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by ecoxmit on 2007-02-03
sudo apt-get install libdbus-1-dev libgtk2.0-dev libdbus-glib-1-dev
solved those dependencies issues for me.

---

