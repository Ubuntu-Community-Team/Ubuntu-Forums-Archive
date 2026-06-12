---
title: "Specifying a local source in sources.list"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2006-12-26
Hi there:

Can you add a line to the sources.list file that specifies a local directory?  If so, what's it look like?

I've got the following in my sources.list file and I get the message that the line is malformed.  

deb home/kerry/programs/photopaint/dists/stable/non-free/binary-i386/ corel non-free

---

### Post by tagra123 on 2006-12-26
> **Kerry Lange said:**
> Hi there:

Can you add a line to the sources.list file that specifies a local directory?  If so, what's it look like?

I've got the following in my sources.list file and I get the message that the line is malformed.  

deb home/kerry/programs/photopaint/dists/stable/non-free/binary-i386/ corel non-free

Try looking at  apt-proxy ot aptoncd. for saving copies. I think another is apt-mirror.

Theres a little more to it than pointing to the folder but it was now awful to set up.

I have apt-proxy set up to save bandwidth and it works great between all of the pcs.

---

### Post by Kerry Lange on 2006-12-26
> **tagra123 said:**
> Try looking at  apt-proxy ot aptoncd. for saving copies. I think another is apt-mirror.

Theres a little more to it than pointing to the folder but it was now awful to set up.

I have apt-proxy set up to save bandwidth and it works great between all of the pcs.

Do I enter "apt-proxy" in the terminal?  Or, do I specify this in the sources.list?

---

### Post by az on 2006-12-26
The line is malformed.  

Try:

deb file:/home/kerry/programs/photopaint/dists/stable/non-free/binary-i386/ corel non-free



And that app is way too old....

---

