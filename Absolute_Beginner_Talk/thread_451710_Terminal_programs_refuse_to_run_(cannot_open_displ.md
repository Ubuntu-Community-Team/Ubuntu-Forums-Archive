---
title: "Terminal programs refuse to run (cannot open display)"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by kukuku on 2007-05-22
Hi.

On my second day of discoveries with Ubuntu, I've managed to get the gnome-terminal refusing to run. It just loads for a bit and then vanishes. Same thing happens with another terminal I found from supported Ubuntu applications (terminal emulator? or whatever it was). Then I went Ctrl-Alt-F1 and tried to run gnome-terminal, which resulted in the following error...

(gnome-terminal:6034): Gtk-WARNING **: cannot open display

After searching around a bit I came across a bit of information stating that this is because of the way I'm logged in as root -- but without access to the root directory. Possibly su - would help, but is this applicable inside gnome too? I'm more or less out of ideas what to do about it, and it's a quite nasty limitation to using gnome...

---

### Post by kukuku on 2007-05-22
Might anyone know if this is indeed connected to the root login or not?

---

### Post by kukuku on 2007-05-22
Trying random programs, Konsole booted up. I tried gnome-terminal in it and it came out with...

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Using gnome-terminal --sync only the serial 105 error code changes to serial 136 error code. I'm most interested in finding out if I caused this and how I can avoid causing it to happen again in the future. The last thing I did before the gnome-terminal started to complain was to add a "sudo nvidia-settings" command to the panel, which didn't work out too well (I found out about gksudo afterwards). Before that I installed the restricted Nvidia drivers. The last command I successfully ran from gnome-terminal was sudo nvidia-settings.

---

### Post by rusty0101 on 2007-06-05
> **kukuku said:**
> Trying random programs, Konsole booted up. I tried gnome-terminal in it and it came out with...

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Using gnome-terminal --sync only the serial 105 error code changes to serial 136 error code. I'm most interested in finding out if I caused this and how I can avoid causing it to happen again in the future. The last thing I did before the gnome-terminal started to complain was to add a "sudo nvidia-settings" command to the panel, which didn't work out too well (I found out about gksudo afterwards). Before that I installed the restricted Nvidia drivers. The last command I successfully ran from gnome-terminal was sudo nvidia-settings.

Running into the same sort of problems. I don't know what command I last ran under gnome-terminal however.

---

### Post by rusty0101 on 2007-06-07
For me, following the disable extensions tip as a workaround in bug [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232) got me at least to having a working gnome-terminal. Apparently there is a bug in nvidia or nvidia-glx that shows up if you have multiple monitors and enable xinerama. disableing extensions works around the bug, but then you lose the desktop effects (which haven't worked on this machine anyway, so no great loss to me.)

-Rusty

---

