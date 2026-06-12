---
title: "creating a new username/copying all settings"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by spin2cool on 2007-03-27
I'd like to change my username on my Edgy box, and I'm wondering what the easiest way to do this is.  Obviously, I'll create a new user first, and copy the contents of the home directory over to the new username.   

What about other settings, like group permissions, and such?  Do I need to be worried about these?  What's the best way to migrate all of these settings over too?

---

### Post by scrooge_74 on 2007-03-27
If I am not mistaken go ahead and create a new user, then from that user copy the entire content of the old user folder.  I think the new user will be the owner of the files, if not you can change them with the sudo chown command (with some parameters) do a chown --help from a terminal

---

