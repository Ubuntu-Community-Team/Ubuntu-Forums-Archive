---
title: "Dual boot Feisty w/ Linux Mint?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-06-23
Hi all! I have a laptop which currently runs Ubuntu 7.04, I've been trying out Linux Mint with a LiveCD for about a week, and I really like it. Anyway, is it possible to set up a dual boot with these two? I don't know how hard that will be with my current partitioning scheme:

[LIST]
[*]7 GB = /
[*]20 GB = /home
[*]1 GB = swap
[/LIST]
In that order.

Obviously, I'd want to share the /home partition between both Ubu and LM, but is there a way to do this without repartitioning everything? Any other advice/suggestions/comments about Linux Mint?

---

### Post by floke on 2007-06-23
My first question, is why do yo only have 28Gs to use?
I also wouldn't share /home between the two - so I would chop down your /home partition - say lop 6-7Gs off it using Gparted and then install Mint into that - it doesn't ask to set up a separate /home (a la PCLOS for example) so you'll be ok. It will also pick up your ubuntu partition in grub so no worries there. I currently use Mint alongside Feisty so can confirm that all this works fine.

---

### Post by hackle577 on 2007-06-23
I have an older laptop with a 30 GB HDD. Other than that, everything sounds sweet! Thanks!

---

