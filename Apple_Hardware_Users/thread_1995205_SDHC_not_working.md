---
title: "SDHC not working?"
date: 2012-06-03
forum: Apple Hardware Users
---

### Post by schut on 2012-06-03
Hey,

I have Ubuntu 12.04 running on my Macbook Pro 8,2. There is just one issue:

SDHC cards (class 10 card) will not mount. It works on another laptop under Ubuntu. SD cards work.

After searching the forum, it seems there are not many users experiencing this problem. Is just a package missing? 

Thanks for your help!

---

### Post by mjuhasz on 2012-09-17
The SD card reader in that MacBook Pro is not yet fully supported by the kernel in 12.04.

Without going into too much technical details bottom line is you may have to wait as long as the 3.7 kernel release, at least that's where the [voltage regulator support]("https://patchwork.kernel.org/patch/1229141/") is expected.

I also have a Class 6 card which suffers from the same issue while my Class 4 works just fine. I keep using the Class 4 card for now or I read the Class 6 card under MacOSX. Another workaround could be buying a USB card reader which is already well supported.

---

