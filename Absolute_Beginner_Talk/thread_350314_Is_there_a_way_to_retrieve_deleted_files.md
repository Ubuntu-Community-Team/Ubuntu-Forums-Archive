---
title: "Is there a way to retrieve deleted files?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by HareBall on 2007-01-31
Subject says it all. I know of ways in Windoze, but was wondering about Linux. I deleted an email message and was wanting it back. I know it has probably been written over by now. I want this for future reference.:roll:

---

### Post by Brunellus on 2007-01-31
> **HareBall said:**
> Subject says it all. I know of ways in Windoze, but was wondering about Linux. I deleted an email message and was wanting it back. I know it has probably been written over by now. I want this for future reference.:roll:
if you deleted it with 

```

rm

```

it's gone.  cherish its memory, because that's all you've got left.

If you deleted it in the GUI, by default ubuntu moves all deleted items into a .trash folder in your home directory.  you can move them out.  Emptying the trash, though, runs 

```

rm -r 

```

on the contents of .trash, so, yeah, then they'd be gone.

If you deleted a mail message in Evolution, there's every chance it's still in Deleted Items.

---

### Post by HareBall on 2007-01-31
> **Brunellus said:**
> if you deleted it with 

```

rm

```

it's gone.  cherish its memory, because that's all you've got left.

If you deleted it in the GUI, by default ubuntu moves all deleted items into a .trash folder in your home directory.  you can move them out.  Emptying the trash, though, runs 

```

rm -r 

```

on the contents of .trash, so, yeah, then they'd be gone.

If you deleted a mail message in Evolution, there's every chance it's still in Deleted Items.
I deleted it from Thunderbird. It went to the trash file and then I emptied the trash :( 
I was hoping there was something like some of the programs that you can run in windoze that will retrieve things.
Oh well, lesson learned about Linux. Still a bunch to go:D

---

### Post by tkjacobsen on 2007-01-31
Here is a short description on how to undelete files on an ext2 filesystem:

[http://www.stud.tu-ilmenau.de/~mojo/undelete.html](http://www.stud.tu-ilmenau.de/~mojo/undelete.html)

Similar tools might be available for other filesystems, but I haven't used any myself..


Also found this link:
[http://std.dkuug.dk/keld/readme-salvage.html](http://std.dkuug.dk/keld/readme-salvage.html)

And this:
[http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html)

---

