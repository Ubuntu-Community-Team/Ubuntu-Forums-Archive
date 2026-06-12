---
title: "No sound..."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by painejake on 2007-12-03
Hi i installed Ubuntu 7.10 recently on my Dell Inspiron 1520 and i cant get my sound working. Im very new to Linux (First used it yesterday) and could someone please help me with this problem as i cant listen to my music :( I have tried a few things but it just doesn't seem to work.

Thanks for any help
Jay:confused:

---

### Post by ferdostar on 2007-12-03
Post the output of ```
sudo lshw -C sound
```

---

### Post by linux23dragon on 2007-12-04
Hi 

Hopefully you have installed Gutsy 32bit (not the 64bit version).  You can get your sound card working by running this command in the terminal.

```
sudo apt-get install linux-backports-modules-generic
```Then reboot.

Please read the last post (post No.#83) of this [***_[COLOR="Blue"]thread[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=530374&highlight=dell+1520") .

Then have a look at [***_[COLOR="Blue"]How_to_get_Mouse_over_preview_of_MP3_files_working[/COLOR]_***]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working"), from the Gutsy Wiki.  Also the Gutsy WiKi is a good source of information on any other matters that may be of interest.

---

