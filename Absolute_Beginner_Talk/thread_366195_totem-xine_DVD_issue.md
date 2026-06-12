---
title: "totem-xine DVD issue"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Rafael, Jr. on 2007-02-20
Hi everyone,
I have the libcss libdvdread and all codecs but everytime I try to play a movie the program just crashes.  Same thing with gxine and mplayer.
Could someone take a look at the following output from my console?
after on totem I click movie -> play <dvd title> I get:

libdvdnav: Using dvdnav version 1.1.2 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/will/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 

*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:356 ***
*** for dsi->dsi_gi.zero1 == 0 ***

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Thank you to any one who can help me.

---

### Post by ashmew2 on 2007-02-20
I think totem is the worst player in Ubuntu....if u want to get vlc , completely remove totem (use the  synaptic package manager and search for movie player) then goto a terminal and type :

```
sudo apt-get install vlc
```

or you could also get amarok

```
sudo apt-get install amarok

```

---

### Post by Rafael, Jr. on 2007-02-21
Thanks for the help.  I couldn't get VLC to work but MPlayer did with the x11 driver.

---

