---
title: "[SOLVED] Media players not working"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-11-04
Hi

When I open Totem or VLC, or go to e.g. Youtube to see a video, after a short time the application (Totem, VLC, Firefox) goes 'Black and White' and when I close it using the cross in top right corner, I get the message that the application is not responding, with the option to 'Force quit'. Any clues? TIA

---

### Post by Cappy on 2007-11-04
run
```
totem
```
in a terminal and post any output it gives you from the terminal back here.

are you running compiz (wobbly windows)? do videos work without compiz on? System --> Preferences --> Desktop Effects

---

### Post by ubername on 2007-11-05
> **Cappy said:**
> run
```
totem
```
in a terminal and post any output it gives you from the terminal back here.

are you running compiz (wobbly windows)? do videos work without compiz on? System --> Preferences --> Desktop Effects

Thanks, here is the output

xxxx@xxxx:~$ totem

(totem:6278): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/john/.recently-used.xbel', but the parser failed: Error reading file '/home/john/.recently-used.xbel': Is a directory.

(totem:6278): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

I am using compiz but on  gutsy, I don't know how to switch it off (I don't have a 'Desktop Effects' command - only 'advanced desktop effects settings'.

The message about 'recently used' being a directory is probably as a result of me stopping the 'recently used' function in 'places' 

TIA

---

