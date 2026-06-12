---
title: "Asus K50IJ webcam  in skype"
date: 2011-10-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ashraf_zmn on 2011-10-15
I am using Ubuntu 11.10 64 bit. I tried,
> LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skype
That gives me,
> ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

But cheese works fine. Only in skype the video is upside down.

---

### Post by jsevi83 on 2011-10-21
Maybe you can try this:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by hotweiss on 2011-10-23
Here's the solution that worked for me:

1. sudo apt-get install lib32v4l-0

2. sudo mv /usr/bin/skype /usr/bin/skype.real

3. sudo gedit /usr/bin/skype

4. Paste:

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

5. sudo chmod +x /usr/bin/skype

Then start Skype from the dash as you would normally.

---

