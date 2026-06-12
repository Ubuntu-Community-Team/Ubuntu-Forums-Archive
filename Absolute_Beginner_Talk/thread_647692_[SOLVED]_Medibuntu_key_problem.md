---
title: "[SOLVED] Medibuntu key problem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-22
'no valid OpenPGP data found.'

I get that error?

---

### Post by wormser on 2007-12-22
Did you ad the line to /etc/apt/source.list and then the key?

Ubuntu 7.10 "Gutsy Gibbon":

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

I got it from [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

---

### Post by MangasColoradas on 2007-12-22
Thanks wormser, that worked.

I followed this [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) and it says to install the key first...

---

### Post by Majorix on 2007-12-22
It is always best to follow the official docs first (they have a how-to-install documentation on their site) and only then try other sources for info.

---

### Post by wormser on 2007-12-22
> **MangasColoradas said:**
> Thanks wormser, that worked.

I followed this [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) and it says to install the key first...

Usually the psychocats is spot on.  They should be emailed about the problem.  Make sure to mark this thread as Solved, directions in my signature.

---

### Post by MangasColoradas on 2007-12-22
Marked as solved now, thanks again wormser. :)

---

### Post by mrojas73 on 2008-03-02
Thank you, it fixed my problem too.

---

