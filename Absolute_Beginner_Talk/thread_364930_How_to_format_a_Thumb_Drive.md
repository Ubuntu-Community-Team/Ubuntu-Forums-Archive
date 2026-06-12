---
title: "How to format a Thumb Drive?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2007-02-18
Hi all,

How do I format a thumb drive? Id like to be partitioned as fat 32 if possible

Thanks,

Homer

btw, I am using Xubuntu.

---

### Post by kidders on 2007-02-18
Hi there,

I would do something like the following...

[LIST=1]
[*]Plug in the drive & take a look at the last few lines of **dmesg** to identify its /dev node.
[*]Use a basic disk partitioner (like **cfdisk** maybe) to partition it whatever way you want. One single big partition is probably best, for compatibility with things like Windows.
[*]Use one of the **mkfs** tools to format the partition(s) using whatever filesystem you like.
[/LIST]

Of course, if your drive is already partitioned, you can just do step 3.

Hope that helps.

---

### Post by mcduck on 2007-02-19
one addition to that post: The drive should not be mounted when you format/partition it.

Anyway, for a graphical tool just install gparted (It's the same tool that was used when installing ubuntu).

---

