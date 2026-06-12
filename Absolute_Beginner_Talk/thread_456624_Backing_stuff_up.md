---
title: "Backing stuff up"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-05-27
I'm trying to decide how I should manage backups on a small (4 computer) network. I've identified several types of items that will need to be backed up. I've also got a rough idea of how I want to do them, but I'd like to run it by some more experienced folks before I try it. Check it out and let me know what you think.

1) Large media files - This would mainly consist of my MP3 files. I would think that this could be handled sufficiently with a shell script and rsync. Then again, I might want to take it a bit further and use Unison for the backups, so that new stuff would be propagated.
2) Configuration - I'd ideally like to have per user and system-wide configuration stored on the server. I think a subversion repository might do the job well. Is there a better way?
3) Documents - These would also probably best be handled with a subversion repository.

Since I've learned that on Linux that there is usually an easy prebuilt way to do most things, I thought I'd ask the community before I tried to come up with my own solution. Any thoughts?

---

### Post by ramjet_1953 on 2007-05-28
You may want to check out this link for Mondo Rescue:

[http://www.mondorescue.org/](http://www.mondorescue.org/)

I think that it may do what you are after.

You can download mondo / mindi, using the Synaptic package manager.

Regards,
Roger :cool:

---

