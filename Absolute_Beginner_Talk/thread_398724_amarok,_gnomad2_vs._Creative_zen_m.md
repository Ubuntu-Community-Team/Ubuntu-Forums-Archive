---
title: "amarok, gnomad2 vs. Creative zen m"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by joel1a on 2007-04-01
Ok, just upgraded to ubuntu 6.10 and got libmtp2 installed along with gnomad2 and amarok.  when I plug in my creative zen M the photo editor wants to open it and the players don't see it.  What am I doing wrong?  Or more to the point what didn't I do?

---

### Post by dracomordag on 2007-04-01
did you use [this guide](http://ubuntuforums.org/showthread.php?t=199250)?

i've never gotten any MTP device to work with Amarok (then again, i switched over to Exaile a while ago), but it works perfectly with gnomad2 for me.

---

### Post by joel1a on 2007-04-01
ha ha,  yea I found it not long after I posted...  guess I jumped the gun.  I will try it ASAP thanks.

---

### Post by joel1a on 2007-04-01
All Right I have tried running following the install ([http://ubuntuforums.org/showthread.php?t=199250]("http://ubuntuforums.org/showthread.php?t=199250"))

I can't seem to get it configure...  this is what I get 

 Now type 'make' to build gnomad2 2.8.10,
 and then 'make install' for installation.

joel@joel-desktop:~/gnomad_install/gnomad2-2.8.10$ make
Making all in src
make[1]: Entering directory `/home/joel/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT id3read.o -MD -MP -MF ".deps/id3read.Tpo" -c -o id3read.o id3read.c; \
        then mv -f ".deps/id3read.Tpo" ".deps/id3read.Po"; else rm -f ".deps/id3read.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT gnomad2.o -MD -MP -MF ".deps/gnomad2.Tpo" -c -o gnomad2.o gnomad2.c; \
        then mv -f ".deps/gnomad2.Tpo" ".deps/gnomad2.Po"; else rm -f ".deps/gnomad2.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT prefs.o -MD -MP -MF ".deps/prefs.Tpo" -c -o prefs.o prefs.c; \
        then mv -f ".deps/prefs.Tpo" ".deps/prefs.Po"; else rm -f ".deps/prefs.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT filenaming.o -MD -MP -MF ".deps/filenaming.Tpo" -c -o filenaming.o filenaming.c; \
        then mv -f ".deps/filenaming.Tpo" ".deps/filenaming.Po"; else rm -f ".deps/filenaming.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/joel/gnomad_install/gnomad2-2.8.10/src'
make: *** [all-recursive] Error 1
joel@joel-desktop:~/gnomad_install/gnomad2-2.8.10$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@joel-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ gnomad2 ]
3 -  Version: [ 2.8.10 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad2-2.8.10 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/joel/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/joel/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

I seem to have issues with installing anything on my own.!:confused:   Any help would be appreciated.

Joel

---

### Post by Nakkis on 2007-04-02
The amarok in edgy isn't compiled with mtp support. Fortunately the Amarok on Feisty is.

---

