---
title: "How to patch WINE ?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-04
I have found a few patched on wine which should fix some problems but i can't understand how to apply them can anybody help?

For example: [http://bugs.winehq.org/show_bug.cgi?id=5131](http://bugs.winehq.org/show_bug.cgi?id=5131)

---

### Post by jfinkels on 2007-05-06
> **mech7 said:**
> I have found a few patched on wine which should fix some problems but i can't understand how to apply them can anybody help?

For example: [http://bugs.winehq.org/show_bug.cgi?id=5131](http://bugs.winehq.org/show_bug.cgi?id=5131)

Hmm, that link where it says patch is just the output from a "diff" between two files. This is most likely just a convenience for the programmers of Wine who are working to fix that bug for the next release of wine. Perhaps you can try installing the latest wine from their development branch/nightly builds/whatever they use.

---

### Post by mech7 on 2007-05-08
but for example here it says too to make a patch? but how do i use / run it it does not say anywhere ? :(

[http://appdb.winehq.org/appview.php?iVersionId=2631](http://appdb.winehq.org/appview.php?iVersionId=2631)

---

### Post by orb9220 on 2007-05-08
Isn't the patch for source code and is applied to wine's source code during the compiling process?

Yep just looked at it. You have to compile wine source and the patch to end up with the modified wine.

It will probally be applied and released in one of the wine updates.

Or you will have to learn on how to compile the source and how to add the patch yourself.

---

