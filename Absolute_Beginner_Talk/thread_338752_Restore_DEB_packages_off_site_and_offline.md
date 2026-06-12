---
title: "Restore DEB packages off site and offline"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Jagermaster on 2007-01-14
Hey all,
I hope someone can help me with a small issue. I'm sure I'm missing something obvious.
I'm getting ready for a situation where I will have to install packages with no Internet connection available.

I have in my hand a CD with EVERY package and dependency met...backed up from /var/cache/apt/archives.

I tested it early last week (*as part of my learning process) *on with a fresh install and a small selection of packages but I had to install these things one at  a time...OK, if it's an emergency I guess ...but all checked out at that point.

NOW...here's where I lost track...I assumed that synaptic would pick up on the packages on the cd like it does when you insert any of the live cd's.  Instead of the happy "packages detected" message, I get the unsavory "NO packages were detected" message. The cd is nothing but packages and I CAN install items with gDebi one at a time...ugh....lol.

Did I miss something? I hope? :-k 

I hope someone can help...
Thanks,
B)

---

### Post by Marsolin on 2007-01-15
I'd suggest checking out [APTonCD]("http://linuxappfinder.com/package/aptoncd").  It allows you to creates a CD that can be used as a repository. Just having deb files on a CD isn't enough.

---

### Post by mcduck on 2007-01-15
if you just want to install *all* packages from the cd you can run 'sudo dpkg -i /media/cdrom/*.deb'

---

