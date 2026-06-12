---
title: "Defrag, scandisk..."
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-09
SO do I have to perform things like defragging my disk everynow and then? How about scandisk? I used to have to do them all the time in windows, how about now? And if I do, how do I do these things and how often?

---

### Post by aysiu on 2006-01-09
You don't need to defrag.
Ubuntu will automatically do a scandisk every 30th time you bootup.

---

### Post by diggs on 2006-01-09
Right on! that was always a bit of a hassle. Now why don't I have to defrag?

---

### Post by cwaldbieser on 2006-01-09
[QUOTE=diggs]Right on! that was always a bit of a hassle. Now why don't I have to defrag?[/QUOTE]
The filesystem you are using (most likely ext3) is designed to minimize fragmentation.

---

### Post by nu2this on 2006-01-09
Way Cool!! I'm really stsrting to like Linux in general & Ubuntu in particular!

---

### Post by diggs on 2006-01-09
[QUOTE=cwaldbieser]The filesystem you are using (most likely ext3) is designed to minimize fragmentation.[/QUOTE]
[img]http://www3.telus.net/public/ulrich_d/orly.jpg[/img]

---

### Post by Zerocool10482 on 2006-01-26
That's really cool. Is there a way I can trigger it to happen when I want it. I would just like to see what happens. Is it in the startup when Ubuntu loads. So I don't have to do any maintenance for Ubuntu.

---

### Post by hen3rz on 2006-01-26
Diggs,

Whats that picture ment to be off.

---

### Post by el3ktro on 2006-01-26
Hi,
I can first repeat what Aysiu said:

- You don't need to defrag your harddrives. All major Linux filesystems (ext3, reiser, xfs, jfs ...) are designed to minimize fragmentation. A little fragmentation will always occur, but this is minimal and you don't have to care about it.

- Ext3 does an automatic file system check every 30 (I actually believe it was 45) mounts. Izt would also do such a check when you switch off your computer without halting Linux first. You can do a manual filesystem check with the command 'fsck.ext3' in the terminal. BUT BEWARE: You should NEVER RUN SUCH A TEST ON A MOUNTED FILESYSTEM. You should only run this test when the filesystem is NOT mounted, this is why this happens so early during bootup.

To sum it up: Forget about defragmentation or file system checks, you're using a modern OS now :-) You don't have to care about such things anymore.

Tom

---

### Post by Zerocool10482 on 2006-01-28
Nice. I love Ubuntu. That's so cool.

---

