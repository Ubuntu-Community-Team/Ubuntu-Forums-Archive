---
title: "Deamon tools look alike?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-03-23
Just wondering if there exsist any program for ubuntu that i can mount image files (.cue, .img and so on) like the program Deamon tools used in windows?

---

### Post by %hMa@?b&lt;C on 2007-03-23
> **U5tabil said:**
> Just wondering if there exsist any program for ubuntu that i can mount image files (.cue, .img and so on) like the program Deamon tools used in windows?

mount /path/to/iso/file -o loop /path/to/folder/for/mounting

---

### Post by U5tabil on 2007-03-23
> **jeffc313 said:**
> mount /path/to/iso/file -o loop /path/to/folder/for/mounting

ok now im on to something. but im getting an error:

mount: you must specify the filesystem type

i typed: sudo mount /place/where/the/image/is/image.cue -o loop /where/i/want/to/mount

---

### Post by DeadAmaranth on 2007-03-25
I use this little feature all the time. Can't believe I had to use a 3rd-party program to do it in XP. :) 

Once I learn how to write scripts well enough, I'll make one for it.



I'm guessing you need to try the command with an .iso file. Do you have an .iso file for the object you wish to mount?

---

### Post by kinematic on 2007-03-25
the actual command is
```
mount -o loop -t iso9660 /path/to/.iso /path/to/directory/for/mounting
```
at least that's what i got from a google search.

---

### Post by scxtt on 2007-03-25
> **U5tabil said:**
> i typed: sudo mount /place/where/the/image/is/**image.cue** -o loop /where/i/want/to/mounti don't know that mount will do that w/ bin/cue files ...

---

### Post by ramzai on 2007-03-25
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

