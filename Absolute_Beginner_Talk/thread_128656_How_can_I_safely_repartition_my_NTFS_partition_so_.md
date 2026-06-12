---
title: "How can I safely repartition my NTFS partition so I can install Ubuntu?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by wbastien on 2006-02-12
^^ Topic. :) I dont want to reformat my computer again as I jsut reformatted it a few weeks ago, so how can I partition it without losing data?

---

### Post by aysiu on 2006-02-12
[QUOTE=wbastien]^^ Topic. :) I dont want to reformat my computer again as I jsut reformatted it a few weeks ago, so how can I partition it without losing data?[/QUOTE] Follow the instructions in the fifth link of my signature. 99% of the time, it'll work well, and you won't lose any data.

Just in case of that 1%, though, **always back *everything* up** first.

**ALWAYS BACK EVERYTHING UP FIRST**.

---

### Post by gerbman on 2006-02-12
[QUOTE=wbastien]^^ Topic. :) I dont want to reformat my computer again as I jsut reformatted it a few weeks ago, so how can I partition it without losing data?[/QUOTE]

You just need to free up enough room on the drive for the installation. To do this in Windows you need a piece of software like Partition Magic to resize the NTFS partition. Another choice you need to make is how to partition the resulting free space for Ubuntu. There are many different ways to do this, but my personal preference is to allocate a 1 GB swap partition and split the rest between my home and root partition. This can all be done in the installation utility by selecting to manually edit the partition table. I'm not sure how familiar you are with these procedures, so I'll leave the ball in your court to ask questions ;-)

Hope that helps.

---

### Post by gerbman on 2006-02-12
Aysiu, I should have known you would beat me to it :-)

---

### Post by wbastien on 2006-02-12
[QUOTE=aysiu]Follow the instructions in the fifth link of my signature. 99% of the time, it'll work well, and you won't lose any data.

Just in case of that 1%, though, **always back *everything* up** first.

**ALWAYS BACK EVERYTHING UP FIRST**.[/QUOTE]
thanks a lot, great guide.

---

