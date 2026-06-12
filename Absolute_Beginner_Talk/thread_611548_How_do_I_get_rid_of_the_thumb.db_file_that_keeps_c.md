---
title: "How do I get rid of the thumb.db file that keeps croping up in Nautilus"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-13
I saw this being talked about a few days ago, but can't seem to trace the thread.

There is a file called thumb.db in my nautilus explorer. Is this normal or just a nuisance,

How to get rid of this?

Thanks

I am in Ubuntu Gutsy

---

### Post by jordanmthomas on 2007-11-13
Thumbs.db is generated when Windows enters a directory.  It's basically just a group of thumbnails of all the images in the directory.  To stop it from being generated, you have to tell windows to not generate thumbnails (god knows I don't remember how to do that...somewhere in explorer's options I'd guess, or you might need TweakUI or something similar)

You can find all the Thumbs.db files in a current directory using the find command (maxdepth means look 10 folders deep at most):
```
find . -maxdepth 10 -name Thumbs.db
```
It's up to you what you do with the list.
Me...I'd look the list over once to make sure I'm ok with deleting all these files and then do this:
```
find . -maxdepth 10 -name Thumbs.db | xargs rm
```
which would delete all the files that came up in your search.

Also, you can just delete them as you see them in nautilus, no harm will be done other than Windows will have to regenerate the file next time it peeks in the folder

Is this what you were looking for?

---

### Post by shuttleworthwannabe on 2007-11-13
Thanks, so it is a MS Windows thingy? I should have known. I will have to reboot into Windows XP and try and figure it out then.

Yes, that is what I was looking for.

and BTW, all the thumbs.db are in my Windows directory...I should have figured it out..

take care

S

---

### Post by jordanmthomas on 2007-11-13
Can't really get too mad at Microsoft on this one though.  Thumbs.db is usually hidden so they don't get in the way.
:)  Glad I could help.

---

