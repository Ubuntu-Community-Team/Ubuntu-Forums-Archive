---
title: "Java problem with sound"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Tanchistu on 2006-04-24
I have a program written in Java that should play some sounds, but everytime I press play I get this message

 > Exception in thread "AWT-EventQueue-0" java.lang.IllegalArgumentException: Line unsupported: interface SourceDataLine supporting format PCM_SIGNED 44100.0 Hz, 16 bit, stereo, 4 bytes/frame, little-endian, and buffers of 88200 to 88200 bytes

What should I do?

---

### Post by skinnygmg on 2006-04-24
who wrote the java app?  maybe they have a codec/update for linux/ubuntu, or can point you in the right direction.  ask them with "contact us" if there's nothing about it on their site.

---

### Post by Tanchistu on 2006-04-24
I have reasons to belive that is not from the codec, but from the "streaming" of the signal to the OS. When I try to load a file coded with an unsuported CODEC I get a different error.

Here is the link to the program if anyone is intrested [http://ff123.net/abchr/abchr.html](http://ff123.net/abchr/abchr.html) the java version, I couldn't install the linux version. As you can see the developer offer little support, and the site is not regulary updated.

---

