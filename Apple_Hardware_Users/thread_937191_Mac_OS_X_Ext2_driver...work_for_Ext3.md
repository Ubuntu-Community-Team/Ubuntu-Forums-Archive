---
title: "Mac OS X Ext2 driver...work for Ext3?"
date: 2008-10-03
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
That's pretty much my question. I've heard varying responses depending on where I look...does the most recent Ext2 filesystem for Leopard work with Ext3 filesystem? 

[http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/")

If so, what's the easiest way to convert Ext2 to Ext3 (I can figure that one out myself, but if someone has a quick answer I'll take it).

---

### Post by cyberdork33 on 2008-10-03
> **teamjh14 said:**
> That's pretty much my question. I've heard varying responses depending on where I look...does the most recent Ext2 filesystem for Leopard work with Ext3 filesystem?yes/no. It "works" but it gives people a lot of trouble. More than it is worth imo.

> **teamjh14 said:**
> If so, what's the easiest way to convert Ext2 to Ext3 (I can figure that one out myself, but if someone has a quick answer I'll take it).

ext3 IS ext2, it just has a journal added to it. You can create a journal on your ext2 filesystem with the tune2fs command from a linux live cd.

```
tune2fs -j /dev/sda3
``` (be sure to use your partition number if it is not 3).

Note that you will need to edit your fstab and such to reflect the change. You might want to read through some experience first to make sure you have your bases covered though:
[http://www.google.com/search?q=convert+ext2+to+ext3](http://www.google.com/search?q=convert+ext2+to+ext3)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
> **cyberdork33 said:**
> yes/no. It "works" but it gives people a lot of trouble. More than it is worth imo.

ext3 IS ext2, it just has a journal added to it. You can create a journal on your ext2 filesystem with the tune2fs command from a linux live cd.


I was completely unaware of this solution. I'll give it a shot.

I read an article that stated "the major difference between ext2 and ext3 is that you don't have to run [FONT="Courier New"]fsck[/FONT] after an unclean shutdown with ext3" (I assume because of the journaling). I've had a handful of unclean shutdowns and the whole disk check in the beginning afterwards, while practical, is annoying. Will tune2fs take care of that situation?

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
Anybody?

---

### Post by cyberdork33 on 2008-10-03
> **teamjh14 said:**
> Anybody?
it creates the journal on the filesystem turning it into an ext3 filesystem. having a journal allows disk commands to be replayed on startup if there is a unclean shutdown. ext2 does not have this, thus, it has to check the fs to make sure an action in the middle of doing something did not corrupt a file.

---

### Post by Tu1J4kXk8NUhMz on 2008-10-03
Ah, I see. Thanks!

---

