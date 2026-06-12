---
title: "how do u fix this problem???"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-20
I've could've sworn i saw a fix here on the board but i can't find it now

(Reading database ... 154688 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@ubuntu:~$

---

### Post by dvarsam on 2006-06-21
Dear "lime4x4", 

By providing the following:

[QUOTE=lime4x4]
(Reading database ... 154688 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]

Sorry, but I have _no_ clue what you are trying to do here...

> I am _NOT_ a mind reader & therefore I can not help you...

NOT even your Subject is descriptive on this Thread, or what you want/looking help with!!!
(e.g. "how do I fix this problem???")

If you are _really_ looking for help, try to be descriptive with your problem!

Thanks.

---

### Post by Gustav on 2006-06-21
I think he tries to install libmjpegtools0, the command is probably 'sudo apt-get install libmjpegtools0'.

@lime4x4: are you using breezy or dapper?

---

### Post by Gustav on 2006-06-21
The package libmjpegtools0 only exist in breezy and earlier but it seems as you have the package libmjpegtools0c2a installed which only exist in dapper or later.

---

### Post by BoyOfDestiny on 2006-06-21
[QUOTE=lime4x4]I've could've sworn i saw a fix here on the board but i can't find it now

(Reading database ... 154688 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@ubuntu:~$[/QUOTE]

well you can try 

to force it:
sudo apt-get install -f libmjpegtools0c2a

or 

remove the conflicting package, not so sure about what the old one is called...
sudo dpkg -r libmjpegutils0 

For the 2 above options, I think you'd still see the old one in synaptic. Just remove it, then select the new one for install...

Last resort:
manually remove the file it conflicts with (this will move it to the trashcan, so you can just copy it back if need be:

sudo mv /usr/lib/libmjpegutils-1.8.so.0.0.0 ~/.Trash



Hope this helps

---

### Post by glotz on 2006-06-21
[QUOTE=BoyOfDestiny]
Last resort:
manually remove the file it conflicts with (this will move it to the trashcan, so you can just copy it back if need be:[/QUOTE]
Unless if you forget about it and empty your trash in the meanwhile!

ps. the two guys from Andromeda rock on! :D

---

### Post by lime4x4 on 2006-06-21
Sorry got that error when running sudo aptitude upgrade. I tracked it down to mjpegtools. Ended up removing mjpegtools then compiling mjpegtools from source and installing it that way

---

