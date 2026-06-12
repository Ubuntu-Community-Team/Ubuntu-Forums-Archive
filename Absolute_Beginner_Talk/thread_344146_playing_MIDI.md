---
title: "playing MIDI"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-22
I'm trying to use Rosegarden, at first when i lauched it i get an error " can't initialize MIDI system " ( or something like that ) - i fixed this by 
```

sudo modprobe snd-seq

```
and now i'm getting this error :
```

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

```
the tutorial i found ( that's meant for Ubuntu 6.06 ) says that i should do the following
```

 sudo sysctl -w dev.rtc.max-user-freq=1024

```
and after that, i still got the same problem in Rosegarden ( and all other programs that try to play MIDI, except Java ). Should i write this command diffrently for 6.10 ?

---

### Post by Sasa_Ivanovic on 2007-01-23
common, anyone ...

---

### Post by eric71 on 2007-01-25
That command to change the frequency never helped for me either.  I guess you really need a kernel compiled with that setting.  In edgy i used a real-time kernel you can get from [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/) , which seems to be down quite often. Also, feisty now has a low latency kernel available with an appropriate timer resolution for midi work.  I've read a few posts around here saying they were able to use this in edgy as well.

---

