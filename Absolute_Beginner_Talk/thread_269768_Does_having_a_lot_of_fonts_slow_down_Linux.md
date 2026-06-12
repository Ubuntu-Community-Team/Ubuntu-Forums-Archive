---
title: "Does having a lot of fonts slow down Linux?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Saoshyant on 2006-10-02
Hi,

I'm wondering: will having a large number of True Type fonts (or of any other kind) slow down a Linux instalation?

I remember reading a lot of times that this was a big problem in Windows, where computers would slow to a crawl the more fonts the user would have.  Then, obviously came the question.  After all, while Windows and Linux are pretty different (thank Penguin God), they share the same kind of fonts: True Type, Type 1, and more rarely Open Type.  So, both OS's may share issues on how they handle fonts.

I've searched the forum, but I found nothing that resembled this, so this thread will not only enlighten me, but also other users in the future :)

---

### Post by adwait on 2006-10-02
AFAIK, no, nothing like that..

---

### Post by jaboua on 2006-10-02
At least it was like that in older releases I read because of some bug, but hopefully that's been fixed.

---

### Post by Saoshyant on 2006-10-02
That's great to hear.

---

### Post by Saoshyant on 2006-10-02
Oh, BTW, I found out that .PCF seems to be the native font type in Linux.  I went to Wp to find some more information, but the article doesn't exist yet.

Gentlemen, is there a Wikipedist in the room?  Would you be kind enough to write an article about [PCF]("https://secure.wikimedia.org/wikipedia/en/w/index.php?title=Portable_Compiled_Format&action=edit")?

---

### Post by thingy on 2006-10-02
Speaking from an experiment I did...I installed about free 1700 truetype fonts and the only issues I noticed was:

a) X took a little longer to start up (i guess there is a memory hit on X for having that many fonts)

b) Any application which displays a font menu will pause for a second or so to display this huge list of fonts.

c) If you had any bad/broken true type fonts in your collection, it will cause problems for X and for any applications that try to use them.

Ofcourse, having more than 100 true type fonts is plain silly as no one is ever likely to need to need that much choice and if you still insist on having that many fonts...god help the person who has to go shopping with you irl!


:-)

---

