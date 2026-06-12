---
title: "No official Firefox PPC binary?"
date: 2006-06-10
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-10
All, (last dumb question of the night, I swear)

Went to Firefox's site tonight to download the browser and it appears  that for Linux they only have a x86 binary.

How does one go about compiling a PPC version of Firefox? (or any app, for that matter?)

---

### Post by aysiu on 2006-06-10
Yeah, Firefox doesn't make a PPC binary for Linux... or a 64-bit one, for that matter.

The Ubuntu repositories Firefox has been updated to 1.5.0.4, though. ```
sudo aptitude update
sudo aptitude install firefox
```

---

### Post by macheadPDX on 2006-06-10
Hello Aysiu,

I did this but I'm still getting 1.5.0.1 version of Firefox (Deer Park). Any ideas how I can fix this?

Thanks in advance!

---

### Post by aysiu on 2006-06-10
The .deb for 1.5.0.4 is right here:
[http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-dbg_1.5.dfsg+1.5.0.4-0ubuntu6.06_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-dbg_1.5.dfsg+1.5.0.4-0ubuntu6.06_powerpc.deb)

So, are you sure you have the right repositories enabled?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by macheadPDX on 2006-06-10
Thanks!

---

### Post by iamdigitalman on 2006-06-10
yeah, 1.5.0.4 just came across the wire for me this morning as well. love that update manager.

oh, it and 8 other updates, including firefox-gnome-support.

good job guys. gonna update now.

-digital ;)

---

