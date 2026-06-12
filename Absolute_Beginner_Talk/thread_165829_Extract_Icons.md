---
title: "Extract Icons?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by iluminate on 2006-04-25
Greetings,

Does anyone know if it possible to extract icons for Windows called .icl ( Icon Extractor)?
I know there are tools to extract them for windows but I can not find anything for Linux.

---

### Post by jazzmuzik on 2006-04-25
I searched as well and didn't find a converter for Linux. Lots of people are looking. I read that icl files can be renamed to dll as they are the same thing. I tried to open icl files with Gimp, gqview, gthumb and ImageMagick and nada. I think you will need to use a Windows icon extractor to convert then to bmp or tiff and then in Linux convert them to png files. Once you get all your bmp (or tiff) files, here is a batch command-line converter, assuming you have ImageMagick installed:

for i in *.bmp; do convert "$i" "$i.png"; done

---

### Post by iluminate on 2006-04-25
Greetings friend,

I have Vmware installed with M$ on the pjuter but I will try to find a solution to extract those icons on Ubuntu :)
What I have found is a util called icoutils, and by using "wrestool" I can extract binaries. [http://www.planetpenguin.de/manpage-1-wrestool.html](http://www.planetpenguin.de/manpage-1-wrestool.html)
But from here I have reached a dead end. Maybe I have to start that darn M$ after all :(

Peace

---

### Post by iluminate on 2006-04-25
:D
Weeee did not have to start that m$. I am sooooo happy now :)
I just followed the example found on [http://www.planetpenguin.de/manpage-1-wrestool.html](http://www.planetpenguin.de/manpage-1-wrestool.html)

```
EXAMPLES
List all resources in file `write.exe':

  $ wrestool -l write.exe
  --type=3 --name=1 --lang=1033 [type=icon offset=0x3120 size=752]
  --type=3 --name=2 --lang=1033 [type=icon offset=0x3410 size=304]
  --type=14 --name=1 --lang=1033 [type=group_icon offset=0x3540 size=34]
  --type=16 --name=1 --lang=1033 [type=version offset=0x3564 size=808]

List all (group-) icon resource in file `write.exe':

  $ wrestool -l --type=group_icon write.exe
  --type=14 --name=1 --lang=1033 [type=group_icon offset=0x3540 size=34]

Extract all icons to current directory, naming the destination files `write.exe_T_N.ico':

  $ wrestool -x --output=. -t14 write.exe
  $ ls *.ico
```
And voila, open up the icons with gthumb and convert to PNG !

I forgot to tell that I renamed the .icl file to .dll and instead of typying write.exe as found in the example, I typed the name of the ddl.

---

### Post by jazzmuzik on 2006-04-25
Great!

Are you converting each one manually to png? If so you can still use this command line converter:

for i in *.ico; do convert "$i" "$i.png"; done

---

