---
title: "How do I run a shell script?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-14
Here is what the screen looks like..

---

### Post by taurus on 2006-10-14
Open a terminal, Applications -> Accessories -> Terminal, change directory where the script it, make sure the permission is set, and run it as

```

cd <wherever the script is>
chmod 755 <filename>
./<filename>

```

---

### Post by chirayu on 2006-10-14
Open the terminal window, browse to the file install-sh and in that directory just do 

```
sh install-sh
```

Hope that helps as well, shorter step than one above :P

---

### Post by Stomstedt on 2006-10-14
owner@owner-desktop:~$ ls
argument   Desktop   ircd-hybrid-7.2.2  zachruhl1.html
argument~  Examples  TeamSpeak2RC2
owner@owner-desktop:~$ cd ircd-hybrid-7.2.2
owner@owner-desktop:~/ircd-hybrid-7.2.2$ chmod 755 install-sh
owner@owner-desktop:~/ircd-hybrid-7.2.2$ ./install-sh
install:        no input file specified
owner@owner-desktop:~/ircd-hybrid-7.2.2$

?? :(

---

### Post by taurus on 2006-10-14
> **Stomstedt said:**
> owner@owner-desktop:~$ ls
argument   Desktop   ircd-hybrid-7.2.2  zachruhl1.html
argument~  Examples  TeamSpeak2RC2
owner@owner-desktop:~$ cd ircd-hybrid-7.2.2
owner@owner-desktop:~/ircd-hybrid-7.2.2$ chmod 755 install-sh
owner@owner-desktop:~/ircd-hybrid-7.2.2$ ./install-sh
install:        no input file specified
owner@owner-desktop:~/ircd-hybrid-7.2.2$

?? :(

Is there a README or INSTALL in ~/ircd-hybrid-7.2.2?

```
ls -la ~/ircd-hybrid-7.2.2
```

---

### Post by Stomstedt on 2006-10-14
There is both.. I'll Copy and paste:

README.FIRST

If you don't read this first, we won't help you.
:-)

******************************* IMPORTANT *************************************

  ************ Note for those who don't bother reading docs ***************
  * - Reading INSTALL is now a must, as the old DPATH is now specified    *
  *   when configure is run.                                              *
  *   You now need to ./configure --prefix="/path/to/install/it"          *
  * - The old config format WILL NOT WORK. Please see etc/example.conf ! *
  * - The old kline, dline, xline, gline format WILL NOT WORK.
  *************************************************************************

  ALSO, IF YOU ARE UPGRADING YOUR CURRENT SOURCE TREE, AND YOU TRY TO BUILD
  IN IT WITHOUT PERFORMING AT LEAST 'make clean', THINGS _WILL_ BREAK. IT IS
  RECOMMENDED THAT YOU RUN 'make distclean' AND THEN RERUN './configure'!

******************************* REQUIREMENTS **********************************

Necessary Requirements:

- A supported platform (look below)

- A working dynamic load library, unless
  compiling statically, without module
  support.

Feature Specific Requirements:

- For the SSL Challenge controlled OPER feature and encrypted server links,
  a working OpenSSL library

- For compressed server links,
  a working zlib library and includes (zlib.h)

- For encrypted oper and (optional) server passwords, a working DES and/or
  MD5 library

*******************************************************************************

- See the INSTALL document for info on configuring and compiling
  ircd-hybrid.

- Please read doc/index.txt to get an overview of the current documentation.

- A good place for general help, discussions, and suggestions for ircd-hybrid
  can be found at [http://www.forum.ircd-hybrid.org](http://www.forum.ircd-hybrid.org)

- There is also a mailing list for general discussion of Hybrid.  To subscribe
  to the Hybrid List, use this link:
  [https://lists.ircd-hybrid.org/mailman/listinfo/hybrid](https://lists.ircd-hybrid.org/mailman/listinfo/hybrid)

- To report bugs in hybrid, send the bug report to [email]bugs@ircd-hybrid.org[/email]

- Known bugs are listed in the BUGS file

- If you run in to a problem you think may be specific to your platform,
  check README.PLATFORMS for some hints.

- SOLARIS USERS: this code appears to tickle a bug in older gcc and 
  egcs ONLY on 64-bit Solaris7.  gcc-2.95 and SunPro C on 64bit should
  work fine, and any gcc or SunPro compiled on 32bit.

- DARWIN AND MACOS X USERS: You must be using at least the December 2001
  Development Tools from Apple to build ircd-hybrid with shared modules.
  Before then you MUST disable shared modules, as we do not have the proper
  flags for cc(1) prior to that point to produce shared modules.

- TESTED PLATFORMS:  The code has been tested on the following platforms, and
  is known to run properly.
  FreeBSD 3.x/4.x/5.x (gcc only, TenDRA will work but only with the latest
  cvs version from ten15.org)
  Linux glibc 2.2/2.3
  Solaris 2.6/7/8
  Cygwin 1.3.22 (no shared modules yet)
  OpenBSD 2.8-3.2
  HP-UX 11.00-11.22
  IRIX64 6.5.19 (gcc only; MIPSpro is unconfirmed)
  NetBSD 1.4-1.6
  Tru64 UNIX 5.2b (only tested with native cc)

  It probably does not compile on AIX or libc5 Linux.

- Old Hybrid 5/6 configuration files are no longer supported.  All conf
  files will have to be converted to the Hybrid 7 format.

- If you are wondering why config.h no longer exists, it's because most
  things that were once in config.h are now specified in the 'general'
  block of ircd.conf.  Look at example.conf for more information about
  these options. Many, notably syslog support and EFnet tweaks, are now
  configure options (see ./configure --help for details.)

- /etc/resolv.conf must exist for the resolver to work.

- Please read RELNOTES and doc/whats-new.txt for information about what is in
  this release.

- Other files recommended for reading: BUGS, INSTALL

--------------------------------------------------------------------------------
$Id: README.FIRST 33 2005-10-02 20:50:00Z knight $


INSTALL

                            Hybrid INSTALL Document

   $Id: INSTALL 685 2006-06-16 12:22:31Z michael $

   Copyright (c) 1997-2006 IRCD-Hybrid Development Team

     ----------------------------------------------------------------------

   +------------------------------------------------------------------------+
   | Note for those who don't bother reading docs:                          |
   |                                                                        |
   | Reading INSTALL is now a must, as the old DPATH is now specified when  |
   | configure is run.                                                      |
   |                                                                        |
   | - You now need to ./configure --prefix="/path/to/install/it" as a      |
   |   minimum. Try ./configure --help or read this file for more info on   |
   |   the possible options you can pass to configure.                      |
   |                                                                        |
   | - Important: The old config format WILL NOT WORK. Please see point 7!  |
   +------------------------------------------------------------------------+

   ***** EFNET NOTE *****
   You should run ./configure with the option '--enable-efnet' to tweak
   some options to be EFNet based.  You must also use the example.efnet.conf
   instead of example.conf.
   **********************

     ----------------------------------------------------------------------

                                  HOW TO BUILD

   As of hybrid-4, the distribution uses GNU autoconf instead of the old
   Config script. You must run ./configure before you can (sanely) build
   ircd-hybrid.
   
   1.  Read the RELNOTES file to find out about the exciting new features in
       this version. Other good reads are doc/whats-new.txt, BUGS,
       etc/example.conf, and README.FIRST.

       An example.conf for EFnet is in etc/ with the values "approved" as of
       October 12th, 2003 called example.efnet.conf.

   2.  Run the configure script. It will create include/setup.h and the
       Makefiles to match your system. In hybrid-7, the paths are now handled
       with the --prefix option to configure.
       /usr/local/ircd is the default if no prefix is specified.

       ./configure --prefix=/usr/local/ircd

       The script will determine whichever of the following is best for 
       your system, but you may (unsupported) force their usage with 
       undefined results:

          * --enable-kqueue - Use the superior kqueue(2) system call as
            opposed to the default poll(2).  This is currently only available
            on FreeBSD 4.1 or higher.

          * --enable-devpoll - Enable the superior /dev/poll support on
            Solaris.  Linux /dev/poll is broken and will not work with this
            option.

          * --enable-epoll - Enables epoll(4) Signal I/O system.  This is
            currently only available on 2.5.44 Linux kernel versions or
            later.

          * --enable-rtsigio - Enable the superior Linux RealTime Signal I/O
            system.  This is currently only available on 2.4 Linux kernel
            versions or later.

	  * --enable-poll - Use POSIX poll(2).

	  * --enable-select - Use POSIX select(2).

          * --enable-clobber - Don't preserve the old binaries on make install

	  Incidentally, the order of listing above is the order of auto-
	  detection in configure.  So if you do have kqueue but wish to
	  enable select(2) instead (bad idea), you must use --enable-select.

          * --enable-openssl - Enable the openssl dependent crypto functions.
            This will allow CHALLENGE to work and encrypted links. On systems
            where the configure script can automatically detect OpenSSL, this
            option is not necessary.  If configure cannot find OpenSSL, you
            must specify a path with this option
            (--enable-openssl=/path/to/openssl)

       These are optional or have default values that may be overridden:
   
          * --disable-shared-modules - Disable module support.  This option is
            more secure, but reduces a lot of the flexibility in hybrid-7.
            This may need to be used on some systems without a working
            dlopen/dlsym.

          * --enable-assert - Enable use of numerous debugging checks.  This
            should not be used on any production servers for maximum speed
	    so as to prevent cores from things that shouldn't normally happen.

	  * --enable-efence - Enable ElectricFence which is a memory debugger.

	  * --enable-profile - Enable profiling support in ircd-hybrid.

	  * --disable-block-alloc - Disable block allocations (only works with
            ElectricFence).

	  * --enable-halfops - Enable halfops (%, mode +h) usage. Halfops
	    are similar to plain ops, but can't kick/deop plain ops. Halfops
	    may or may not kick/deop other halfops depending on if (+p) is
	    set. Halfops may not set (+/-p).

          * --enable-small-net - Tunes the server for smaller networks by
            reducing the startup memory footprint. This should really only be
            used for *small* networks, as this tends to be a performance hit
            on larger networks.

	  * --enable-syslog=kill/squit/connect/users/oper, separated by
	    spaces, in quotes - Enables syslog logging, with events you specify
	    (none is okay too, and logs the most essential messages only.)

	  * --enable-syslog-facility=FACILITY - Check with your sysadmin to see
	    what this should be; by default it is LOG_LOCAL4. If you get it wrong
	    initially, no problem; just edit the value in include/setup.h.

          * --with-nicklen,
	    --with-topiclen - Respectively, sets the maximum NICK length and
	    maximum TOPIC length. Note that this must be consistent across your
	    entire network. Defaults are 9 and 120, respectively.

	  * --disable-zlib - Build the ircd without ziplinks support.

	  * --disable-gline-voting - This is good for small networks or where
	    G-Line voting is not necessary. Please understand that by disabling
	    this, it will allow any operator with G-Line permissions to G-Line
	    someone without requiring the approval of 2 other operators. However,
	    it is useful if you use proxy scanners or services that do G-Lines. 

   3.  Run 'make'; this should build the ircd.

   4.  Run 'make install'; this will install the server, modules(1), and tools
       in the path with the prefix specified when configure was ran.

           (1) Unless the server was compiled without module support.

   5.  If you wish to install the contrib modules, run 'make install' in the
       contrib/ folder to compile and install the modules and help pages.

   6.  If you wish to enable the user log, oper log, and failed oper log,
       kill log, kline log and the gline log issue these commands at the
       shell prompt (in the prefix directory).

       $ touch logs/userlog
       $ touch logs/operlog
       $ touch logs/foperlog
       $ touch logs/kill
       $ touch logs/kline
       $ touch logs/gline

       Note: If you use different names in ircd.conf, you must 'touch'
             their specific names.

   7.  If you are upgrading from Hybrid 5 or Hybrid 6, the config files
       have changed drastically...

       By default, the kline file is named kline.conf, the dline file is 
       named dline.conf, the xline file is called xline.conf, and the gline 
       file is called gline.conf.

       The nick resv file is named nresv.conf, channel resv file is named
       cresv.conf.

       The oper motd file is named opers.motd.

     ----------------------------------------------------------------------

                                HOW TO GET HELP

   - Send Check or Money Order to... just kidding! You're on your own for
     support. Try asking other ircd-hybrid admins on EFnet if you can't 
     fix it yourself. If you do fix anything, however, please send context
     or unified diffs to [email]bugs@ircd-hybrid.org[/email] so the fixes can be 
     incorporated into the next release of ircd-hybrid. If hybrid crashes
     on you, PLEASE contact [email]bugs@ircd-hybrid.org[/email] ASAP with a backtrace of
     the core. The Hybrid team can't fix bugs if no one tells us about them!

   - [http://forum.ircd-hybrid.org/](http://forum.ircd-hybrid.org/)
     We decided to create a phpBB-like forum about ircd-hybrid, where you
     can get help from coders and admins, post your suggestions, modules etc.

   - [https://lists.ircd-hybrid.org/mailman/listinfo/hybrid](https://lists.ircd-hybrid.org/mailman/listinfo/hybrid)
     Here you can subscribe to a mailing list for general discussion of Hybrid.

     ----------------------------------------------------------------------

                                     NOTES

   The best way to get a backtrace of the core is to follow this sequence of
   instructions:

   1.  Change to the directory containing the core file

   2.  Run gdb on the binary and the core file.  With an unmodified Hybrid-7.2
       installation, an example command line is below (in the /usr/local/ircd
       directory)

       $ gdb bin/ircd ircd.core


   3.  At the "(gdb)" prompt, enter the command "bt full"

   4.  Save the output of the backtrace command and send it to
       [email]bugs@ircd-hybrid.org[/email].

   5.  Be sure to save the ircd binary, the modules, and the core file in a
       safe place in case the developers need to look deeper than a backtrace
       provides.


Thanks.

---

### Post by taurus on 2006-10-14
If you look at the INSTALL, it says that you need to build it before you can install it.  Therefore, here is what you need to do.

```

sudo aptitude update
sudo aptitude install build-essential (so you can build your app from source...)
./configure
make
sudo make checkinstall

```

---

### Post by Stomstedt on 2006-10-14
in the README.FIRST it says something about an OpenSSL what is that?  Do I need to get that as well?  And now that my server is built how do I run it? :D Thanks..

---

### Post by Stomstedt on 2006-10-14
Compiling ircd-hybrid 7.2.2

Installing into: /usr/local/ircd
Ziplinks ................ no
OpenSSL ................. no
Modules ................. shared
IPv6 support ............ yes
Net I/O implementation .. epoll
EFnet server ............ no (use example.conf)
Halfops support ......... no
Small network ........... no
G-Line voting ........... yes

Configured limits:
NICKLEN ................. 9
TOPICLEN ................ 160

owner@owner-desktop:~/ircd-hybrid-7.2.2$

---

### Post by invalid on 2007-03-20
This is a late follow up, but it may be helpful for others.

This package is available in the universe repos, so there isn't a need to compile it yourself unless you need specific build options.

---

