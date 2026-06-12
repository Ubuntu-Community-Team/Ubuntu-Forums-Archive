---
title: "Warning about using nvidia-settings to save to xorg.conf"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-06-05
I'm not sure the best place to post this, but I figured the beginners would get the most benefit.  If you save your xorg.conf file through nvidia-settings, it will overwrite your mouse section with its own.  It also seems to make a few other (maybe only cosmetic) changes to the layout of the file.  I had modified my mouse section to use the thumb buttons and for the longest time couldn't figure out why I'd have to keep re-doing the mod.  Finally I saved xorg.conf through nvidia-settings, but saved it to a different file name, then compared it to my real xorg.conf and noticed that it puts in its own, completely generic, mouse section.

What I do now is if I want to save from nvidia-settings, I will save to a different filename, then copy and paste just the relevant lines into my real xorg.conf file.

FYI for anyone who is interested.

---

### Post by dfreer on 2007-06-05
Good Advice! the nvidia-settings completely rewrites the xorg.conf file, in my experience. I often find that my trackpad scrolling area will no longer work, and for some reason the terminal will no longer launch (weirdest thing ever, thought it was a fluke but if I switch back to my default xorg.conf they work).

---

### Post by wpshooter on 2007-06-05
> **timzak said:**
> I'm not sure the best place to post this, but I figured the beginners would get the most benefit.  If you save your xorg.conf file through nvidia-settings, it will overwrite your mouse section with its own.  It also seems to make a few other (maybe only cosmetic) changes to the layout of the file.  I had modified my mouse section to use the thumb buttons and for the longest time couldn't figure out why I'd have to keep re-doing the mod.  Finally I saved xorg.conf through nvidia-settings, but saved it to a different file name, then compared it to my real xorg.conf and noticed that it puts in its own, completely generic, mouse section.

What I do now is if I want to save from nvidia-settings, I will save to a different filename, then copy and paste just the relevant lines into my real xorg.conf file.

FYI for anyone who is interested.

Thanks for the info BUT if this O/S ever comes of age, all of this stuff should NOT be necessary !!!

---

