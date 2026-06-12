---
title: "Shared file systems for Mac and Linux?"
date: 2011-12-07
forum: Apple Hardware Users
---

### Post by blueridgedog on 2011-12-07
My current Linux install can read journaled HFS with the current Linux kernel and I can write to non-journaled HFS.  Is there a journaled system that the two operating systems have in common?  I did a search and came up with a variety of outdated information, but ultimately concluded the answer was no.  Any revelations out there?

I find myself running OSX more lately for various reasons and would like to be able to access my store of files which are all on ext4 partitions.

---

### Post by Lars Noodén on 2011-12-07
I put /home on unjournaled HFS+  Then use the linux system as a base and symlink various application configurations into the linux system.  It's not always that the whole configuration directory can be symlinked.

---

### Post by blueridgedog on 2011-12-20
Thanks.  Any mounting tips for Mac?  It appears that Lion has an empty fstab.  I am moving my 700 gig of data to an HFS volume now.  It has taken me a few weeks to get my hackintosh working to my needs (and I learned a massive amount about how mac works).

---

### Post by Lars Noodén on 2011-12-21
No mounting tips, that's something that I've been meaning to look into on Lion myself.  I've been able to put it off because OS X automatically finds the HFS+ Linux partition and mounts it without intervention for me.

---

### Post by namo on 2011-12-22
Check out the following howto:
[http://www.tuxation.com/creating-home-partition-mac-linux.html](http://www.tuxation.com/creating-home-partition-mac-linux.html)

It worked for me.

---

### Post by linuxopjemac on 2011-12-23
You can also follow this thread:
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)

---

