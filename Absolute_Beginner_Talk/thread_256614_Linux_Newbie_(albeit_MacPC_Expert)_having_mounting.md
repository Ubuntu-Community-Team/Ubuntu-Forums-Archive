---
title: "Linux Newbie (albeit Mac/PC Expert) having mounting issues"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by robotissues on 2006-09-13
OS X was my gateway drug into Linux - I have been playing with computers for over 20 years, and yet I am having difficulty finding information on how to do something that seems as if it should be super straightforward - I want to mount (connect) a folder on my mac notebook (running OS X.4) to my freshly installed Ubuntu installation.  I suspect this is pretty easy - and this is why I am having trouble finding anything on the topic.  I have read man mount.  Please advise!

---

### Post by sgtBiafra on 2006-09-13
First, a quick question: is the Ubuntu installation on the Apple notebook or on another machine?

If it's on the same machine, you should be able to simply mount it using the OS X mount command assuming that it will support the filesystem on your Ubuntu partition (typically ext3).

If Ubuntu is on another machine on your network you're probably looking to setup a NFS share of a folder on said machine and then mount it from the Mac. I don't have an example on hand but you should be able to find information if you use some of the keywords above either here or on a web search engine.

Please excuse me if I misinterpreted your initial post.

---

