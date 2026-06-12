---
title: "No sound and bad resolution in VMware ubuntu"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by madHatterCutsTheChatter on 2006-12-15
Help, im v. new to Linux and VMware. 

I can't install my sound card on Ubuntu 6.06.(Runs on winXP host ; VMware Server(latest version) )

My volume icon shows a cross and when  i double-click on it; it shows that i dont have GStreamer pluggins or the sound card isnt installed. How can i fix this?

Also, my resolution wont go beyond 1024*768. All applications appear enormous.

Help!!:( :(

---

### Post by Bachstelze on 2006-12-15
You need to install VMWare tools to use high resolutions in vmware (that will innstall the vmware graphics driver).

---

### Post by madHatterCutsTheChatter on 2006-12-27
Thanx, i fixed the resolution prob. but i still dunno how 2 go abt the sound card prob.:(

---

### Post by puccaso on 2007-01-14
doesnt work
tried to do aoss vmplayer
and nothing

then tried esddsp (the old way)
and this happend

```
mahir@jt-laptop:~/Documents/Downloads/jan2007/MCE2005OEM$ esddsp vmplayer WindowsXPPro.vmx
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(vmplayer:11183): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```

---

