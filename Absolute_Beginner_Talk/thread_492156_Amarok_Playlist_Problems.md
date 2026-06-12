---
title: "Amarok Playlist Problems"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-07-04
My music collection is in a separate NTFS partition from my Ubuntu installation so I can also access it from windows if necessary. I've been trying to use amarok (I used it in my kubuntu days and liked it) but am having some problems with importing playlists. My music collection has imported ok, I can play that in amarok fine but when I try to import and play my playlists (.m3u) it comes up with a "Local File Doesn't Exist" error. I've looked through the forums but couldn't find a solution, any help?

---

### Post by Wiebelhaus on 2007-07-04
I'd check their support forums , I faithfully use it , it's buggy as all hell , but it's just so amazing , I'll deal with the bugs...also it's only going to get better.

---

### Post by Matuku on 2007-07-04
It seems to be a problem with relative and absolute paths; if I convert it to a .pls (which contains absolute paths) it works (but the method I use is quite long-winded). Even if I open up the .m3u and change the addresses to absolute ones it also works. But what I'm looking for now is a program that will convert from .m3u to .pls for me; any suggestions?

---

### Post by tpg on 2007-07-14
> **Matuku said:**
> It seems to be a problem with relative and absolute paths
I know that you've probably already checked this, but are the m3u's in the right place for relative paths to work? Also things like spaces might cause confusion (they probably need to be escaped), but as it works fine when you change the paths to absolute I doubt this is the problem.

Have a look at [this]("http://www.tamacom.com/pathconvert.html") for path conversion (I haven't tried it myself).

BTW, you can access ext2/ext3 partitions from windows using the Ext2 IFS driver [here]("http://www.fs-driver.org/").

---

### Post by forestpixie on 2007-07-14
> **tpg said:**
> ...
BTW, you can access ext2/ext3 partitions from windows using the Ext2 IFS driver [here]("http://www.fs-driver.org/").


to be honest that's what I ended up doing - made an ext3 partition moved the music to it - Amarok has no problem reading those .mru's now. Then did as tpg suggests - use the ext2fs driver to see them in windows.

---

