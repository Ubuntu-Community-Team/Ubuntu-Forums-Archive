---
title: "CDemu/installing an app. with no auto install/mounting .cue or .bin"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Niomi on 2005-10-29
I'm looking to mount a .cue/.bin file, simular to the way you would mount a .iso.
This looks like it is the program I need and I've downloaded it: [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

However, this will be the first time I've installed something that requires more work than clicking 'next' a lot. The installation intructions sound like greek to me. Is there a page or tutorial that can help explain the process?

> #***************************************************************************
#                        INSTALL  -  description
#                             -------------------
#    copyright            : (C) 2003 by Robert Penz
#    email                : [email]robert.penz@outertech.com[/email]
#***************************************************************************

#***************************************************************************
#*                                                                         *
#*   This program is free software; you can redistribute it and/or modify  *
#*   it under the terms of the GNU General Public License as published by  *
#*   the Free Software Foundation; either version 2 of the License, or     *
#*   (at your option) any later version.                                   *
#*                                                                         *
#***************************************************************************

The install is quite simple, so that currently there is no automatic install.

#*#*#*#*#*#
#*#  1  #*#
extract the archive, what you apparently already did ;-)

#*#*#*#*#*#
#*#  2  #*#
you need the source of your current running kernel.
/lib/modules/`uname -r`/build/include needs to point at it. if you're not sure if it points
to the righ kernel just type: ls -la /lib/modules/`uname -r`/build if its the correct kernel
source all is ok. ;-)

#*#*#*#*#*#
#*#  3  #*#
make

Depending on your config of the gcc, you get non or many warnings, but even if you get
some, only one is in the cdemu module. e.g. on a Suse 8.2 with the suse standard kernel source
extracted to /usr/src/linux/ (/lib/modules/`uname -r`/build/ points to that) it looks this way.

************************************************************
In file included from /usr/src/linux/include/linux/tqueue.h:19,
                 from /usr/src/linux/include/linux/aio.h:4,
                 from /usr/src/linux/include/linux/fs.h:201,
                 from /usr/src/linux/include/linux/capability.h:17,
                 from /usr/src/linux/include/linux/binfmts.h:5,
                 from /usr/src/linux/include/linux/sched.h:10,
                 from cdemu.c:68:
/usr/src/linux/include/asm/system.h: In function `__set_64bit_var':
/usr/src/linux/include/asm/system.h:189: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/src/linux/include/asm/system.h:189: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from cdemu.c:70:
/usr/src/linux/include/linux/file.h: In function `fcheck_files':
/usr/src/linux/include/linux/file.h:37: warning: comparison between signed and unsigned
/usr/src/linux/include/linux/file.h: In function `fcheck':
/usr/src/linux/include/linux/file.h:50: warning: comparison between signed and unsigned
/usr/src/linux/include/linux/file.h: In function `__put_unused_fd':
/usr/src/linux/include/linux/file.h:62: warning: comparison between signed and unsigned
In file included from /usr/src/linux/include/linux/blk.h:4,
                 from cdemu.c:75:
/usr/src/linux/include/linux/blkdev.h: In function `blk_queue_bounce':
/usr/src/linux/include/linux/blkdev.h:212: warning: comparison between signed and unsigned
/usr/src/linux/include/linux/blkdev.h: In function `blk_finished_io':
/usr/src/linux/include/linux/blkdev.h:348: warning: comparison between signed and unsigned
cdemu.c: In function `ce_findtrack':
cdemu.c:241: warning: comparison between signed and unsigned

************************************************************

if you get an error message (not a warning) like

cdemu.c: In function `ce_transfer':
cdemu.c:***: too few arguments to function `do_generic_file_read'

you most likely have a new redhat kernel.

you just need to change one line in the module source

search for this 2 lines
      do_generic_file_read(vc->vc_backing_file, &position,
                &desc, vc_read_actor);

and add a ",0" to the second line
                &desc, vc_read_actor, 0);
  

and as root

#*#*#*#*#*#
#*#  4  #*#
make install

#*#*#*#*#*#
#*#  5  #*#
now we can load the kernel module just with typing

modprobe cdemu

no message should be given by this command

for you Debian users (maybe others), you might have to run `update-modules` first

#*#*#*#*#*#
#*#  6  #*#
after the install you just need to call cdemu to get the help screen of the userspace program

if you're using devfs, then nodes will show up in /dev/cdemu/ automagically.  if you're using
udev, you might want to add this to /etc/udev/rules.d/99cdemu:
KERNEL="cdemu[0-9]*", NAME="cdemu/%n"
otherwise you'll get a bunch of nodes showing up in /dev/ instead of /dev/cdemu/

ps: Any bug reports, comments, feature requests wished.

---

### Post by adamkane on 2006-03-21
See:
[http://www.ubuntuforums.org/showthread.php?t=144236](http://www.ubuntuforums.org/showthread.php?t=144236)

---

### Post by mlind on 2006-03-21
Another ways is to converted .bin .cue images .iso format, using bchunk for
example. It's available via apt-get.

---

