---
title: "Deceiving &quot;Mac&quot; version on daily builds."
date: 2012-03-07
forum: Apple Hardware Users
---

### Post by andreigherghe on 2012-03-07
Hello!

Instead of doing a classic hybrid MBR-GPT partition table i want just a pure GPT. This was solved by using the EFI GRUB on Ubuntu.

I just went to download Ubuntu 12.04 daily, and i saw a "Mac" version. Cool! I thought. Downloaded, burned to CD, but surprise! Unlike the normal images, there was no EFI boot loader! I fired up the EFI shell tried to find the image, but no luck.

Searched on the internet for this "Mac" image, and it looks like it has the EFI boot loader removed.

WHAT?:confused: It's true that at the beginning it was buggy, it even bricked my MacBook Air! I was forced to reflash the EFI firmware, to make it go past the POST. But in the newer versions, EFI booting works flawlessly. Even brightness works on nVidia GPUs.

What do you think?

---

