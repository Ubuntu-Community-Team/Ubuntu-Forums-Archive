---
title: "Can I mount one directory on a drive to be seen on another?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2008-03-04
Is it possible to mount just a single directory as another directory on a separate drive?  For instance:

I want to mount a certain folder on a USB drive to /home/<user>/Media so that the file system sees that other folder only in this new location.  How do I do this?

-Mike

---

### Post by LuisGMarine on 2008-03-04
Hmm, I tried this an the only way I can see it is by creating a sym link.

This is what I did.  I have a folder named** REPORTS** on my USB drive, the correct path would be:
```

/media/USB/REPORTS
```

I want that folder to show up in my **/home/<username>/ **folder.  So I ran a link that says
```

ln -s /media/USB/REPORTS /home/<username>/REPORTS

```
So now when I go to** /home/<username>** the REPORTS folder is there, and I can view the info and stuff.

Hope this works for you , if you get lost in the process let me know an I can help you set it up.

---

### Post by mikeserv on 2008-03-04
Yeah, that's what I ended up doing.  I knew it could be done that way, but I haven't had the best of luck with symbolic links.  Of course, up to now, I've been creating sym links to an sshfs system, and every once in a while they go bad, but I think that has to do with network problems.  Hopefully the same thing doesn't occur with a properly mounted external.

-Mike

---

