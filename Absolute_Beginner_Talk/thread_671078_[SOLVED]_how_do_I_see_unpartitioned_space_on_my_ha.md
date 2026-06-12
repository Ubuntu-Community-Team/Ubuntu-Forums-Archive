---
title: "[SOLVED] how do I see unpartitioned space on my hard disk?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-18
I have Gutsy installed on my 250 GB hard disk, but I don't quite remember if I left any space unpartitioned.
I installed GParted, and it shows all my partitions, free and used space and all that, but not if any space was left unpartitioned.
Am I missing something here?
Thanks.

---

### Post by ItalOz on 2008-01-18
In my opinion Gparted should be showing you unpartitioned space. It did for me.
If not it means that there isn't any

---

### Post by mikeyphi on 2008-01-18
> **kleo skywalker said:**
> I have Gutsy installed on my 250 GB hard disk, but I don't quite remember if I left any space unpartitioned.
I installed GParted, and it shows all my partitions, free and used space and all that, but not if any space was left unpartitioned.
Am I missing something here?
Thanks.

Any space left unpartitioned is shown as 'unallocated'

---

### Post by kleo skywalker on 2008-01-18
It is not showing any unallocated space, but it is showing my disk as being around 233 GB, when it is in fact a 250 GB disk. Why so?
I know that 250 GB does not mean exactly 250 GB, but 17 GB is a big difference.

---

### Post by mikeyphi on 2008-01-18
> **kleo skywalker said:**
> It is not showing any unallocated space, but it is showing my disk as being around 233 GB, when it is in fact a 250 GB disk. Why so?
I know that 250 GB does not mean exactly 250 GB, but 13 GB is a big difference.

That's about right!! My 250 disk shows as 235......

---

### Post by BillDozer on 2008-01-18
This is the correct size.

Computer calculate in Gigabytes where a Kilobyte is 1024 bytes, a Megabyte is 1024 x 1024 bytes, a gigabyte is 1024 x 1024 x 1024 bytes.

Computer manufacturors calculate in "human" sizes where a kilbyte is 1000 bytes, a Megabyte is 1000 x 1000 bytes and so on.

So 250 Gb = 250.000.000.000 bytes for the computer manufacturor which results in:
250.000.000.000 / 1024 / 1024 / 1024 = 232

Which is the size reported by Gparted.

---

### Post by kleo skywalker on 2008-01-18
> **mikeyphi said:**
> That's about right!! My 250 disk shows as 235......

Oh, so it's normal, eh?

---

