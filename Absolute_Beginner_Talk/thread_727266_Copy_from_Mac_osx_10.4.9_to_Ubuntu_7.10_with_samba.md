---
title: "Copy from Mac osx 10.4.9 to Ubuntu 7.10 with samba makes extra ._ files"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2008-03-17
When I copy files from Mac osx 10.4.9 to Ubuntu 7.10 with osx's Finder (trough samba) extra ._ files copies are made in the directory i copy to.

Whats happening and  how do  I disable this ?

---

### Post by scramasax on 2008-03-17
> **chrisdee said:**
> When I copy files from Mac osx 10.4.9 to Ubuntu 7.10 with osx's Finder (trough samba) extra ._ files copies are made in the directory i copy to.

Whats happening and  how do  I disable this ?

These are what would be the resource fork on the HFS+ filesystem:

[http://en.wikipedia.org/wiki/Resource_fork](http://en.wikipedia.org/wiki/Resource_fork)

You can't disable OS X's production of these unfortunately.  You can stop it dropping [.DS_Store](http://en.wikipedia.org/wiki/.DS_Store) files on a non-Mac machine:

[http://docs.info.apple.com/article.html?artnum=301711](http://docs.info.apple.com/article.html?artnum=301711)

But you can't disable its creation of resource forks in files.

---

### Post by chrisdee on 2008-03-17
Thank for your reply.

I started to like osx after using it for about 6 months now, but after getting
this info I dont like the os that much anymore.

This function is stupid, because I get alot of extra files in my webfolder that I dont want. These are in turn shown to everyone on the internet accessing my website.

Thank you for showing me how to disable this on other network folders.
I really think this shoud be disables locally also, but I guess as you say this is
not possible:(

Expecially since I run backup of my files on my mac to my ubuntu samba server
these stupid files are copied anyway because they already exists on the mac.
This gives me alot of extra work deleting them from the ubuntu server afterwards.

---

