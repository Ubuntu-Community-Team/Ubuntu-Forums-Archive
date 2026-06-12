---
title: "7/7 mount boot loader"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Tlingit on 2007-11-04
Hello,
I am on 7/7 in this advanced menu i for the boot loader. It says (hd0),
but i only have
/dev/sda1 ntfs /media/sda1 121088 MB 16200 MB (used)
/dev/sda3 ext2 1095 MB Unknown (used)
/dev/sda4 swap 10001MB Unknown(used)
/dev/sda/2 ntfs /media/sda2 8000 MB 7100MB

what should i put were (ha0)?
any other things i should know

were should i mount or put were (hd0) is??? for the boot loader??

---

### Post by dpar on 2007-11-04
(hd0) means the first hard drive. Grub starts counting at 0. This, i believe would translate to mean that it wants to install grub onto sda1.

---

### Post by Tlingit on 2007-11-04
so i can change 0 in (hd0) to 3? because that is were i am installing  linux?

---

### Post by dpar on 2007-11-04
I don't think so, that would put grub on your swap partition. Are you trying to duel boot linux and windows? If so, then let it install grub on hd0.

---

### Post by Tlingit on 2007-11-04
Ok yes i am dual booting Linux and Vista i will leave it as it is hope it works

---

### Post by dpar on 2007-11-04
Ya, I don't know squat about Vista, but on XP, that is what you would do.

This is a good read too    [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Tlingit on 2007-11-04
Hello,
Yep thank you i have been reading that web site along with many others and you just told me the last key  it works like a charm boom have it all set up now im going back to working on wireless so thank you.

---

### Post by dpar on 2007-11-04
Your welcome....glad it all worked out.

---

