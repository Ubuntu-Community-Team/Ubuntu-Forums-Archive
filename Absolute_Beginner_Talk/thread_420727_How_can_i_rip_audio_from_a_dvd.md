---
title: "How can i rip audio from a dvd?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by dreamwarrior on 2007-04-23
hi recently i downloaded ultimate ubuntu,and i would like to rip the audio from a dvd,theres a few programs to work with dvds,but i dont now if any can rip only the audio...or if i can set any to do so...can anyone tell me which or how to do it? ill list the programs which appear in "U.U."(ultimate ubuntu),perhaps in this way someone can help me..: dvd::rip,lemonrip.....can anyone help me? thanks in advance...dreamwarrior..

---

### Post by simonn on 2007-04-24
Get dvds working with mplayer, you may need libdvdcss etc.. see the ubuntu wiki.

Then...

```

mplayer dvd://[X] -vc dummy -vo null -ao pcm -aofile [ouput file].wav

```

Where [X] is the dvd title number and [output file] is the output file

NOTE: haven't tested, but it should work.

---

### Post by Bachstelze on 2007-04-24
I personnally use DVD Decrypter, it's by far the best ripper out there imo. It is for Windows but VMWare is your friend :)

---

