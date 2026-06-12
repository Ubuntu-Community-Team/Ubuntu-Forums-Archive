---
title: "Feisty: &quot;Session only lasted less than 10 seconds&quot; error"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by obscenic on 2007-06-26
I've had feisty up and running smoothly for a couple of weeks, and the only recent change I've made was installing gnomebaker as far as I can recall.  Just before the first time this happened, I was in a state where no gnome apps would start up and the system locked during reboot and I was forced to do a hard resart.

Now I get the "Your session only lasted less than 10 seconds" error after logging into gnome.

my .xsession-errors file reads something like this:

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mark"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 128: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 129: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 147: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
gnome-terminal: error while loading shared libraries: libutil.so.1: cannot dynamically load executable


I've tried the forum suggestions such as re-chowning the .ICEauthority file, renaming the Xsession file, checked the hard drive space (18gb free), all to no avail. I'm totally lost.  Any help would be greatly appreciated.

Should add that I seem to get similar messages when logging into tty1: -bash: /dev/null: Permission denied" in a seemingly endless loop...

---

