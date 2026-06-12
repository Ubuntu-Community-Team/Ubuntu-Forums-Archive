---
title: "gtk+-2.0"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by chasebadkdis on 2008-04-17
Hey guys, trying to installl airpwn, Im running the configure file and then I run into this error... what do I need to do?  I tried to install GTK but I think thats what I needed to do?

> checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.



Thanks everyone!

---

### Post by Oldsoldier2003 on 2008-04-17
> **chasebadkdis said:**
> Hey guys, trying to installl airpwn, Im running the configure file and then I run into this error... what do I need to do?  I tried to install GTK but I think thats what I needed to do?



Thanks everyone!

you need libgtk2.0-dev

---

### Post by chasebadkdis on 2008-04-17
okay thank you, im installing it right now, just install that through synaptic manager and i should be good to go?

---

### Post by chasebadkdis on 2008-04-17
okay, installed the package, ran configure again, worked, then when I try to run "make"

> /usr/include/linux/wireless.h:660: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:687: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:698: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:714: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:727: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:754: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:844: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:852: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:861: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:873: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:896: error: &#8216;IFNAMSIZ&#8217; undeclared here (not in a function)
/usr/include/linux/wireless.h:911: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:955: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1059: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1077: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
callbacks.c: In function &#8216;fillDeviceList&#8217;:
callbacks.c:121: error: storage size of &#8216;ir&#8217; isn&#8217;t known
callbacks.c:129: error: &#8216;IFF_LOOPBACK&#8217; undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[1]: *** [callbacks.o] Error 1
make[1]: Leaving directory `/home/krischase/Desktop/airsnort-0.2.7e/src'
make: *** [install-recursive] Error 1



helppp?

---

### Post by chasebadkdis on 2008-04-18
I sitll havent figured out a solution, any help would be greatly aprpeciated!

---

### Post by chasebadkdis on 2008-04-18
Can I get a single response? I undesrtand it takes time, but its been 21 hours since a reply and my posts already down a buncha pages...

---

### Post by Bachstelze on 2008-04-18
What you provided might not be enough to find out what the problem is. Please paste *all* the error messages.

---

### Post by chasebadkdis on 2008-04-18
okay, so this is what I do first, and then it prints out the following
> krischase@krischase-laptop:~/Desktop/airsnort-0.2.7e$ sudo ./configure
[sudo] password for krischase: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking PACKAGE_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


Then I do the make command

> krischase@krischase-laptop:~/Desktop/airsnort-0.2.7e$ make
make  all-recursive
make[1]: Entering directory `/home/krischase/Desktop/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/home/krischase/Desktop/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
	then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:660: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:687: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:698: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:714: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:727: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:754: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:844: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:852: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:861: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:873: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:896: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:911: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:955: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1059: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1077: error: expected specifier-qualifier-list before ‘__u16’
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
callbacks.c: At top level:
callbacks.c:922: fatal error: opening dependency file .deps/callbacks.Tpo: Permission denied
compilation terminated.
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/krischase/Desktop/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/krischase/Desktop/airsnort-0.2.7e'
make: *** [all] Error 2
krischase@krischase-laptop:~/Desktop/airsnort-0.2.7e$ 


---

### Post by chasebadkdis on 2008-04-18
this is what happens if i type sudo make

> krischase@krischase-laptop:~/Desktop/airsnort-0.2.7e$ sudo make
make  all-recursive
make[1]: Entering directory `/home/krischase/Desktop/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/home/krischase/Desktop/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
	then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:660: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:687: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:698: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:714: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:727: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:754: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:844: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:852: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:861: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:873: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:896: error: &#8216;IFNAMSIZ&#8217; undeclared here (not in a function)
/usr/include/linux/wireless.h:911: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:955: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1059: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1077: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
callbacks.c: In function &#8216;fillDeviceList&#8217;:
callbacks.c:121: error: storage size of &#8216;ir&#8217; isn&#8217;t known
callbacks.c:129: error: &#8216;IFF_LOOPBACK&#8217; undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/krischase/Desktop/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/krischase/Desktop/airsnort-0.2.7e'
make: *** [all] Error 2
krischase@krischase-laptop:~/Desktop/airsnort-0.2.7e$ 


---

### Post by Bachstelze on 2008-04-18
You should **not** do *sudo ./configure*. Delete your extracted source directory and try again without sudo.

---

### Post by chasebadkdis on 2008-04-18
oh really? I thought you were supposed to always sudo it....  how would I go about deleting it?

---

### Post by ad_267 on 2008-04-18
If you still have the archive then just delete all the extracted files and extract it again.

---

### Post by Bachstelze on 2008-04-18
Something like

```
rm -rf Desktop/airsnort-0.2.7e
```

And **watch out for typos!**

---

### Post by chasebadkdis on 2008-04-19
I tried

rm -rf Desktop/airsnort-0.2.7e

didnt do anything, just skipped a line..

tried rm -rf Desktop/airsnort-0.2.7e

didnt do anything

then I just type -rf Desktop/airsnort-0.2.7e and it says comamnd not recognized

---

### Post by ad_267 on 2008-04-19
Are you in your home directory? Try:
```

rm -rf ~/Desktop/airsnort-0.2.7e

```

The command rm means remove and the option r means remove recursively, so it removes the directory specified and any subdirectories and files. The f option means force.
You can just use the file manager to delete directories and extract archives if you don't feel comfortable with the command line yet.

---

### Post by chasebadkdis on 2008-04-19
okay, so i was able to succesfully remove it liek you said, but then I ran ./configure , without sudo, finished, ran make and got the same errors as before...

---

### Post by FrozenFox on 2008-04-19
The error is probably in the code itself or it has a problem with the newer versions of compilation tools, not your setup. I can't make heads or tails of it, and it doesn't compile (same errors) on Arch Linux either, codename "Don't Panic", with the same callbacks.c issues. You should probably contact the author.

---

