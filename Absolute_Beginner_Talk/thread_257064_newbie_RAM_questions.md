---
title: "newbie RAM questions"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-09-14
Hello all, how are you?

I finally got a long awaited second hard drive and used it entirely for Ubuntu 6.06 and have a nice dual-boot going at home. My modem at home doesn't work, but the Nvidia driver I needed was on the CD so my graphics work well too. Went like a dream. 

My computer has 512 MB ram and as I was going through the system log I noticed that it says 511 MB LOWMEM and 0 MB HIGHMEM. 

I have no idea what Highmem and lowmem are, but for some reason this doesn't feel right. Also when I ran the system monitor it says 44% of RAM is in use (33% Cache) and none of the swap is in use.

The performance is not slacking in any way. I would just like to know 
[LIST]
[*]what Highmem and Lowmem are and 
[*]how to adjust them and 
[*]what it would do if I changed that.
[/LIST]

Thanks a lot in advance,

Cheers,
David K

---

### Post by kerry_s on 2006-09-14
That's ok, most computers these days have shared resources. A percentage of your ram is proabley allocated to the cpu or graphics card to use. That's how the computer company's cheat people out of ram.

---

### Post by dckirba on 2006-09-14
Well, it actually does show me almost all my ram - 511 of 512. I have a 128MB  Graphics card and that works well.

---

### Post by CatKiller on 2006-09-14
> **dckirba said:**
> Also when I ran the system monitor it says 44% of RAM is in use (33% Cache) and none of the swap is in use.

The performance is not slacking in any way.
A friend of mine that is more knowledgeable about such things was telling me about memory usage under Linux. He said that free memory is wasted memory, since it's not actually **doing** anything. So when you load a file, any file, Linux keeps it in memory until that memory is explicitly needed for something else - in case it turns out that you need it again - at which time the data in the memory gets replaced. And the previously-cached memory probably gets written to disk. That's why Linux memory usage seems higher than with other operating systems - they empty the memory, and then have to spend time loading the data again if it turns out that you need it again.

I don't know enough about it to comment on his statements' validity, but it seems reasonable to me.

Not that any of this actually answers your questions ;)

---

### Post by Najand on 2006-09-14
I have a link it might help you:
```

http://www.linux-mips.org/wiki/Highmem

```

---

### Post by dckirba on 2006-09-14
Thankyou, that did help :)

---

