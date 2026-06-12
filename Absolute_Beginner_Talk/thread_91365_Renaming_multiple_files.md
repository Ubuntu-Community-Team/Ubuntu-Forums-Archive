---
title: "Renaming multiple files"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-17
Hello,

How do I rename multiple files in console?

Lets say here are the following files:

catwp-640.jpg
dogwp-800.jpg
horsewp-1024.jpg
penguinwp-1280.jpg

How do I get it to loo like this:

catwallpaper-640.jpg
dogwallpaper-800.jpg
horsewallpaper-1024.jpg
penguinwallpaper-1280.jpg

I tried **mv *wp*.jpg *wallpaper*.jpg** but it thinks I am trying to move the files into a directory.

How do I rename multiple files with CLI?

If it cannot be done in CLI, does anyone know how to write a script that will rename multiple files?  It cannot conflict with other files, the prefix (animals) or the suffix (numbers), and has to recognise non-alphanumberic characters such as the dash.

---

### Post by matthewv on 2005-11-17
The command rename does multiple renaming. Never used it though, so I don't have a clue how it works

---

### Post by bionnaki on 2005-11-17
[http://ubuntuguide.org/#mvb](http://ubuntuguide.org/#mvb)
perhaps that will work - havent tried though.

---

### Post by GeirG on 2005-11-17
I'll second Matthewv, rename should do the trick.
I have only played around with it a little bit, and I don't know Perl regexps enough to use it efficiently. 
I seriously need to learn though, 'cus it sure beats individually renaming all those ... bird pictures by hand.

Regards,

---

### Post by doclivingston on 2005-11-17
Try ```
rename s/wp/wallpaper/ *.jpg
```

Which renames the files "*.jpg", substituting "wp" with "wallpaper".

---

