---
title: "Showing certian drives/partitions on desktop"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by qpwoeiruty on 2007-03-16
I have a mounted fat32 partition in /media/storage. How would I get that to show up on my desktop? I don't want all the partitions I mount to show up there which is why I turned off the option to show all on desktop (it shows cds and partitions that I don't want there). .storage doesn't even show up in Places like my other mounted partitions do...

---

### Post by 23meg on 2007-03-16
You can create a link to it on your desktop.

```
ln -s /media/storage ~/Desktop
```

---

### Post by qpwoeiruty on 2007-03-16
Thanks. That worked.

I had tried: ln -s /media/storage /home/$(whoami)/Desktop
but there was something wrong with the symlink that was created...

---

### Post by 23meg on 2007-03-16
"~/" corresponds to the home folder of the active user. You can use it in place of "/home/username" everywhere.

---

### Post by qpwoeiruty on 2007-03-16
Thanks. That means that the code I tried and the one you gave me should be functionally the same, right? What could have make it not work that way? I did use my real username in place of $(whoami) when I typed it into the console. $(whoami) was inserted for the forums.

BTW: Is it possible to remove the arrow that appear on the links? I know that it is a symlink and don't need a visual reminder of it...

---

### Post by 23meg on 2007-03-16
> Thanks. That means that the code I tried and the one you gave me should be functionally the same, right? 

Yes.

> What could have make it not work that way?

It should have worked; I have no idea. Getting used to "~/" instead is a better idea though; it's shorter, and it doesn't need a command interpreter to work (it also works in graphical file selectors and the like).

> BTW: Is it possible to remove the arrow that appear on the links? I know that it is a symlink and don't need a visual reminder of it...

Not that I know of; do a forum search and you'll most likely find it if it's possible.

---

### Post by qpwoeiruty on 2007-03-16
> **23meg said:**
> Not that I know of; do a forum search and you'll most likely find it if it's possible.

I had searched for it but nothing came up. Not a big deal really. Thanks again for your help.  I was using ~ for tilda but I've reconfigured it to use just the grave. I'll definitely try to get used to ~/ in the console/terminal.

I'm always amazed at how friendly and helpful people are here, especially towards newbies. It's just not like that on most other forums.

--One very happy Edgy user :)

---

### Post by 23meg on 2007-03-16
One hackish way I can think of that you may want to resort to if it's hard coded (instead of recompiling) would be to find the icon file and replace it with a transparent PNG.

---

