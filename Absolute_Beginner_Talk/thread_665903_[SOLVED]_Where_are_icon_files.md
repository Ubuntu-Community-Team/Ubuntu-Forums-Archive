---
title: "[SOLVED] Where are icon files?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-12
I am trying to add a favicon.ico to my MediaWiki install. I figured I'd just use one of the Ubuntu Gutsy system icon files.

I searched the filesystem (via Nautilus) for *.ico, and several hours later when I checked it was still running the search!

Not sure what's up with that, but I figure most/many of the icons are in a particular directory; I'd appreciate someone telling me which directory. Thanks.

---

### Post by HereInOz on 2008-01-12
Try /usr/share/pixmaps

---

### Post by Xavieran on 2008-01-12
Also,in Linux world we don't use .ico images...so an icon you find will just be a small png or svg or xpm...
Unless you know how to convert those into .ico...:)

---

### Post by erfahren on 2008-01-12
Linux doesn't use the .ico format for icons (that's really a Windows thing)

you can use GIMP to save a .png in .ico format - a favicon needs to be 16x16 - EDIT: maybe browsers can handle them bigger now

---

### Post by jjsonp on 2008-01-12
Awesome - thanks! I copied the file from /usr/share/pixmaps and added the following line to my MediaWiki's LocalSettings.php and it works perfectly:
$wgFavicon = "http://localhost/mediawiki/skins/common/images/icons/apple-green.png";

And actually there are some png's in the MediaWiki icon subdirectory already; I was erroneously searching for ico files, so many thanks for clearing that up.

---

### Post by nikoPSK on 2008-01-12
Can you please mark this thread as "SOLVED" :)

Best,
nikoPSK

---

### Post by jjsonp on 2008-01-12
Done - thanks, didn't even know that was possible/my responsibility.

---

### Post by nikoPSK on 2008-01-12
> **jjsonp said:**
> Done - thanks, didn't even know that was possible/my responsibility.

That's fine, another thing learned, I didn't know till like 200 posts :p

Regards,
nikoPSK

---

