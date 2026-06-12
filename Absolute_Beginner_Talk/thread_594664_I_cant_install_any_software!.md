---
title: "I cant install any software!"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-10-28
from the Applications menu,

Almost every program there says, "XXXX cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

And everytime I try to check a box, it says that the list needs reloading, so it reloads, but then keeps asking me to reload every single time i check any box.

Little help anyone?

(I just installed Ubuntu 7.10)

---

### Post by jenhsun on 2007-10-28
1. what CPU type you have? EMT64? i386?? AMD64?
2. in terminal, type
sudo apt-get update
and see what's going on.
3. Go to check your software source in System/Administration/Software source
try to enable most of them.
4. report your problem here again.

---

### Post by KevNice on 2007-10-28
Ok, thanks for your post, all I had to do was enable the sources.

Cheers!

Kev

---

