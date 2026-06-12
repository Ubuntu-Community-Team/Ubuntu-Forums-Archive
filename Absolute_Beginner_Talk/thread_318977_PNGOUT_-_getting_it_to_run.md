---
title: "PNGOUT - getting it to run"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Xubus on 2006-12-14
_Preface_: I'm new to Linux. I tried Gentoo a couple of years back but never managed to install it. I succeeded in compiling quite a bit but never managed to get a working installation.

Last week I decided to give Ubuntu a try, and I was really, *scarily* amazed at how easy it is to set up. It's a great learning experience, and my aim is to run Gentoo as soon as I'm familiar with how Linux works (far away, I'm sure). I'm loving all the perks, like Beryl and KHTML. :)


_On to my problem_: I can't get [PNGOUT Linux binaries](http://jonof.edgenetwork.org/index.php?p=kenutils) to run. Is there something stupidly simple that I haven't been able to do due to lack of experience? I've tried both the static version and the dynamic version to no avail.


An aside request is whether anyone knows of a simple way of logging avatars, a la Miranda IM's avatar logging plugin.


I wasn't sure whether to put this in beginner talk or general help, if this is the wrong place I apologise. As to why I posted it here rather than in the linked site's forums, they're not exactly very active and there wasn't a single Linux related thread that I could find.

---

### Post by steve.horsley on 2006-12-15
Not knowing what it is, I don't really want to try and run it myself. What is the problem - how are you trying to run them, and what error error do you get?

---

### Post by Xubus on 2006-12-15
> **steve.horsley said:**
> Not knowing what it is, I don't really want to try and run it myself. What is the problem - how are you trying to run them, and what error error do you get?

It's a PNG optimiser written by Ken Silverman. I managed to get it working, stupid me. Unfortunately it doesn't list its commands/switches (that seemed unintuitive - every other program I've used in bash so far lists its commands), but I'm sure I'll figure them out by trial and error. Thanks for replying nonetheless!

---

### Post by steve.horsley on 2006-12-15
You're welcome. Thanks for the heads-up.

---

### Post by canardo on 2007-06-28
sorry to bump an old post but how do you install precompiled binaries (particularly this application) onto debian/ubuntu 

Thanks in advance

---

### Post by Falcorian on 2007-10-01
> **canardo said:**
> sorry to bump an old post but how do you install precompiled binaries (particularly this application) onto debian/ubuntu 

Thanks in advance

You use the binary from the command line.

For example:

```
./pngout-linux-i686-static HUGE.png small.png
```

Also. to bring up the manpage:

```
./pngout-linux-i686-static --help
```


You can of course stick it somewhere on your path, you ~/bin and use it from anywhere as well.

---

