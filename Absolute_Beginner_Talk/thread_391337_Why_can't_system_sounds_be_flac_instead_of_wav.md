---
title: "Why can't system sounds be flac instead of wav?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-23
I tried exporting a customized logout sound to /user/share/sounds in flac format, but Ubuntu won't read it. It seems somewhat counter-intuitive for Ubuntu to prefer a Microsoft proprietary format over its "free" correlate. Is this something that might be changed in the future? Thanks in advance.

---

### Post by hardyn on 2007-03-23
The wavs are uncompressed audio files, so they are not using anybodys technology just a convienient extension for a pile of bits. a flac is a compressed format and would require decompression before playing. the uncompressed formats can be shot to the sound card directly, where a flac would have to decompressed first, taking time and computing power.  It is done because it is convienient nothing more i would imagine.

---

### Post by ricardisimo on 2007-03-23
Unless I'm very much mistaken, flac is also uncompressed.

---

### Post by Bachstelze on 2007-03-23
You are mistaken. FLAC's compression is lossless but it's still compression.

[http://en.wikipedia.org/wiki/FLAC](http://en.wikipedia.org/wiki/FLAC)

---

### Post by ricardisimo on 2007-03-23
I guess I'm very much mistaken... Still, Audacity lists 16-bit flac as one of its uncompressed audio format export options, hence my error.

---

### Post by Bachstelze on 2007-03-23
Anyway, to answer your original question, I guess the reason why the sytem sounds can't be FLAC is because no one thought it was important enough to justify working on implementing it. You can either file a "Wishlist" bug... or code it yourself :)

---

