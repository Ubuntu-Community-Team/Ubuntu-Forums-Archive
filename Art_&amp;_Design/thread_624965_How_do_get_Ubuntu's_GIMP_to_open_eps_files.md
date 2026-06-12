---
title: "How do get Ubuntu's GIMP to open eps files?"
date: 2007-11-27
forum: Art &amp; Design
---

### Post by madeinbrazil on 2007-11-27
I was able to get Gimp on Windows to open a eps file. Instructions are here:

[http://www.gimptalk.com/forum/topic/Eps-487-1.html](http://www.gimptalk.com/forum/topic/Eps-487-1.html)

Basically it says:
> GIMP is capable of opening EPS files if ghostscript is installed on your system.

# Download Ghostscript from following url for your operating systm.
(download Download gs851w32.exe if using ms-windows)
[http://sourceforge.net/project/showfiles.php?group_id=1897&package_id=1845&release_id=321615](http://sourceforge.net/project/showfiles.php?group_id=1897&package_id=1845&release_id=321615)

# Install it, go to /bin directory of where you installed ghostscript
# copy all exe files (may be 2 or 3 etc) and paste in gimp's roo directory (where gimp is installed)
# restart gimp and try opeing eps, ps, pdf etc files 

But, how do I do this for Ubuntu 7.10? I downloaded the file ghostscript-8.51.tar.gz file from sourceforge and now I'm lost... Yes, I am a Linux newbie, trying to get away from Windows. I've never even used the terminal and plan on staying away from it if at all possible.

Any help?

---

### Post by Paul820 on 2007-11-27
Ghostscript is in the repositories in gutsy
> sudo aptitude install ghostscript

---

### Post by madeinbrazil on 2007-11-27
I have it installed, on Gutsy. But, as the instructions say, the .exe files should be copied and pasted manually into Gimp's folder. But, what would be the equivalents of an ".exe" file?

---

### Post by Paul820 on 2007-11-27
You can't put .exe files into the gimp folder on gutsy or any linux, as those are for windows only. Gimp and any other program on linux does not understand what they are. If you have installed ghostscript from the repos then gimp should automatically open the files for you.

---

### Post by madeinbrazil on 2007-11-27
Yes, I knew exe was for Windows only. Thanks for reminding though, its always nice to have thorough information.

For some reason now it works! :) I guess reinstalling Ghostscrpt did it. I had installed it before but tried it again, thanks a bunch!

One less reason for me to use Windows :guitar:

---

### Post by ookboo on 2008-06-04
Confirmed!  With ghostscript installed, GIMP works like a GHAMP...

---

### Post by Stoneface on 2008-07-09
Well I installed ghostscript as well, but still when I want to open an .eps file I receive the same error:```
Opening '/home/jasper/webdesign/HM/logo logo3.eps' failed: Encapsulated PostScript image plug-In could not open image
```

---

### Post by Stoneface on 2008-07-09
Well apparently it is just one .eps file that does not open. Maybe it is corrupted/damaged. Other .eps files do open.

---

