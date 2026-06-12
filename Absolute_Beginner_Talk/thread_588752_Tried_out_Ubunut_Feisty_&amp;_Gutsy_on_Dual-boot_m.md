---
title: "Tried out Ubunut Feisty &amp; Gutsy on Dual-boot machine, now want to expand."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by sirjimmus on 2007-10-23
Hi,

for about two weeks I have been dual booting ubuntu and windows xp.  I have two hard drives, the main one has my xp installation and is 250gb,  the second was previously just a store for movies/games/documents and so on and I resized that to make room for ubuntu.

As of now I have only booted into xp to run Supreme Commander, everything else I do in Linux, including getting Steam + CSS running.

Is there an easy way within ubuntu itself to copy those files over, and expand the linux partition into the space made?  I would like my entire drive to be devoted to linux, but also keep the contents of the drive intact.

Currently I was thinking of borrowing my roommates 500 gb HD that's currently in his x-box to copy everything, wipe the partition and then resize the linux one.

Anybody see a problem with trying this or know of a better alternative?

Thanks
Jim

---

### Post by rudeboyskunk on 2007-10-23
Well, if it were me, I would do it.  ;)

But what you MIGHT want to do is resize Windows to be much smaller than it is.  The way I switched from Windows to Linux was to have a dual boot and use Linux as much as I could for everything I could, and Windows for fewer and fewer things.  When that list got to zero, it was time to just get rid of Windows.

You can run many Windows games and other Windows programs in Linux using either wine ([www.winehq.com](www.winehq.com)) or cedega ([www.cedega.com](www.cedega.com)).  Wine is free, Cedega is $5/month.

You should be able to mount your Windows partition within Linux and copy the files over that way.  Before you do that, though, you should make sure that when they are copied over they aren't all given root ownership (i.e., make sure that you as a regular user can access them without having to become root).  If you cannot do this, do what you suggested earlier.

Of course wait for other people to post suggestions, somebody might have a better idea than me.

---

