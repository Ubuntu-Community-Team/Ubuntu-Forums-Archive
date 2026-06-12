---
title: "Permissions problem - cannot open my own files."
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-11-22
Okay, here's the problem.  My windows XP professional user profile got corrupted, all of my user permissions got screwed, I had to make a new account and copy the whole of my documents across, etc.  And of course, when I tried to open any files, I got a lovely "Access denied" message. I tried several methods, but I believe the user profile corruption madness wouldn't let the permissions change  - but enough about XP.

My theory was, that perhaps I could get to open these extremely important files using my Ubuntu liveCD.  So, that's what I'm on now.  But I'm doing 

```

sudo chmod a=rwx *.*

```

in the right folder, but when I rightclick on the files, the owner is set to root.  If I change this to LiveCD user, it just changes back to root.  But the permissions are set so that all can open and access the files - but it won't open.  An image, for example, to open in the image viewer just gives me an access denied message.

So, please, can you people help me get to open my files, or at least be able to copy them or something?  Because I'm lost and I don't know how to fix it.

And no, the files weren't encrypted.    (at least, I think not)


thanks for any help you can give.

---

### Post by ExpatPaul on 2007-11-22
Try changing the owner. The command is:

```
sudo chown OWNER FILE
```

Where OWNER is the new owner
and FILE is the file name

---

