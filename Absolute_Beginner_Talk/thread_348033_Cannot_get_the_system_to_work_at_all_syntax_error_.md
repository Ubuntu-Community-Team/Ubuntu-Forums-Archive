---
title: "Cannot get the system to work at all: syntax error near unexpected token"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2007-01-28
I have completely lost my Ubuntu. I cannot get it to work even after a fresh install, because the home partition seems to have the same FS problem than the root FS did.
First, fsck fails. Manual fsck will not work, but I could do a thing like
e2fsck -b 8193 <sda4> and the answer was:
syntax error near unexpected token 'newline'
How am I supposed to understand something like that?
Is there a way to get the system to work? New install won't do the trick as I know now.

I will not be able to recommend Ubuntu or any Linux to anybody if these kinds of things happen, though I have tried to be a fan and deal with all these problems. It just isn't reliable at all.

---

### Post by JamieC on 2007-01-28
You need to remove the left and right arrows from around the device name (sda4).

What error messages do you receive? If you could provide them we could provide better instructions.

---

### Post by 1002285 on 2007-01-28
> **JamieC said:**
> You need to remove the left and right arrows from around the device name (sda4).

What error messages do you receive? If you could provide them we could provide better instructions.

Ok, that was stupid of me then. By now, I have got the system going somehow, though the fsck still failed (it ws before looking back at the forum).

I looked at the /home partition from Windows and found 2 files named sth like recently-used - and I remembered from another thread that these were problematic in one case in relation with opening gnome-panel. So i deleted them

After that, though fsck failed again, I was able to log in and the ubuntu gui started.

So maybe I am too stupid for Ubuntu, but I'm someone who has tried for months now. What would I tell in this situation to one of my good friends who I have convinced that ubuntu is easy and reliable and who looses valuable worktime because of this? It would be uncomfortable at least.

I will write again when I have tried fsck once more.

---

### Post by 1002285 on 2007-01-28
> **JamieC said:**
> You need to remove the left and right arrows from around the device name (sda4).

What error messages do you receive? If you could provide them we could provide better instructions.

Now I got sth like that:
Attempt to read block from filesystem resulted in short read ... Could this be a zero-length partition?

---

### Post by 1002285 on 2007-01-28
In windows I see on this partition a folder called "Recycled" and I cannot delete it. It seems like Windows is putting deleted files to that "recycled" instead of its own partition's recycle bin.
I do not remember having this "recycled" there earlier.
Can there be a connection?

Was able to delete "Recycled", but no change.

---

