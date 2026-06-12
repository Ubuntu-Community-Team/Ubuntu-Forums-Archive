---
title: "Ubuntu on external HD"
date: 2007-01-21
forum: Apple PPC Users
---

### Post by HenningS on 2007-01-21
I have a 250GB external harddrive that is formatted in that Mac OS X journaled thingy. When I use the LiveCD, Ubuntu recognizes it and all its contents, but can|t write on it. Now my question is:
Can I install Ubuntu on that harddrive (maybe set up a partition for it - possibly without deleting anything) and use it for Linux like I would a LiveCD, that is pressing a key while booting to load Ubuntu from that harddrive? If that's possible, how would I do it?
Thanks for helping!

---

### Post by kidders on 2007-01-21
Hi there,

As you mentioned, Linux won't write to journaled HFS+ filesystems. Turn off the journal, and you shouldn't have any trouble. :-)

---

### Post by linear on 2007-01-21
> **HenningS said:**
> I have a 250GB external harddrive that is formatted in that Mac OS X journaled thingy. When I use the LiveCD, Ubuntu recognizes it and all its contents, but can|t write on it. Now my question is:
Can I install Ubuntu on that harddrive (maybe set up a partition for it - possibly without deleting anything) and use it for Linux like I would a LiveCD, that is pressing a key while booting to load Ubuntu from that harddrive? If that's possible, how would I do it?
Thanks for helping!

USB or FireWire? I know booting from an external FireWire disk is supported in Edgy, but don't know if USB will work. (Dapper is another story - not easily done.)

As for the howto, the instructions [here]("http://www.ubuntuforums.org/showpost.php?p=755739&postcount=4") should mostly work - though you may need some tweaks to yaboot.conf to get exactly what you want. (There have been various conflicting posts on getting an install that "just works".)

---

