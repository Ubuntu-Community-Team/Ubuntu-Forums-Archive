---
title: "Updated Kernel, lost wireless, can't boot old kernel"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-02-09
The update manager told me there was a new kernel (28 vs 27), so I clicked update. After installing, I rebooted to the new kernel ( 28, ) and couldn't get on wireless (linksys WUSB54G).

Ok, no problem I thought. I'll just reinstall ndiswrapper. So I did sudo uninstall and uninstalled it as normal. However, when I went back to 'make' and 'make install' it, I just get an error.

> 
agrieser@andrew:~/multimedia/drivers/ndiswrapper-1.28$ sudo make
Password:
make -C driver
make[1]: Entering directory `/home/agrieser/multimedia/drivers/ndiswrapper-1.28/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-686/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/agrieser/multimedia/drivers/ndiswrapper-1.28/driver'
make: *** [all] Error 2



agrieser@andrew:~/multimedia/drivers/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/agrieser/multimedia/drivers/ndiswrapper-1.28/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-686/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/agrieser/multimedia/drivers/ndiswrapper-1.28/driver'
make: *** [install] Error 2


My next thought was, ok I'll just go back to kernel 27 until I get this sorted out. Nope, can't boot to the old kernel. It gets to the part where network interfaces load, and it freezes. I guess because it can't find ndiswrapper (I uninstalled it from the new kernel).

So....whats the next step? Do I need to reinstall the 'make' and 'build' commands? I remember having to do that the first time I installed ndiswrapper.

/bummed

-Andrew

/afterthought
I wish I would have seen the warning about the new kernel on the forums. Not sure if it's related though

---

### Post by po0f on 2007-02-09
Atreus12,

You updated the kernel, but did you also get the headers for the new kernel as well?

---

### Post by Atreus12 on 2007-02-09
I don't really know. I was working on something else, so I just told it to update and let it run on another workspace. It was a 77MB download, and I did all the updates it suggested. Obviously, I haven't been online since getting the new kernel. So if it didn't add them initially, I don't have them

---

### Post by po0f on 2007-02-09
Atreus12,

Can you post ndiswrapper's Makefile?  We can probably edit it to compile a module for the old kernel so you can at least get back online.  If it's >100 lines, just attach it to a new post.

---

### Post by Atreus12 on 2007-02-09
the makefile
> 
DRIVER_VERSION = $(shell sed -n 's/^\#define[ \t]\+DRIVER_VERSION[ \t]\+"\([^"]\+\)"/\1/p' driver/ndiswrapper.h)

UTILS_VERSION = $(shell sed -n 's/^\#define[ \t]\+UTILS_VERSION[ \t]\+"\([^"]\+\)"/\1/p' driver/ndiswrapper.h)

distdir=ndiswrapper-${DRIVER_VERSION}
distarchive=${distdir}.tar.gz

DISTFILES=AUTHORS ChangeLog INSTALL Makefile README ndiswrapper.spec \
				   ndiswrapper.8 loadndisdriver.8
DIST_SUBDIRS=utils driver

DESTDIR = 
mandir = $(DESTDIR)$(shell [ -d /usr/man/man8 ] && echo /usr/man || echo /usr/share/man )

KVERS ?= $(shell uname -r)

.PHONY: all

all: 
	+make -C driver
	+make -C utils

.PHONY: install
install:
	+make -C driver install
	+make -C utils install
	mkdir -p -m 0755 $(mandir)/man8
	install -m 644 ndiswrapper.8 $(mandir)/man8
	install -m 644 loadndisdriver.8 $(mandir)/man8

.PHONY: clean distclean
clean:
	+make -C driver clean
	+make -C utils clean
	rm -f *~
	rm -fr ${distdir} ${distdir}.tar.gz patch-stamp

distclean: clean
	+make -C driver distclean
	+make -C utils distclean
	rm -f .\#*

uninstall:
	@echo "NOTE: Not all installed files are removed, as different" \
		"distributions install ndiswrapper files at different places."
	@echo "Run uninstall as many times as necessary until no" \
		"\"removing\" messages appear below."
	@if [ "x$(shell which loadndisdriver)" != "x" ]; then \
		echo "removing $(shell which loadndisdriver)"; \
		/bin/rm -f $(shell which loadndisdriver); \
	fi
	@if [ "x$(shell which ndiswrapper)" != "x" ]; then \
		echo "removing $(shell which ndiswrapper)"; \
		/bin/rm -f $(shell which ndiswrapper); \
	fi
	@if [ "x$(shell which ndiswrapper-buginfo)" != "x" ]; then \
		echo "removing $(shell which ndiswrapper-buginfo)"; \
		/bin/rm -f $(shell which ndiswrapper-buginfo); \
	fi
	@for module in $(shell find /lib/modules/$(KVERS) \
			-name "ndiswrapper*"); do \
		echo "removing $$module"; \
		/bin/rm -f $$module; \
	done

dist:
	@rm -rf ${distdir}
	mkdir -p ${distdir}
	@for file in $(DISTFILES); do \
	  cp  $$file $(distdir)/$$file; \
	done
	for subdir in $(DIST_SUBDIRS); do \
	  if test "$$subdir" = .; then :; else \
	    test -d $(distdir)/$$subdir \
	    || mkdir $(distdir)/$$subdir \
	    || exit 1; \
	  fi; \
	done
	+make -C driver distdir=../${distdir}/driver dist
	+make -C utils distdir=../${distdir}/utils dist

	# Update version in dist rpm spec file - don't crash if it fails
	-sed -i "s/\%define\s\+ndiswrapper_version\s\+[^\}]\+\}/%define ndiswrapper_version $(DRIVER_VERSION)\}/" $(distdir)/ndiswrapper.spec
	tar cfz ${distarchive} ${distdir}

rpm: dist ndiswrapper.spec
	rpmbuild -ta $(distarchive) --define="ndiswrapper_version $(DRIVER_VERSION)"



edit: I also attached it

---

### Post by Atreus12 on 2007-02-09
A couple of basic understanding questions:

Should I have lost my wireless connection on a kernel update if I am using ndiswrapper? (maybe should is the wrong word)

By default, will all my addons (like make, build...etc) be carried over (or installed) in the new kernel?

Did I do something wrong, or is this something I'm going to have to do every kernel update?

-Andrew

---

### Post by po0f on 2007-02-09
Atreus12,

The following might work, change this line:

```
[FONT="Courier New"]KVERS ?= $(shell uname -r)[/FONT]
```

to this:

```
[FONT="Courier New"]#KVERS ?= $(shell uname -r)
KVERS ?= 2.6.15-27-686[/FONT]
```

We just commented out the old line so we can change it back easier.  If it doesn't work, let me know.

Also, when booting the old kernel, during the boot process you can Ctrl-C right when it gets to the "configuring network interfaces" (or whatever it's called) stage to skip it.

---

### Post by Atreus12 on 2007-02-09
Awesome! It worked.
So what should I do about the 2.6.15-28-686 kernel? I still need to get the kernel headers somehow, can that be done from the 27-686 kernel?

Also, I am interested in the answers to my above question about upgrading the kernel.
Thanks!!
The reason I love Ubuntu is because the support >> all others
-Andrew

---

### Post by po0f on 2007-02-10
Atreus12,

If you haven't already figured it out, you should install the headers for that new kernel like so:

```
[FONT="Courier New"]$ sudo apt-get install linux-headers-2.6.15-28-686[/FONT]
```

When you get the new headers installed and you are ready to build ndiswrapper for it, *don't* uninstall the old one.  It's fine right where it is.  Just change that line we edited to reflect the new kernel version.  The reason we have to do it this way is because we have booted the kernel with the opposite kernel of the version we want to build the module for.  If you build it twice, once with "KVERS ?= 2.6.15-27-686" and another with "KVERS ?= 2.6.15-28-686", you'll have ndiswrapper built for both kernels and you should be good to go.

After you have built the module twice, go ahead and change it back to what that line was originally, "KVERS ?= $(shell uname -r)".

[EDIT]

And to answer your question about the kernel upgrades, yes you are going to have to rebuild ndiswrapper for each upgrade.  It's not so hard though, is it?  ;)

---

### Post by Atreus12 on 2007-02-10
> **po0f said:**
> 
And to answer your question about the kernel upgrades, yes you are going to have to rebuild ndiswrapper for each upgrade.  It's not so hard though, is it?  ;)


No, it's not difficult....now that I understand the process. :)

---

### Post by Dark Cerberus on 2007-02-14
Hi

I have just recompiled my Kernel and found out that I have this exact problem, but I don't quite understand what I am suppose to do. (a little new to Linux)

Is there anyway you could help me with a step by step process of what to do or something like that. 

I use Kernel 2.6.18.2 in case it's relevant, and i checked but I can't seem to find Ndiswrapper's makefile. 

All help is appreciated.
Thanks

---

