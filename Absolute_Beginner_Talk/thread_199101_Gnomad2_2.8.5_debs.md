---
title: "Gnomad2 2.8.5 debs?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Brokenrgv on 2006-06-18
anyone seen a deb package of this around somewhere, the repo's dont have it and im still to new to compile properly without a heap of problems if someone could post a link so i could use my new zen vision m i would be forever gratefull :) thanks

---

### Post by mister_p_1998 on 2006-06-18
[QUOTE=Brokenrgv]anyone seen a deb package of this around somewhere, the repo's dont have it and im still to new to compile properly without a heap of problems if someone could post a link so i could use my new zen vision m i would be forever gratefull :) thanks[/QUOTE]

It IS in the REPO's! thats where I got mine!
Are you using Synaptic Package Manager?

---

### Post by Brokenrgv on 2006-06-18
yep maybe ive got the wrong repo's in my list i thought i had them all though, are you talking about version 2.8.5 though? i know the older version is there.

---

### Post by Winblowz on 2006-06-18
I'm using Gnomad2 with my Creative Zen Micro, and I just checked the version in the repo's. It's version 2.8.1. Are you sure you need 2.8.5? Is it a compatibility issue (only 2.8.5 support your player)?

---

### Post by Lord Illidan on 2006-06-18
Try and install it from source. It will be a learning experience, and we **will** help you.

First get this...

```
sudo apt-get install build-essential
```

Download the archive, unzip it, open a terminal, go to the location where you unzipped it.

Type in

```
./configure
```

And post the output here.. ALL of it, please. Don't be put off by errors, that's why we are here.

---

### Post by Brokenrgv on 2006-06-18
yep i need 2.8.5 to support mtp transfers on my player (creative zen vision m)

ok im working my wa through my dependancy's for gnomad2, ive installed greater than version that are required  for gnomad but im stuck 

checking for GN... configure: error: Package requirements (             glib-2.0  gthread-2.0              libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'gtk+-2.0' found

so ive started installed those packages, glib is installed, libnjb installed gtk+- requires, well this is the output

configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

as ive mentioned ive allready instaled glib (vers 2.9) but it doesnt seem to recognise this so im stuck in a circle.

---

### Post by msak007 on 2006-06-18
[QUOTE=Brokenrgv]yep i need 2.8.5 to support mtp transfers on my player (creative zen vision m)

ok im working my wa through my dependancy's for gnomad2, ive installed greater than version that are required  for gnomad but im stuck 

checking for GN... configure: error: Package requirements (             glib-2.0  gthread-2.0              libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'gtk+-2.0' found

so ive started installed those packages, glib is installed, libnjb installed gtk+- requires, well this is the output

configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

as ive mentioned ive allready instaled glib (vers 2.9) but it doesnt seem to recognise this so im stuck in a circle.[/QUOTE]

I've gotten a Creative Zen MicroPhoto working with Gnomad 2.8.5. It requires a little bit more than just that package though. For starters, are you sure you have the gtk2.0 package installed? Open a terminal and type 

```
sudo apt-get install libgtk2.0-dev
```

This will install all the needed above packages, including gtk, glib, atk, pango, and cairo. I don't want to double-post, so [here's]("http://ubuntuforums.org/showthread.php?t=199250") my thread on how I got it working. It's a little long and might be confusing, so if you need any help setting it up let me know. Thanks for mentioning that package, because I couldn't think of all the dependency problems I ran into when trying to write the how-to.

---

### Post by Brokenrgv on 2006-06-19
thanks for sudo apt-get install libgtk2.0-dev, but ive hit a snag this is what appears before it stops
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
dont worry i read your how-to and noticed im missing that pearl package :) so over this atm
just when i thought i was home and hosed :( 
output below
Making all in src
make[1]: Entering directory `/home/simon/Desktop/gnomad2-2.8.5/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o uti l.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadat a.o wmaread.o wavfile.o -pthread -L/usr/local/lib -lgthread-2.0 -lnjb -lusb -lgt k-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontco nfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -l cairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/loca l/lib -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/simon/Desktop/gnomad2-2.8.5/src/juke box.c:1873: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libgtk-x11-2.0.so: undefined r eference to `g_intern_static_string'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libpango-1.0.so: undefined ref erence to `g_slice_free_chain_with_offset'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libpangocairo-1.0.so: undefine d reference to `g_slice_alloc'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libpangocairo-1.0.so: undefine d reference to `g_slice_alloc0'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libpangocairo-1.0.so: undefine d reference to `g_slice_free1'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/simon/Desktop/gnomad2-2.8.5/src'
make: *** [all-recursive] Error 1

---

### Post by msak007 on 2006-06-19
I'm not really sure how to help you there. You may not have all the dependencies needed. Just for reference, this is from Gnomad's site:

Requirements


Gnomad needs:

    * libnjb (which in turn requires libusb).
    * libid3tag
    * gtk+-2.0 and libgnomeui

Gnomad also optionally integrates with the GNOME desktop if it is found at configure time. You can find the needed libraries in the links below.

Look:

Gnomad +
       |
       +- GTK+-2.0 (incl GDK, GLIB)
       |
       +- libgnomeui
       |
       +- libnjb +
       |         |
       |         +- libusb (optional on *BSD)
       |
       +- libid3tag
       |
       +- GNOME 2.0
	
You've already installed libgtk2.0-dev, and I assume you've already installed build-essential to get all the compilers, right? You may want to install libusb-dev and libid3tag0-dev too because those are needed. If you followed the how-to, then you should already have libnjb and libtmp installed. I really have no idea what the whole "/../../../../" thing in your output is all about. I didn't have any of those lines in my output when I compiled gnomad.

---

### Post by msak007 on 2006-06-19
I'm not really sure how to help you there. You may not have all the dependencies needed. Just for reference, this is from Gnomad's site:

Requirements


Gnomad needs:

    * libnjb (which in turn requires libusb).
    * libid3tag
    * gtk+-2.0 and libgnomeui

Gnomad also optionally integrates with the GNOME desktop if it is found at configure time. You can find the needed libraries in the links below.

Look:

Gnomad +
       |
       +- GTK+-2.0 (incl GDK, GLIB)
       |
       +- libgnomeui
       |
       +- libnjb +
       |         |
       |         +- libusb (optional on *BSD)
       |
       +- libid3tag
       |
       +- GNOME 2.0
	
You've already installed libgtk2.0-dev, and I assume you've already installed build-essential to get all the compilers, right? You may want to install libgnomeui-0, libusb-dev, and libid3tag0-dev too because those are needed. If you followed the how-to, then you should already have libnjb and libtmp installed. I really have no idea what the whole "/../../../../" thing in your output is all about. I didn't have any of those lines in my output when I compiled gnomad.

Edit: sorry for the double-post, my connection must've timed out and it got submitted twice

---

### Post by Brokenrgv on 2006-06-20
sorry for the late "thanks for the reply" been busy, ill keep cracking away at this its obvious im missing dependancy's since im only new to this compiling thing, thanks again for the help, ill keep trying by gees it would be alot easier, though not as educational to have the latest vers as a deb so thats my hope if i cant get it compiled and installed ill just wait.

---

### Post by shakespeare on 2006-06-28
There is an update 2.8.6 of gnomad2 using libmtp 0.0.9 which apparently adds playlist support. However this version has problems with the Creative Zen Vision:M (and maybe some others). Stick with gnomad2 2.8.5 and libmtp 0.0.8

You'll need the following packages:
  gnomad2 2.8.5   from gnomad2.sourceforge.net
  libmtp 0.0.8   from libmtp.sourceforge.net
  libnjb 2.2.5   from libnjb.sourceforge.net
These must be built following the included instructions closely. You'll need a few more packages to accomplish this (in addition to build-essentials):
  libusb-dev   from Ubuntu repositories
  libid3tag0-dev   from Ubuntu repositories
  libgnomeui0-dev   from Ubuntu repositories

---

### Post by ShiftyPowers on 2006-06-29
Shakespeare, what problems are you seeing with the CZV:M with 2.8.6?  I'm running that version at home and things seem to be running fine except for the progress bar not working.

---

### Post by Brokenrgv on 2006-06-29
i agree shiftypowers all fine here except the progress bar

---

### Post by shakespeare on 2006-06-30
[QUOTE=ShiftyPowers]Shakespeare, what problems are you seeing with the CZV:M with 2.8.6?  I'm running that version at home and things seem to be running fine except for the progress bar not working.[/QUOTE]

It recognizes the Zen Vision:M and starts scanning the device. After some seconds (maybe the media scan is completed), it crashes with a segment fault. It has been reported to the developers by another CZV:M user also.

Did you build gnomad2 2.8.6 with libmtp 0.0.9 (as instructed) or with 0.0.8?

---

### Post by msak007 on 2006-06-30
I haven't heard of any reports of Gnomad 2.8.6 / libmtp 0.0.9 causing crashes, still workin with the MicroPhoto. The only bug I've encountered is the one already mentioned - no progress bars.

---

### Post by Brokenrgv on 2006-06-30
same here no crashes stable as :) with ZVM

---

### Post by shakespeare on 2006-06-30
[QUOTE=msak007]I haven't heard of any reports of Gnomad 2.8.6 / libmtp 0.0.9 causing crashes, still workin with the MicroPhoto. The only bug I've encountered is the one already mentioned - no progress bars.[/QUOTE]

OK. I found the problem using gdb: gnomad2 2.8.6 was crashing on the call to get_mtp_filetype_description. Apparently it is necessary to explicitly remove earlier versions of libnjb - just running make install for libnjb 2.2.5 can fail silently if libnjb 2.2.4 from the Ubuntu repositories is already installed.

BTW, the missing progress bars issue is noted in the source code with the comment "it is so fast anyway, so who'd want it?".

---

