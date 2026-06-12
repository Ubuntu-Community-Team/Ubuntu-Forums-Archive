---
title: "Help installing gipmsg on gutsy"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by karthikophobia on 2007-12-05
i tried installing gipmsg on gutsy
when i type 'make' i get the following error message:
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gnome-config... (cached) no
checking for gnomeConf.sh file in /usr/local/lib... not found
checking extra library "applets"... ./configure: 1126: no: not found

checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for POSIXized ISC... no
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -O2 ) works... yes
checking whether the C compiler (gcc -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
checking for object suffix... o
checking for executable suffix... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... chmod: .: new permissions are r-xrwxrwx, not r-xr-xr-x
yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache ./config.cache
checking what warning flags to pass to the C compiler... -Wall -Wunused
checking what language compliance flags to pass to the C compiler... 
checking for pthread_create in -lpthread... (cached) yes
checking for gtk-config... (cached) /usr/bin/gtk-config
checking for GTK - version >= 1.2.0... yes
checking for SmcSaveYourselfDone in -lSM... (cached) yes
checking for X11/SM/SMlib.h... (cached) yes
checking for XpmFreeXpmImage in -lXpm... (cached) no
checking for working const... (cached) yes
checking for inline... (cached) inline
checking for off_t... (cached) yes
checking for size_t... (cached) yes
checking for working alloca.h... (cached) yes
checking for alloca... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking for argz.h... (cached) yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for getcwd... (cached) yes
checking for munmap... (cached) yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for setlocale... (cached) yes
checking for strchr... (cached) yes
checking for strcasecmp... (cached) yes
checking for strdup... (cached) yes
checking for __argz_count... (cached) yes
checking for __argz_stringify... (cached) yes
checking for __argz_next... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... (cached) yes
checking for gettext in libc... (cached) yes
checking for msgfmt... (cached) no
checking whether catgets can be used... no
checking for msgfmt... (cached) no
checking for gmsgfmt... (cached) no
checking for xgettext... (cached) :
checking for catalogs to be installed...  ja
checking for gettext... (cached) yes
checking for dlfcn.h... (cached) yes
checking for dl.h... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for X11/extensions/xf86misc.h... (cached) no
checking for esd-config... (cached) /usr/bin/esd-config
checking for ESD - version >= 0.2.7... yes
checking whether to enable applet... no
creating ./config.status
creating Makefile
creating src/Makefile
creating intl/Makefile
creating po/Makefile.in
creating config.h
config.h is unchanged
linking ./intl/libgettext.h to intl/libintl.h
karthikophobia@BD-102:/media/sda6/Downloads/gipmsg-0.4.0beta1$ make
make  all-recursive
make[1]: Entering directory `/media/sda6/Downloads/gipmsg-0.4.0beta1'
Making all in src
make[2]: Entering directory `/media/sda6/Downloads/gipmsg-0.4.0beta1/src'
gcc -DHAVE_CONFIG_H -I. -I. -I..        -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -g -O2 -Wall -Wunused  -c main.c
main.c:13:19: error: gnome.h: No such file or directory
In file included from main.c:18:
properties.h:13: error: expected specifier-qualifier-list before ‘guint16’
properties.h:41: error: expected ‘)’ before ‘*’ token
properties.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
properties.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
properties.h:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
properties.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from main.c:19:
win.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:43: error: expected ‘)’ before ‘*’ token
win.h:49: error: expected ‘)’ before ‘*’ token
win.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:57: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:61: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
win.h:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from main.c:20:
ipmsg.h:115: error: expected specifier-qualifier-list before ‘gchar’
ipmsg.h:126: error: expected specifier-qualifier-list before ‘gint’
ipmsg.h:145: error: expected specifier-qualifier-list before ‘guint’
ipmsg.h:162: error: expected specifier-qualifier-list before ‘guint’
ipmsg.h:176: error: expected ‘)’ before ‘port’
ipmsg.h:180: error: expected ‘)’ before ‘data’
ipmsg.h:181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IPMsgSend’
ipmsg.h:182: error: expected ‘)’ before ‘com’
ipmsg.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IPMsgReSendData’
ipmsg.h:184: error: expected ‘)’ before ‘mode’
ipmsg.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ipmsg.h:192: error: expected declaration specifiers or ‘...’ before ‘guint32’
ipmsg.h:193: error: expected declaration specifiers or ‘...’ before ‘guint32’
ipmsg.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ipmsg.h:207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sendWin_clist_comp’
ipmsg.h:219: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ipmsg.h:224: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IPMsgNonPopupTimeout’
ipmsg.h:232: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘nIPMsgNonPopup’
In file included from main.c:21:
sig.h:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
sig.h:37: error: expected ‘)’ before ‘*’ token
sig.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_sendWin_key_press_event’
sig.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_sendWinEv_button_press_event’
sig.h:51: error: expected ‘)’ before ‘*’ token
sig.h:55: error: expected ‘)’ before ‘*’ token
sig.h:59: error: expected ‘)’ before ‘*’ token
sig.h:63: error: expected ‘)’ before ‘*’ token
sig.h:67: error: expected ‘)’ before ‘*’ token
sig.h:71: error: expected ‘)’ before ‘*’ token
sig.h:75: error: expected ‘)’ before ‘*’ token
sig.h:79: error: expected ‘)’ before ‘*’ token
sig.h:83: error: expected ‘)’ before ‘*’ token
sig.h:87: error: expected ‘)’ before ‘*’ token
sig.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_sendUserList_button_press_event’
sig.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_menu_select_group_cb’
sig.h:101: error: expected ‘)’ before ‘*’ token
sig.h:105: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWin_delete_event’
sig.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWin_button_press_event’
sig.h:115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWin_button_press_event’
sig.h:120: error: expected ‘)’ before ‘*’ token
sig.h:124: error: expected ‘)’ before ‘*’ token
sig.h:129: error: expected ‘)’ before ‘*’ token
sig.h:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWin_button_press_event’
sig.h:138: error: expected ‘)’ before ‘*’ token
sig.h:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWinEv_key_press_event’
sig.h:148: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_buttonWinEv_button_press_event’
sig.h:153: error: expected ‘)’ before ‘*’ token
sig.h:157: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_logWin_delete_event’
sig.h:162: error: expected ‘)’ before ‘*’ token
sig.h:167: error: expected ‘)’ before ‘*’ token
sig.h:171: error: expected ‘)’ before ‘*’ token
sig.h:180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_popupmenu_fuzai_cb’
sig.h:183: error: expected ‘)’ before ‘user_data’
sig.h:186: error: expected ‘)’ before ‘user_data’
sig.h:189: error: expected ‘)’ before ‘user_data’
sig.h:197: error: expected ‘)’ before ‘*’ token
sig.h:200: error: expected ‘)’ before ‘*’ token
sig.h:203: error: expected ‘)’ before ‘*’ token
main.c: In function ‘kill_exit_proc’:
main.c:63: warning: implicit declaration of function ‘alarm’
main.c:64: warning: implicit declaration of function ‘exit’
main.c:64: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:64: error: ‘EXIT_SUCCESS’ undeclared (first use in this function)
main.c:64: error: (Each undeclared identifier is reported only once
main.c:64: error: for each function it appears in.)
main.c: In function ‘trap_usr1’:
main.c:69: warning: implicit declaration of function ‘IPMsgOpenSendWin’
main.c: At top level:
main.c:72: error: array type has incomplete element type
main.c:73: error: ‘POPT_ARG_STRING’ undeclared here (not in a function)
main.c:73: warning: implicit declaration of function ‘N_’
main.c:76: error: ‘POPT_ARG_INT’ undeclared here (not in a function)
main.c:76: error: ‘struct OPTION_T’ has no member named ‘port’
main.c:77: error: ‘struct OPTION_T’ has no member named ‘localnet_bcast’
main.c: In function ‘main_quit’:
main.c:107: warning: implicit declaration of function ‘gtk_main_quit’
main.c: At top level:
main.c:111: error: expected ‘)’ before ‘client_data’
main.c:118: error: expected ‘)’ before ‘*’ token
main.c:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c: In function ‘main’:
main.c:160: error: ‘GnomeClient’ undeclared (first use in this function)
main.c:160: error: ‘smClient’ undeclared (first use in this function)
main.c:162: error: expected specifier-qualifier-list before ‘gint’
main.c:163: warning: excess elements in struct initializer
main.c:163: warning: (near initialization for ‘geom’)
main.c:163: warning: excess elements in struct initializer
main.c:163: warning: (near initialization for ‘geom’)
main.c:163: warning: excess elements in struct initializer
main.c:163: warning: (near initialization for ‘geom’)
main.c:163: warning: excess elements in struct initializer
main.c:163: warning: (near initialization for ‘geom’)
main.c:164: error: ‘GtkWidget’ undeclared (first use in this function)
main.c:164: error: ‘app’ undeclared (first use in this function)
main.c:178: warning: implicit declaration of function ‘bindtextdomain’
main.c:179: warning: implicit declaration of function ‘textdomain’
main.c:188: warning: implicit declaration of function ‘gnome_init_with_popt_table’
main.c:189: error: ‘winMain’ undeclared (first use in this function)
main.c:189: warning: implicit declaration of function ‘gnome_app_new’
main.c:191: warning: implicit declaration of function ‘newGnomeClient’
main.c:192: warning: implicit declaration of function ‘gtk_signal_connect’
main.c:192: warning: implicit declaration of function ‘GTK_OBJECT’
main.c:193: warning: implicit declaration of function ‘GTK_SIGNAL_FUNC’
main.c:193: error: ‘on_buttonWin_destroy’ undeclared (first use in this function)
main.c:195: warning: implicit declaration of function ‘getenv’
main.c:195: warning: assignment makes pointer from integer without a cast
main.c:199: warning: implicit declaration of function ‘IPMsgSetup’
main.c:199: error: ‘struct OPTION_T’ has no member named ‘port’
main.c:200: warning: implicit declaration of function ‘create_buttonWin’
main.c:211: warning: implicit declaration of function ‘gnome_parse_geometry’
main.c:211: error: ‘struct <anonymous>’ has no member named ‘x’
main.c:211: error: ‘struct <anonymous>’ has no member named ‘y’
main.c:211: error: ‘struct <anonymous>’ has no member named ‘w’
main.c:211: error: ‘struct <anonymous>’ has no member named ‘h’
main.c:212: warning: implicit declaration of function ‘gtk_widget_set_uposition’
main.c:212: error: ‘struct <anonymous>’ has no member named ‘x’
main.c:212: error: ‘struct <anonymous>’ has no member named ‘y’
main.c:214: error: ‘struct <anonymous>’ has no member named ‘w’
main.c:214: error: ‘struct <anonymous>’ has no member named ‘w’
main.c:215: error: ‘struct <anonymous>’ has no member named ‘h’
main.c:215: error: ‘struct <anonymous>’ has no member named ‘h’
main.c:216: warning: implicit declaration of function ‘gtk_widget_set_usize’
main.c:216: error: ‘struct <anonymous>’ has no member named ‘w’
main.c:216: error: ‘struct <anonymous>’ has no member named ‘h’
main.c:218: warning: implicit declaration of function ‘gtk_widget_show_all’
main.c:219: warning: implicit declaration of function ‘gtk_widget_hide’
main.c:219: warning: implicit declaration of function ‘get_widget’
main.c:219: warning: implicit declaration of function ‘GTK_WIDGET’
main.c:225: warning: implicit declaration of function ‘atexit’
main.c:232: warning: implicit declaration of function ‘gtk_main’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/media/sda6/Downloads/gipmsg-0.4.0beta1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/sda6/Downloads/gipmsg-0.4.0beta1'
make: *** [all-recursive-am] Error 2

plz help

thanq

---

### Post by sourcemorph on 2007-12-05
well if this doesn't work why don't u try installing xipmsg... u want an ip messenger right?

---

