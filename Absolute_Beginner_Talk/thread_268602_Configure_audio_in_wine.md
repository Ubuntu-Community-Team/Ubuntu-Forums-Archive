---
title: "Configure audio in wine?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-30
When I click theAudio tab in winecfg, Wine crashes. I understand this is a fairly common problem, and that there are guides for how to fix it, but I can't seem to find them. I found the wine.wiki, via winehpq, but one of the suggested solutions did not work, and the other two I didn't quite understand.

It said to disable the default wine sound drver, but I don't know where to find it.it suggested changing a key string in the Wine registry, but I can't find it.

Help would be appreciated.

/Mimsy

---

### Post by zvezdogled on 2006-09-30
I had the same problem.
This thread helped me resolve it.
[http://www.ubuntuforums.org/showthread.php?t=210684]("http://www.ubuntuforums.org/showthread.php?t=210684")

---

### Post by Mimsy on 2006-10-01
Aha! I put 

> sudo modprobe snd-seq

in the terminal, and now I can click the Audio tab without crashing. Sweet! Thank you for the link. :)

Now when I click I instead get a message in the terminal that says, 

> fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

So now I'm off to do another search, for how to find and install libjack.so.

Oh, and Software updates wants to install a new version of Wine. anyone know anything about it? Are there any cool fixes in it that I will help me get sound and install my game-like application that so far has refused to run under wine?

Thanks,
Mimsy

---

