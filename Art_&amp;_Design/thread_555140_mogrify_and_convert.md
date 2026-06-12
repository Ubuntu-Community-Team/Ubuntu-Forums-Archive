---
title: "mogrify and convert"
date: 2007-09-19
forum: Art &amp; Design
---

### Post by zmkhan on 2007-09-19
I cannot for the love me get mogrify and convert to work for a school assigment. I installed ImageMagick with "apt-get install imagemagick"

Mogrify commands don't do anything, or maybe it's saving to some default directory? Convert gives me a: "Convert: missing an image filename "image.jpg" I'm following the exact usage guidelines given on the ImageMagick page. I'm thinking it may be some path or env settings but I'm just a beginner and have no clue how to set those. Any help would be greatly appreciated, thanks in advance.

---

### Post by yabbadabbadont on 2007-09-19
I have found that following the examples in the ImageMagick help pages only work roughly half the time...  It provides some nice tools, but it seems like only the developers of them know the correct parameter sequencing to use.  :(  If you ever find an accurate set of documentation, please share it.  

As for a helpful suggestion, I've found that playing with the order of the parameters passed to the convert command will sometimes produce the desired output.  I'm sorry that I can't provide any better suggestion.  (I've never gotten the mogrify command to work correctly)

---

### Post by FuturePilot on 2007-09-19
What is the command you are using? I've been able to resize an image with mogrify and convert an image with the convert command just fine.

---

### Post by zmkhan on 2007-09-19
.. found my problem, corrupt images files... ImageMagick couldn't find the files because it couldn't read them. 15% off my grade because I'll have to turn the assignment in late b/c of corrupt files.. :mad:

Thanks for the help though everyone.

---

### Post by yabbadabbadont on 2007-09-19
Simple things like resizing aren't the problem.  At least not for me.  I can't speak for the OP though.

Edit: And I don't have to, since I was too slow.  :D

---

