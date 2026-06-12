---
title: "midi audio file"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by muntaser on 2008-01-08
hi everybody
How can I play midi audio files on ubuntu?

thanx for your help

---

### Post by erginemr on 2008-01-08
Hello,

To play midi files, you need to install "timidity" as a software synthesizer. It is in Synaptic.

Check out this manual:
[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

If you are lucky to have a sound card (such as SB live series) that have hardware midi support, read this thread as well:
[http://ubuntuforums.org/showthread.php?t=8736](http://ubuntuforums.org/showthread.php?t=8736)

It is much better if you can use hardware synthesis, as Timidity relies on software synthesis, therefore CPU, and does not perform well on low end machines.

---

