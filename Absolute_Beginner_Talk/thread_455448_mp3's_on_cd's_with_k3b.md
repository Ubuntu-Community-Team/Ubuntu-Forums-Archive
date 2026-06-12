---
title: "mp3's on cd's with k3b"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2007-05-26
i would like to burn mp3 audio onto cd's using k3b.

i get:

Mp3 Audio Decoder plugin not found.
K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.
Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU).

can someone explain this or tell me how to do this?

---

### Post by Bachstelze on 2007-05-26
```
sudo apt-get install libk3b2-mp3
```

---

### Post by Rita G. on 2007-05-26
thanks HymnToLife! you made my day. works great!

---

### Post by andoty_jazz on 2007-08-31
Bonjour!

"As much as possible, I only wanted Official Ubuntu repos to retain clean updates."

So thank you very much coz I won't be needing external repos on my sources.

Really really appreciate your help.

---

