---
title: "removing long named file or folder"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Jnetty99 on 2008-03-24
I was playing with rtorrent for the first time last night and added a torrent link to test. 
anyways I now have a file or folder (not sure) under /Home/Me/ and can't figure out how get in the folder or delete it?

The name is long  'Linux Ubuntu Server 7 with lots of software ISO'

When I type cd Linux Ubuntu Server 7 with lots of software ISO I get 'no such file or directory'. 
when I type rm Linux Ubuntu Server 7 with lots of software ISO I get 
rm: cannot remove `Linux': No such file or directory
rm: cannot remove `Ubuntu': No such file or directory
rm: cannot remove `Server': No such file or directory

Any tips?

---

### Post by Lord Illidan on 2008-03-24
Spaces in bash are not handled very well. Try to use tab-completion, or else enclose the entire name in quotes. rm 'Linux Ubuntu...'

---

### Post by .nedberg on 2008-03-24
try just

cd Linu<Tab>

It should expand to the complete foldername in a way that should work. Do the same if you want to remove it.

Or just put the name in quotes:

cd "Linux Ubuntu Server 7 with lots of software ISO"

---

### Post by Jnetty99 on 2008-03-24
thanks, that helped with the Quotes.

---

### Post by Athelstan101 on 2008-03-24
Try this:
```
$ cd 'Linux Ubuntu Server 7 with lots of software ISO'
```

Or this:
```
$ cd Linux\ Ubuntu\ Server\ 7\ with\ lots\ of\ software\ ISO
```

---

