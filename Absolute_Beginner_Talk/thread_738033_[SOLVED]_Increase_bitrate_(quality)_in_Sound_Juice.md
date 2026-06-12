---
title: "[SOLVED] Increase bitrate (quality) in Sound Juicer?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by sdim on 2008-03-28
Hi,everybody.
How can I set the bitrate to at least 192 in Sound Juicer?
This is the setting as it is now,and it encodes at 128.:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

---

### Post by Sbarton on 2008-03-28
Have a look here: [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

Scroll down to sound juicer and there is info on how to change bitrate.
HTH
regards

---

### Post by sdim on 2008-03-28
Thanks for the answer.
I found this piece of code,created a new profile,and it works fine:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

---

### Post by Sbarton on 2008-03-29
Glad you worked it out!
If you mark the post solved others may finf it helpful.
Thanks and regards

---

