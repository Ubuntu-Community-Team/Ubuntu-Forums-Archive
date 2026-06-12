---
title: "Dual boot problems"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-09
Hello

I set up a dual boot for my main hard drive when my secondary hard drive was already formatted as an ext. 3. Since then I have reformatted my secondary as an NFTS file system and now when I boot up my ubuntu OS I get this screen that says

```
fsck.ext3 unable to resolve 'uuid=080b319f-76e9-4eaa-906c-d11c22ea60e9'
```

what do I need to do to make sure that my os doesn't search for that hard drive at startup?

thanks

---

### Post by ray bot on 2008-01-09
Run ```
gksudo gedit /etc/fstab
``` and take out the line with that uuid

---

### Post by mrphud on 2008-01-09
Cool that worked. Are you familiar with sound problems for this OS?

---

### Post by NullHead on 2008-01-09
the uuid is like a mac address it's made just for that partition and format of the drive. When you format it the section that you formated is no longer using that special ID called a uuid. so when ubuntu installes it makes a special ID for you're current partition and puts that into you're computers files. SO when you boot it checks for that ID and if it changes it gives you the error you got.

---

