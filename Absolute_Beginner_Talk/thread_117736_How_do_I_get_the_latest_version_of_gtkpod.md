---
title: "How do I get the latest version of gtkpod?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-15
I've installed gtkpod, which is included in the Ubuntu community repository.

However...the latest version in Ubuntu is 0.88.  I've got a 5th Gen iPod (:p ) and it doesn't work.  I'm guessing I need v0.99, which the gtkpod site says supports video files.

How do I get it?  Preferably using Synaptic.

---

### Post by dueY on 2006-01-15
Synaptic can be pretty slow with getting the newest versions of programs on it.  This is because the Ubuntu team puts the programs through a lot of testing first to make sure they work and don't break anything else etc.  So you're either going to have to add new repositories that would have it, or download the source or binary from the creator's website and install it yourself.

---

### Post by stuporglue on 2006-01-15
Generally speaking, what happens is the versions stay the same for a given Ubuntu release. 

For example, you're proabably using Ubuntu Breezy (5.10). The latest stable Gtkpod that the Ubuntu devs compiled and tested before Breezy was released must have been v. 0.88. If you're using Breezy, that probably won't change unless there are security patches or huge user demand. If either of those are the case, the newer version will show up in the security or backports  mirrors. 

If you want to install .99 via synaptic, you'll have to wait for Dapper, or use it now even though it's still in development. I'm using Dapper and it lists gtkpod version as 0.99.2

---

### Post by 23meg on 2006-01-15
Since .99 is in Dapper, you can place a backport request if there already isn't one. Take a look at the backports policy before doing it.

---

### Post by Edward The Bonobo on 2006-01-15
Actually...Breezy wouldn't install (a known problem, but I forget the details), so I'm running Hoary.

Can I not get synaptic to point at another (non-Ubuntu) repository that has 0.99?

---

### Post by stuporglue on 2006-01-15
If you have the bandwidth to spare, what I would recomend is to upgrade to Breezy (or Dapper, if you're feeling brave). If the Breezy+your computer problem was just with the installer, you can upgrade fairly easily.

An upgrade to Breezy plus a request for a gtkpod backport would probably be the easiest route. Upgrading to Dapper would be the fastest route. 

If you want gtkpod .99 with Hoary, I'm not sure what the best route would be. Possibly compiling it yourself. I'm not aware of (m)any un-official Ubuntu repositories, and using them may be risky anyways.

---

### Post by dueY on 2006-01-15
[QUOTE=Edward The Bonobo]
Can I not get synaptic to point at another (non-Ubuntu) repository that has 0.99?[/QUOTE]

You can do this.

---

### Post by Edward The Bonobo on 2006-01-15
Supplementary questions:

1) How do I upgrade to Breezy/ Dapper?  Can someone talk a newbie through this?

2) How do I get synaptic to point to another repository?  And how do I find another repository?  Do I specify a URL?

---

### Post by 23meg on 2006-01-15
1) [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

2) [https://wiki.ubuntu.com/SourcesList](https://wiki.ubuntu.com/SourcesList)

---

### Post by Edward The Bonobo on 2006-01-18
See also: 

[http://www.ubuntuforums.org/showthread.php?t=114946](http://www.ubuntuforums.org/showthread.php?t=114946)

---

