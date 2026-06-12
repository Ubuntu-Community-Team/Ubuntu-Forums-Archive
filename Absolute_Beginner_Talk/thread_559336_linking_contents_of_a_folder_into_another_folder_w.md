---
title: "linking contents of a folder into another folder with its contents"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by crazybilly on 2007-09-25
I'd like to be able to have the contents of my windows 'my documents' in my home folder.

Right now, I do that with a symlink. W/in my home dir, I've got a 'Documents' folder that's linked to /media/hda5/My Documents.

But what I'd like is not to have another folder deep--I'd like to be able to have all the folders in My Documents show up in /home/mine.  Without replacing the contents of /home/mine, but rather in addition to them.

I could symlink to My Documents/*, but then, if I saved a new file in /media/hda5/My Documents, it doesn't show up in /home/mine, does it?

Anyway to do this?   Thanks!

---

### Post by justleen on 2007-09-25
you should vreate symlinks to all the different folders then..

and if you save a file to location A, it will not show up in location B...

But,. offcourse, if you have simlinked them, and save to My Docs, you will see them in the symlinked folder  in /home/mine/My Docs/

---

### Post by crazybilly on 2007-09-25
hmmm...sounds like ln won't do what I want to do, huh?

Are there other solutions out there?

thanks!

---

