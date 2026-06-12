---
title: "Installing in WINE"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by brdmartin on 2007-01-27
Hello all
Im wanting to see if a complete switch to Linux is a viable thing for me, but there's a few things which I have to figure out how to do first.

One of the main ones is to be able to open the .cr2 files that my digital camera creates. The camera came with a windows program called digital photo professional (the program does very little other then opening .cr2 files actually), which I am trying to install with WINE. I have placed the CD in the CD drive, and then went to the terminal and typed: 
```
wine D:/setup.exe
```
The CD seemed to spin, but I just got another command prompt of the -desktop:~$ variety. When I went into winecfg, it doesn't appear to have a way to install any windows programs.
Of course, if anyone knows of any program in Linux that can open .cr2, that would rock:guitar: 

Any Ideas?:confused:

---

### Post by mrgrapefruit on 2007-01-27
i don't know much about wine as i've never had the need to run a windows program, but 'dcraw' is utility for doing just what you're looking for

> Cant gimp open .cr2 files? Isnt it picture files?

I just had a look and it seems like it does!

---

### Post by aktiwers on 2007-01-27
After installing Wine, did you remember to run: winecfg
from Terminal?

Also, try simply double-clicking on the setup.exe icon in your cdrom drive.
Cant gimp open .cr2 files? Isnt it picture files?

---

### Post by jazzuban on 2007-01-27
Fire up Synaptic Package Manger, and search for dcraw. It will find 3 programs that work with the cr2 raw format: rawstudio, gimp-dcraw and dcraw. Install.

(you may need to enable additional repositories:
in Synaptic, go to Settings, Repositories,
Click to enable all the repos - main, universe, multiverse, restricted.
Close everything, and click "Reload")

---

### Post by brdmartin on 2007-01-27
I remember trying to open .cr2 files in Gimp before, and it didn't work, but mabie it will now, I'll give it a try.

---

### Post by brdmartin on 2007-01-27
So when I try to open the cr2 with GIMP, I get a plethora of error messages, 1292 errors to be exact. Each says Tiff image message (CR2 files are not Tiff files actually) 
1. incorrect count for field "BitsPerSample" (3, expecting 1); tag trimmed
2. Old-style JPEG compression support is not configured
3. Could not get photometric from '/media/EOS_DIGITAL/DCIM/100CANON/IMG_0336.CR2'. Assuming min-is-black. 
4. Too many error messages

The good news though is that I learned that my new flash card reader works automatically in Ubuntu.

Im trying to install the dcraw program, which I guess also let's me open the files directly in GIMP, but being new at this, and not being a computer programmer by profession, this kind of thing makes no since to me "Compile with "gcc -o dcraw -O4 dcraw.c -lm -ljpeg -llcms" or "gcc -o dcraw -O4 dcraw.c -lm -DNO_JPEG -DNO_LCMS". Run with no arguments to see a usage message."

huh???:confused:

---

### Post by brdmartin on 2007-01-27
Alright, installed the dcraw in synaptic, and works pretty well. Opens the files just fine. Thanks everyone

Now I just gotta figure out why they are all coming up pink when I load them, but at least that can be fixed
:D

---

