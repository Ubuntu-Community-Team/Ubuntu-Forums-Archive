---
title: "Need to mount hfsplus with journaling in write mode, how?"
date: 2007-11-01
forum: Apple PPC Users
---

### Post by IronWolve on 2007-11-01
How do I force mount a hfsplus partition with write mode, since write is only supported if journaling is turned off?

I cant boot into it to turn journaling off, and I need to re-write the bootup files....

There has to be a way to force mount with write enabled when journaling is enabled. (Are you crazy?!) Yes, i need it.

Thanks.

---

### Post by jbardin on 2007-11-01
since the kernel doesn't support (can't WRITE) to hfsplus journals, there no way to write to the filesystem with the journals turned on.

This page has fairly up-to-date info:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by IronWolve on 2007-11-01
I know, im asking how to bypass this, so I can write. I guess put an older kernel on.

I want to write even if it can corrupt data.

---

### Post by jbardin on 2007-11-02
I guess the older kernel is your best bet. 
You just have to hope the mac doesn't check the logs before you can disable/rebuild them.

---

### Post by IronWolve on 2007-11-02
hackintosh on intel, with no sse3, need to put an sse2 kernel. 

Hope we get a native driver soon that supports journaling.

---

