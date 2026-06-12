---
title: "Any software similar to blindread in order to read scratched CD/DVD?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-10
Hi
Thank you for reading my post.
Is there any software for reading scratched CD  or DVD disks?
a software that can skip scratched sector and copy available sectors?
In windows we had blindread but I am no more a windows user.

Thanks.

---

### Post by prshah on 2008-04-10
> **legolas_w said:**
> Hi
Thank you for reading my post.
Is there any software for reading scratched CD  or DVD disks?
a software that can skip scratched sector and copy available sectors?
In windows we had blindread but I am no more a windows user.

Thanks.

Try ```
sudo apt-get install dvdisaster
```

It will attempt to read and recover data from scratched DVDs and CDs in a linear OR progressive fashion.

But, more usefully, it will allow you to add ECC information to the blank portion of an ISO image file so that if a CD created off that ECC encoded image is scratched, the optical drive firmware will automagically build the missing data from the ECC information, on the fly, completely transparently to the user! . A MUST for those who backup on optical drives!!

---

