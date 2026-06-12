---
title: "ext3 versus reiserfs"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2007-05-10
Hey guys!

I recently got a 500GB sata disc I'm using for backup and storage purposes and i'm wondering if I should format it as reiserfs or ext3?

I've heard rumors that reiserfs might take over for ext3 in a while, could any of you give me a short summary of the pros and cons for those two?

*edit:*
err, ignore that last question, i'm looking at Wikipedia right now! /selfslap ;)

---

### Post by Cypher on 2007-05-10
First of all, ReiserFS will not take over EXT3 as the standard Linux filesystem. 

ReiserFS is very well tuned to handle reading/writing of very small files constantly. In that, it is very useful for database servers which perform these actions. EXT3 does a much better job with larger files and general usage. 

EXT4 is supposed to improve handling of smaller files better and should rival ReiserFS in it's speed.

There are number of comparisons about these two FS' and in most cases, EXT3 will turn out to be the safer bet for overall performance..

---

### Post by Sef on 2007-05-10
They are both good file systems.   Ext3 is more popular and the most common default for GNU/Linux.   The only advantage of Reifers over Ext3 is that Reifers will never have fragmentation problems.   Usually ext3 won't but it can if the disk is really full (like 90%) or you are writing a novel or dissertation.  In short, either one will work fine for you.

---

### Post by Nunyah on 2007-05-10
Thank you for quick answers, Cypher and Sef!

After your insight and some reading, I think Ext3 is the one that fits my needs the most.

My thanks.

---

