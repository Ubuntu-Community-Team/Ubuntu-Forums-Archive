---
title: "xorg.conf mouse section reverted back by itself"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-24
I recently modified my xorg.conf file to get my mouse to use the side buttons.  All was working great, then yesterday I booted into Feisty, and noticed my side buttons weren't working anymore.  I checked the xorg.conf file and the mouse section was changed back to what it was prior to my modifying it.  A couple of things I know I did in between:  I switched off Beryl from auto starting with Feisty, and I messed around with my screen resolution (trying other resolutions/refresh rates, only to go back to what I had it set originally).  Any ideas why my mouse section reverted back?  I've since modified it again and my side buttons work once more.  I'm just trying to understand why it happened.

Thanks.

---

### Post by Pragmatist on 2007-05-24
Can you replicate the error?  If you shutdown and then boot up, does it change again?

---

### Post by timzak on 2007-05-31
Just a post-script on this issue.  I think I figured out why the mouse section changed back.  I just read another post on here from someone who saved their xorg.conf file via nvidia-settings and the output looks identical to what mine did so I think my mouse section was changed when I saved changes I made in nvidia-settings.  I don't know why this would change the mouse section, but it apparently does.  It also changes the whole layout of the xorg.conf file.  Ie, the ServerLayout section moves from the end of the file to the beginning, etc.

See this post: [http://ubuntuforums.org/showpost.php?p=2515006&postcount=10](http://ubuntuforums.org/showpost.php?p=2515006&postcount=10)

---

