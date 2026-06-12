---
title: "robust image duplicate finder?"
date: 2008-10-18
forum: Art &amp; Design
---

### Post by acracker on 2008-10-18
Hey, I'm looking for a program that can compare all images within a folder and find the duplicates, then automatically delete them based on some rules (image size, dimensions, format, etc...). I found a good program that can do this on Windows ([http://www.keronsoft.com/dupdetector.html](http://www.keronsoft.com/dupdetector.html)) but installing under Wine fails. Is there something similar for Ubuntu?
I've tried the kipi plugin for 'find duplicate images' but I don't want to click through every duplicate and confirm the deletion (there are many images).

Thanks.

---

### Post by Nemo_bis on 2010-01-01
Yes, DupDetector for Windows is very good. 
For Ubuntu/Linux, on the [Find Duplicate Images]("http://ubuntuforums.org/showthread.php?t=341736") thread you can find some suggestions based on fdupes (there's also the GUI version, FSlint, as suggested in [Multiple Image Files]("http://ubuntuforums.org/showpost.php?p=5295897&postcount=2"): I tried it and it's much better than KleanSweeper (which requires KDE and won't let you automatically select for deletion "all files but the newest one" etc. in a group of duplicate). But they all find only identical images. 
On [Good duplicate file scanner]("http://ubuntuforums.org/showpost.php?p=4677848&postcount=11") imgSeek was suggested for images, but even if I select the highest similarity grade I find only false duplicate images.

So, I suggest you [GQview]("http://gqview.sourceforge.net/"), which lets you search duplicates for normal/high/low similarity, is very fast, shows thumbnails and reports almost no false duplicates even in "normal similarity" mode: very efficient (and it's in the repositories). 

I've read also that [VisiPics]("http://www.visipics.info/index.php?title=Download") is a good tool: it's for Windows but works under Wine.

---

