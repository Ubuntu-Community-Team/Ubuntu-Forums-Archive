---
title: "X5522EA laptop - sound not working on board speaker"
date: 2014-01-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by srini-vassan on 2014-01-22
I am running Ubuntu 12-04 64bit on Asus X552EA laptop (AMD A4-5000). With pulse audio driver i am not able to get the audio on the laptop speaker. Headphone works fine. From the forums search, i found that this issue fixed on the latest kernel. If any work around for the official 12-04 Kernel (3.2.0-58) welcomed.

---

### Post by Dreamer Fithp Apprentice on 2014-01-23
Have you tried pavucontrol? If not enter```
sudo apt-get install pavucontrol
``` and your password, etc. If you already have it, that won't hurt, it'll just check to see if it is updatable. Anyway, start it by whatever means you like, such as typing "pavucontrol" in a terminal or run box. It has an "output devices" tab. It wouldn't be surprising if fiddlihg around there would help.  Maybe not, but it's worth a try.

---

