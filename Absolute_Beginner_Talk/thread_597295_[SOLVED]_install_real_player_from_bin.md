---
title: "[SOLVED] install real player from bin"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by chilliepierre on 2007-10-30
I have looked through the other posts, but to no avail.  I have this error when I try to run the .bin file.

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Please help me out.  What do I do?

Thanks!

---

### Post by Inxsible on 2007-10-30
> **chilliepierre said:**
> I have looked through the other posts, but to no avail.  I have this error when I try to run the .bin file.

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Please help me out.  What do I do?

Thanks!Are you first making it executable by ```
sudo chmod +x RealPlayer10GOLD.bin
```

---

### Post by chilliepierre on 2007-10-30
I did do that...I figured out through helixcommunity.  I will mark this as solved.  Thanks.

---

### Post by haldean on 2007-10-30
```
sudo apt-get install libstdc++5
```

---

### Post by Billisnice on 2007-10-30
Will this tie real player to firefox?

---

### Post by philinux on 2007-10-30
realplay gold installs firefox plugins

---

