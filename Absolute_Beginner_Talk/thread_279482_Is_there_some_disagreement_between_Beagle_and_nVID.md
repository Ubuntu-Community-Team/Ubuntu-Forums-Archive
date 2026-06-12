---
title: "Is there some disagreement between Beagle and nVIDIA?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-18
Just when I'd finally resolved a bit of my graphics and speed problems by switching drivers from "nv" to "nvidia", now I start having problems with Beagle eating up all of my CPU usage. It happens at startup, and then at least once later if I'm on long enough. Is this coincidence? Are the two related in any way? Is there a quick (or long) fix i can employ? TIA.

P.S. - Just what, exactly, is Beagle?

---

### Post by po0f on 2006-10-18
ricardisimo,

The issue *might* be related to your NVIDIA drivers, but I doubt it.  Beagle is creating an index of your home directory so you can search for stuff a lot faster.  Every so often it rebuilds this index;  I'm guessing it checks to see when a significant amount of files have been added/removed before it re-indexes.  If you don't search for stuff a lot, or if you are organized like me ;), you don't need Beagle, and can turn it off.

---

### Post by ricardisimo on 2006-10-18
> **po0f said:**
> ricardisimo,

The issue *might* be related to your NVIDIA drivers, but I doubt it.  Beagle is creating an index of your home directory so you can search for stuff a lot faster.  Every so often it rebuilds this index;  I'm guessing it checks to see when a significant amount of files have been added/removed before it re-indexes.  If you don't search for stuff a lot, or if you are organized like me ;), you don't need Beagle, and can turn it off.

     OK. I've done file searches before, just testing it out via the regular file browser - Nautilaus, I guess - and it never works. Or rather it will find text files or scripts with the word I'm searching in it, but not in the filename itself. Weird, right? Is that Beagle or something else?

     How do I turn Beagle off? Thanks.

---

### Post by ricardisimo on 2006-10-18
I take it all back... I just tried it again and it worked fine. Bizarre.

Still, how would I turn it off?

---

### Post by po0f on 2006-10-18
ricardisimo,

This is off the top of my head, but navigate to System -> Preferences -> Sessions.  Click on the Start-Up (?) tab.  There should be an entry for Beagle or Indexing Service or whatever they decided to call it.  Click on it and click the disable button.

[EDIT]  Spelling...

---

### Post by Zeddicus on 2006-10-18
> **ricardisimo said:**
> I take it all back... I just tried it again and it worked fine. Bizarre.

Sounds like the reason it wasn't working before was that it hadn't had the chance to index your files. :)

---

### Post by ricardisimo on 2006-10-20
> **Zeddicus said:**
> Sounds like the reason it wasn't working before was that it hadn't had the chance to index your files. :)

Seems like a good theory, but when I noticed it was doing the same thing this morning, I decided to leave it alone. I came back six hours later and it's still eating up all of my cpu. Clearly that's not by design. Any recommendations other than shutting it off? Is a fix in the works? Thanks.

---

