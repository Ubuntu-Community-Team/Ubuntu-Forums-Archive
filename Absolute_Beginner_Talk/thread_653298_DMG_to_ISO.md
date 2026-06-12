---
title: "DMG to ISO"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by SympliG0th on 2007-12-29
I have a DMG file that I know is valid and real. 
I've tried dmg2iso but the pearl script was written in windows so I had to mod it.

When I run the script it tries to use the zlib of pearl and it's looking in usr/local/bin for pearl even though pearl is sitting in usr/bin. Changed the first line of the script to tell it where pearl was but it's still looking in the same place.

Any suggestions?

---

### Post by adam.tropics on 2007-12-29
Could always just put a symbolic link in /usr/local/bin.

```
sudo ln -s /usr/bin/perl /usr/local/bin/perl
```

---

### Post by SympliG0th on 2007-12-29
tried that as well. still not linking correctly :(

---

### Post by adam.tropics on 2007-12-29
Not sure then, although, looking at your first post, you did spell perl....not pearl in your script?

---

### Post by taurus on 2007-12-29
What does the first line of your program look like?

---

### Post by SympliG0th on 2007-12-29
#!/usr/bin/perl
#
# dmg2iso - dmg to iso convert tool

# Copyright (C) 2004 vu1tur <to@vu1tur.eu.org>

---

### Post by SympliG0th on 2007-12-30
Any other suggestions because I need to know if I can get this to work before I fully convert to Ubuntu.

---

### Post by SympliG0th on 2007-12-31
Well I found out what the error was, it couldn't find a perl module that was required. Wish it would have just said that instead of the round about errors. Wish there was a list of the ones needed to. 

Fixed that but now it's still telling me that the file is invalid when I know it is O.o

---

### Post by shad0w_walker on 2008-01-01
Try AcetoneISO2, just came across the tool from this post:  

[http://ubuntuforums.org/showpost.php?p=4050221&postcount=2](http://ubuntuforums.org/showpost.php?p=4050221&postcount=2)

And noticed that when i looked in the utilities menu it has a convert macos image option.

---

