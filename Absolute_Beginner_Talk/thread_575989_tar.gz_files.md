---
title: "tar.gz files"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by waylandradio on 2007-10-14
I have downloaded a printer driver and it is a .tar.gz file.  How do I get it to open?  I need very, very basic instructions!!!  Thanks Dave

---

### Post by jon zendatta on 2007-10-14
desktop > terminal >
enter:
tar -xzvf file.tar.gz
cd file
. / configure
sudo make install

---

### Post by llamakc on 2007-10-14
The last part should be:

./configure
make
sudo make install

that is if it is not just the PPD.

---

### Post by Beggar on 2007-10-14
ARchive manager will also handle them, just right click in nautilus and select extract here.

---

### Post by ryanVickers on 2007-10-14
compiling source usually doesn't just work "out of the box" with Ubuntu I don't believe, but it's worth a try (still haven't got mine working!!!)

---

### Post by waylandradio on 2007-10-14
Thanks for the replies, but they make no sense to me at all.  I am a beginner that has downloaded a printer driver which I cannot get to open.  Please can I have very simple, step by step instructions what to do, ones that I will understand and follow.  Most of what is I has read is way above my head.  Thanks

---

### Post by PurposeOfReason on 2007-10-14
So it's a tar.gz file? Right click it and choose extract here. Then there should be a README, go from there. If it has .deb files, just double click those.

---

### Post by Frak on 2007-10-14
> **waylandradio said:**
> Thanks for the replies, but they make no sense to me at all.  I am a beginner that has downloaded a printer driver which I cannot get to open.  Please can I have very simple, step by step instructions what to do, ones that I will understand and follow.  Most of what is I has read is way above my head.  Thanks
What kind of printer driver was it, and mind you, working with a source package (.tar.gz) is long and hard to maintain.

Also, have you tried using the built in drivers from CUPS?

---

