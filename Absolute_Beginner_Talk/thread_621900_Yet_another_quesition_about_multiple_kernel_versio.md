---
title: "Yet another quesition about multiple kernel versions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by bw44 on 2007-11-24
I know similar questions have been asked and answered in various threads, but I've checked them and I'm still not clear about something.

I just upgraded to Gutsy from Feisty.  I don't remember what the kernel version was under Feisty.

Now GRUB lists two kernel versions:

2.6.22-14-generic

2.6.20-16-generic
     
(I didn't notice before that this was a 2.6.20-16 -- when I originally posted this I said it was 2.6.22-16.)

At some point I  noticed there were two versions listed by GRUB, but I didn't look carefully at the numbers  and assumed the most recent would be the default. (duh!)

But 2.6.22-14 is listed first and is apparently  the one to which I have been booting. The uname command shows:

```
~$ uname -a
Linux DELL2 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

Should I be booting to 2.6.22-16?
                                       
(Again, my mistake -- this should have read 2.6.**20**-16

So assuming 2.6.22-14 is newer than 2.6.20-16, I've been booting to the more recent one.  I hope I didn't damage anything by actually booting to the older version!

Could someone confirm my understanding?

Thanks, and sorry for the confusion.

---

### Post by gn2 on 2007-11-24
16 is newer. 7.04 updated from 14 to 16, I think 7.10 shipped with 16.

---

### Post by bw44 on 2007-11-24
> **gn2 said:**
> 16 is newer. 7.04 updated from 14 to 16, I think 7.10 shipped with 16.

Could you please re-read my newly edited post? You are saying that 16 is newer than 14 (which is logical), but after looking more closely at the version numbers I think that 2.6.**22-14** is newer than 2.6.**20-16**.  

Could you or someone explain the kernel version numbering scheme?  Maybe then it would be easier to keep it straight in my mind. (I think  I need more coffee beans or some sleep!).

Thanks for replying.

---

### Post by gn2 on 2007-11-24
> **bw44 said:**
> I think that 2.6.**22-14** is newer than 2.6.**20-16**.  


You're correct, it is.

---

### Post by bw44 on 2007-11-24
gn2, Thanks for the confirmation.

For anyone interested, there's a detailed description of the Linux kernel version numbering scheme and its history at:

  [http://en.wikipedia.org/wiki/Linux_kernel#Versions](http://en.wikipedia.org/wiki/Linux_kernel#Versions)

---

