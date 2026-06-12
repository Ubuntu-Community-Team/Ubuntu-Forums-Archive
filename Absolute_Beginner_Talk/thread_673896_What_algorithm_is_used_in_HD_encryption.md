---
title: "What algorithm is used in HD encryption?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Cadmus on 2008-01-21
Call it academic curiosity, or being able to prove on a graph to other people how secure it is. But what algorithm is used when you ask for HD encryption in Gutsy? I've taken a few pokes at google but I can't seem to turn anything up, also I'm struggling to find any info in the docs.

---

### Post by hyper_ch on 2008-01-21
you have different options for that. Best to grab you an alternate install cd and test it out yourself (in a VM).

---

### Post by Cadmus on 2008-01-21
Oooh, so encryption is like a box of chocolates, if so I'll be using Brazil Nut in Caramel if that's available :)

 I've got a spare box to try this on, no test better than live eh? Thanks for the fast response.

---

### Post by OoooMatron on 2008-01-21
Not a direct answer to your question either but another encryption program that encrypts partitions and containers for files is truecrypt and there you have a choice of different encryption methods and hash generators.

"TrueCrypt currently supports the following hash algorithms:

    * Whirlpool

    * SHA-1

    * RIPEMD-160
"

[www.truecrypt.org](www.truecrypt.org)

---

### Post by argie on 2008-01-21
It's based on dm-crypt as far as I know, so I think that would be AES-256. They may have changed the default though.

---

