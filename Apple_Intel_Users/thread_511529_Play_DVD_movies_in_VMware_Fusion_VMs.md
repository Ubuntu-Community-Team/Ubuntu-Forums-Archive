---
title: "Play DVD movies in VMware Fusion VMs?"
date: 2007-07-27
forum: Apple Intel Users
---

### Post by Mr Humphries on 2007-07-27
[FONT="Times New Roman"]On my Core 2 Duo iMac, DVD movies play fine in Mac OS and Windows thanks to:

1. Reflashing the firmware to make the drive RPC-1 from RPC-2
2. Installing Region X on Mac OS and DVD Region + CSS Free on my Windows Boot Camp partition

The only places so far that I've installed Unices are inside VMware Fusion VMs. After installing all the required packages like libdvdcss2, libdvdnav et cetera, the movies just won't play. The entire contents of each DVD are visible in the file manager though. Has anyone been able to watch DVD movies inside VMs containing GNU/Linux, Solaris, FreeBSD ...?

Thanks for any input.
[/FONT]

---

### Post by benanzo on 2007-07-27
When you attempt to play an encrypted DVD via Xine or MPlayer or totem-gstreamer does it give any error messages indicating the lack of libdvdcss or other codec error?  Or does it give some other error?

My guess, considering you've taken the necessary steps to install the deCSS libraries, is that this could be a problem that is VM-specific.  I've not heard of this before, but it does not seem too unlikely that DVD video playback could be tricky from inside a VM.  Can you paste the specific error you get back here?

---

### Post by Mr Humphries on 2007-07-28
In Ubuntu Ultimate 1.4 x64, errors along the lines of "The disc is encrypted; there don't seem to be codecs to play it." gxine even causes the X server to restart. Other than gxine, I've tried Xine, Totem, VLC, MPlayer, Ogle and Kaffeine. Xine, for example, says:

- xine engine error -
There is no input plugin available to handle 'dvd:/'.
Maybe MRL syntax is wrong or file/stream source doesn't exist.

---

### Post by luisbg on 2007-07-30
Why do you want to run the dvd's in VMware when VLC can do the trick?

luisbg

---

### Post by luisbg on 2007-07-30
oops, just read your error

try installing this packages
libdvdplay0
libdvdread3
lsdvd

probably all are not necessary but better too have too much than too less. Anyway, AFAIK vlc doesn't need this since it uses it's own codecs.

luisbg

---

