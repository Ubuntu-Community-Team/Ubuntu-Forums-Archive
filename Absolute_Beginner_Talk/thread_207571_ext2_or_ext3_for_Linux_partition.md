---
title: "ext2 or ext3 for Linux partition?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by total-noob on 2006-07-02
I am about to install Ubuntu (and this is not the first time - I have tried successfully on a couple of other machines :D ). But being somewhat new to Linux, I have never really figured out which filesystem is the one I should be using for the Linux partion (I usually install dual boot with a shared vfat partion). Should it be extended2 or extended3? I know that there is something about journaling, but does it make any difference - I haven't really noticed any. Could someone clarify or provide a link to the explanation. I am sure it must have been in a FAQ somewhere - I just missed it.

---

### Post by Xzallion on 2006-07-02
I would choose Ext3 instead of Ext2, since they are very similiar and can be converted to each other. See the wikipedia article [here]("http://en.wikipedia.org/wiki/Ext3").

Hope that helps.

---

### Post by MaximB on 2006-07-02
you should chose ext3 and not just b/z of the journaling but you can make a bigger partition and you can have a bigger "max file size".
the journaling makes the recovery process much faster and safer.
every other file system like reiserFS has it's advantages so you should carfully chose depending on your needs.
search for more info at this forum.

---

### Post by steve.horsley on 2006-07-02
The only difference between ext2 and ext3 is the journalling (which ext3 has). Journalling is where the OS keeps a separate record of what it is about to do (and deletes when done) on the disk, so in the case of a crash or power cut, it can use the journal to fix any half-finished updates rather than being left with a screwed-up filesystem.

You want the journalling. Go with ext3.

---

