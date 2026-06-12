---
title: "Install winefish"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-03-16
I'm totally new at Ubuntu and I've just downloaded Winefish and unpacked it.

I've opened the install-file, but I can't figure out what to do.

"To install Winefish from source
===============================

1) get the required libraries (header files and executable files)

 	* glib-2.0 (version >= 2.2.2)
	* libgtk2 (version >= 2.4.0)
	* libpcre
	* [ aspell ] (pptional; for spell checking)
	* [ grep, find, [ sed, xargs ]] (optional; for grep function)

2) details about `configure'

	$ sh configure --help

   if you wanna use
	--prefix=/home/myhome/apps/
   (or something like that) please take care of options which
   relate to mime type, desktop icons, etc.

   Vietnamese TeX Users:
   	you may use `--with-unikey-gtk' ---
   	if you get troubles with Winefish + Unikey GTK.

3) for the development release (winefish-x.x.x.y),
   please excute `autoconf' to generate `configure' script

	$ autoconf

4) some variables control winefish. See `src/config_spec.h' for details.

5) configure and compile

	$ sh ./configure [your-options]
	$ make

6) reduce filesize

	$ make strip # this requires `strip' program

7) install everything

	$ su
	$ make install
"

I've never tried to install a program before except when I use apt-get install.

Hope there's someone out there who can help me.

---

### Post by cayamara on 2006-03-17
Hi!
You were trying to compile winefish from source. Now you have two options:

**1.** Use a debian package instead:
```
$ wget http://debian.wgdd.de/debian/dists/unstable/main/binary-i386/editors/winefish_1.3.2.5-0dl0_i386.deb
$ sudo dpkg -i winefish_1.3.2.5-0dl0_i386.deb
```

**2.** Try to compile it on your own.
For this, there are some documentations online. I would recommend [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware") from the Ubuntu Wiki to start off with.

If you are new to Linux, I would recommend you to use the .deb (option 1). Later, you can try to compile winefish from source.

---

### Post by sabrina on 2006-03-17
Thank you for the answer.

I've decided to use a debian package, which is working just fine.

---

