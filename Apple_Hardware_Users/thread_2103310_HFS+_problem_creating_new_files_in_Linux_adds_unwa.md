---
title: "HFS+ problem: creating new files in Linux adds unwanted flag attributes"
date: 2013-01-09
forum: Apple Hardware Users
---

### Post by skullmunky on 2013-01-09
I'm running Kubuntu 12.04 on a Macbook Pro, set up in the usual multiboot way.  I work back and forth between OSX and Ubuntu a lot, so keep many documents on the HFS+ partition (non-journaled) and can generally work with them fine in both OS's.  

However, I notice that often when I create new files on the HFS+ partition while in Ubuntu, they end up having a lot of additional attribute flags when I boot back into OSX.

for example, this .doc file I made in LibreOffice in Ubuntu is locked and can't be edited in OSX:
```

ls -lO

-rw-rw-r--@ 1 skullmunky  1000   uappnd,uchg,nodump,opaque  19968 Jan  6 21:40 I_would_like_to_edit_this_but_cant.doc

```

'uchg' means it's locked (unchangeable), 'uappnd' means it can only be appended to, and I don't know what opaque and nodump are for but they shouldn't be there either.  

I can fix this with chflags in OSX

```

chflags nouappnd *
chflags nouchg *
chflags noopaque *
chflags dump *

```

But is there a way to make this not happen in the first place?  Some kind of mount setting for the hfsplus driver, maybe?

---

