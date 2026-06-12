---
title: "swfdec for Shockwave Flash"
date: 2007-05-08
forum: Apple PPC Users
---

### Post by Alterax on 2007-05-08
Hello, everyone!

I am writing because I was having a problem installing the swfdec flash player on Feisty for the PowerPC.

I had (I thought) installed all of the dependencies that it had listed on the page, along with build-essential.  But I was still getting an error from an unmet dependency for gnome-vfs 2.

I couldn't find the package it required in the repository, but after giving up melodramatically and running apt-get install gnome-devel (The Gnome development packages), I was able to get a successful ./configure && make && make install.

I hope this helps anyone else that is having trouble with getting Flash to work with Feisty-PPC.

--Alterax

---

### Post by stmiller on 2007-05-08
Gnash currently is being more actively developed. Install gnash (instead), and check out the PPCFAQs (link below) for more flash tips.

---

### Post by kugn on 2007-05-10
I agree. In fact if you were to upgrade to Gutsy, the Gnash version you install will play videos on youtube, though it's still quite buggy.

---

