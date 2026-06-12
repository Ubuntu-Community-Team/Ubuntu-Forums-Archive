---
title: "/usr/bin vs. /usr/local/bin"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by slink on 2007-10-08
Hi

I'd like to know the what's the difference between placing binaries at **/usr/bin** (the most of non-system binaries) and **/usr/local/bin** (like GoogleEarth).

Thank you

---

### Post by macogw on 2007-10-08
/usr/bin/ is for things installed/packaged by the distro.  /usr/local/bin/ is for things you've built from source locally for your system.  that's just the standard usage.  it doesn't *really* matter if the binaries are in usr/local/bin or /usr/bin/ provided you're not moving things around all over the place (else they won't be able to find their other parts)

---

### Post by aitorcalero on 2007-10-08
I think there is not difference at all, since both two paths are in your $PATH environment variable. Check this picture to know more about Linux filesystem.

[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

---

### Post by slink on 2007-10-08
That makes sense. Thanks!

---

### Post by HermanAB on 2007-10-08
The idea is that /usr/local is for schtuff you built yourself.  This is done to keep things tidy and prevent problems the next time you do an update.  Most users probably would not want the Ubuntu update manager to overwrite their carefully handcrafted programs, so some separation is necessary.

---

