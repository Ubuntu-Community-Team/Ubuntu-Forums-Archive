---
title: "NTFS mount!!!"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-28
How do i mount my main drive,(My windows drive NTFS) and my external USB NTFS drive so that i can read/write to them?
thanks

---

### Post by PriceChild on 2006-10-28
A nice tutorial: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

The external usb drive should be automounted...

---

### Post by DOD1951 on 2006-10-28
As far as I know writing to native NTFS formatted disks from Ubuntu is not well supported.

---

### Post by PriceChild on 2006-10-28
> **DOD1951 said:**
> As far as I know writing to native NTFS formatted disks from Ubuntu is not well supported.You can isntall ntfs-3g from a howto on these forums.

However... writing to ntfs filesystems is NOT safe, and could in extreme cases cause large data loss.

Much safer to write to ext2/3 partitions from windows using [http://fs-driver.org](http://fs-driver.org)

---

### Post by szaka on 2006-10-29
> **PriceChild said:**
> 
However... writing to ntfs filesystems is NOT safe, and could in extreme cases cause large data loss.
Hello PriceChild,

Could you please give more details? I'm the ntfs-3g driver project leader and writing with ntfs-3g must be safe and it NEVER should cause any kind of data loss. Our growing quality testing is very extensive, especially before each releases and drivers with know reliability problems are never released.

If you were aware of any data loss situation then please let me know as soon as you can. At present nobody reports data loss with the latest driver released over a month ago, even if many people are trying to break the filesystem intentionally.

Thank you.

---

### Post by fparri on 2006-10-30
Hi Szaka!

Do you think it could be possible, in future releases of Ubuntu, to have your driver already included in the distribution? I guess it would be much better for the common user :)

---

