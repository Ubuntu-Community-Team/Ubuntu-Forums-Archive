---
title: "gcc - Ubuntu CD?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-19
Does the gcc package come with the Ubuntu CD? I don't have a ethernet connection or a DVD recorder, so I need to use my Ubuntu CD as a offline repo.

---

### Post by 23meg on 2007-03-19
Yes. You should install it, as well as other tools needed for compiling for source with ```
sudo apt-get install build-essential
```

---

### Post by .oops on 2007-03-19
Thanks. :)

---

### Post by taurus on 2007-03-19
> **23meg said:**
> Yes. You should install it, as well as other tools needed for compiling for source with ```
sudo apt-get install build-essential
```

You need to make sure there is an entry for your CDROM in /etc/apt/sources.list first or else it will look for one on the net.

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

