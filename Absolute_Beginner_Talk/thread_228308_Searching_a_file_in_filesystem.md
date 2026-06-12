---
title: "Searching a file in filesystem"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-08-03
Hi,
I try to do search for a file or directory in my filesystem. I use Ubuntu 6.02 LTS.

I go to root and type the following command 

> ls -aR {file/directory_name}
it does not work the error message is 

> ls: hda6{file/directory_name}: No such file or directory 

When I try this for a filename  I am sure which is in the filesystem. it still gives the same stupid message.

What do you recommend? Thanks...

---

### Post by professor_chaos on 2006-08-03
you could use the find command or the locate command. Or use the GUI finder in Menu->Places->Search for files

```
locate somefile
```
```
find / -type f -name somefile -print
```

---

### Post by dtfinch on 2006-08-03
I usually use "locate" to find files.
For example, to find files with "Inbox" in their name:
locate -r Inbox[^/]*$
The -r tells it I'm searching with a regular expression and the "[^/]*$" prevents it from matching any part of the path but the filename. Otherwise, if there's a folder matching that name, it'll list every file within it.

It's very fast, almost instantaneous. It depends on the slocate nightly cron job to keep its index up to date.

---

