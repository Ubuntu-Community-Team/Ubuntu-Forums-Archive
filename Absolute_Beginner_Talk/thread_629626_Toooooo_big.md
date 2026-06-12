---
title: "Toooooo big"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-12-02
I just downloaded Gutsy from the Purdue mirror and when I tried to burn the CD it said it was 112, 508 kb and too big.  Is gutsy that big or did something go wrong?

---

### Post by CatastrophicToad on 2007-12-02
How big is it?  How big is the CD you're trying to burn it to?  What CD burning program are you using?

---

### Post by norwizzle on 2007-12-02
That's only 112mb if my math hasn't failed me. Ubuntu fills a cd (700nb). Maybe you mean 112mb over the limit, for which then might mean that your disc isn't empty.

---

### Post by daengbo on 2007-12-02
Something's definitely wrong. Whenever you download a distro to burn to CD, you should check the MD5SUM (hash) of it to make sure the download worked properly. In a terminal, type
md5sum [name of iso file]
and compare it to the MD5SUM here:
[http://ftp.daum.net/ubuntu-releases/gutsy/MD5SUMS](http://ftp.daum.net/ubuntu-releases/gutsy/MD5SUMS)
If they aren't the same, you should try downloading again.

---

