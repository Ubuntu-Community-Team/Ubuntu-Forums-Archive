---
title: "Synaptic Package Manager Channels"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-13
Under Synaptic Package Manager > Settings > Repositories, in the Software Preferences dialog, the channels were accidentally deleted.  I believe there were eight originally, but for adding channels I am offered only four, all labeled Binary.  Do I need the other four "Source" channels?  If so, how can I get them back?  If not, why were they included originally?

I would greatly appreciate your help.  Thanks.

Buck

---

### Post by Average Joe on 2006-11-13
You don't really need the source channels. Usually installing the binaries works fine. Only if you want to compile (and modify) the source code yourself, you need the source files. That is why they are included by default.

You can see what is in your /etc/apt/sources.list file. The source repositories are probably commented out (lines starting with #deb-src). If you want to include them again, remove the # in front of these lines, save the file, and do a sudo apt-get update.

---

### Post by Buck2348 on 2006-11-13
Average Joe:

Thank you very much for that informative answer.

Buck

---

