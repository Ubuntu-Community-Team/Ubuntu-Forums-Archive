---
title: "How to copy a website"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-09-04
What is an app. or a way to copy a website? Like, to mirror it, basically? Thanks x)

---

### Post by aysiu on 2007-09-04
I think this might work: ```
wget -m http://www.nameofsite.com
```

---

### Post by Peter1234123 on 2007-09-04
Thanks, so much, it worked :), Now I gotta get BIND9 and Apache setup on the server I'm making, to mirror the site xD

---

### Post by HermanAB on 2007-09-04
If you are running your own BIND for the domain name, then you can set it up to do round robin DNS and load share between the two machines.

Cheers,

H.

---

### Post by vanadium on 2007-09-04
wget is a possibility. However, if you encounter difficulties, httrack might come to the rescue: httrack is specifically targetted to mirror websiste.

---

### Post by s26c.sayan on 2007-09-04
+1 httrack

---

### Post by hyper_ch on 2007-09-04
if the site belongs to you and if there is rsync installed, you could mirror it using rsync.

[http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

