---
title: "JAD Java Decompiler Problem with libraries"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by JesterGr on 2007-05-26
I have downloaded Jad and unzipped it. I then moved the jad.exe to /bin (so i can call jad from terminal as a command. is that true? i am a newbie as you might have already figured out) and i
```
chmod a+x jad
```

but when i try to call jad (from terminal) it pops up
> jad: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I ensured that libstdc++6, libc6 are already in /usr/lib 

Plz, plz, plz give me a clue ... i have a homework to do, and i am already kinda late :(

---

### Post by JesterGr on 2007-05-28
bump. i suppose that this is not the right place to ask? which subforum is suitable for such questions? can any moderator move it there?

---

### Post by elektronaut on 2007-06-12
I had the same problem and solved it using the statically linked version which you can find on jad's home page.

---

### Post by ElemonGW on 2007-07-16
```
sudo apt-get install libstdc++2.10-glibc2.2
```
and everything will work like a charm!

---

### Post by manoswerts on 2008-05-21
> **ElemonGW said:**
> ```
sudo apt-get install libstdc++2.10-glibc2.2
```
and everything will work like a charm!

Maybe it's a little late, but i came across this topic today, and the above sudo apt-get didn't help me. So for people that come across this topic in the future, I just downloaded the statically linked version found [here]("http://www.kpdus.com/jad.html#download").

---

### Post by pentolino on 2008-07-24
Hello, both approaches work for me, statically linked version and install the library though apt-get.
Of course I prefer the apt-get way, so I advise anyone who will stumble here to try it first.
I use Ubuntu 7.10.
Thanks to all of you anyway

---

