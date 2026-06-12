---
title: "Multiple wget downloads (+ rm to mp3)"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2005-11-21
Hello everybody,

A while ago I got a reply to my question how to convert realmedia to mp3. Arwen wrote a great script. Thanks a million.

(see [http://ubuntuforums.org/showthread.php?t=62564](http://ubuntuforums.org/showthread.php?t=62564) )

Anyway, does anynoe know how to simultaneously download several files via wget?

At the moment wget just runs through a long list. Is there anyway to download 4-5 files (from different sites) at the same time?

I use a list of command like :

wget -nc [http://www.tv-radio.com/scripts/download.php?file=rfi/mere/polonais/info/polonais_2200-2300-20k.ram](http://www.tv-radio.com/scripts/download.php?file=rfi/mere/polonais/info/polonais_2200-2300-20k.ram) -O /home/dafydd/rfi2200.rm
wget -nc [http://www.sr.se/laddahem/ekot/nyheter/p1eko18.rm](http://www.sr.se/laddahem/ekot/nyheter/p1eko18.rm) /home/dafydd/svenska1800.rm
wget -nc [http://www.sr.se/laddahem/ekot/nyheter/p3eko22.rm](http://www.sr.se/laddahem/ekot/nyheter/p3eko22.rm) /home/dafydd/svenska2200.rm
wget -nc [ftp://217.163.8.205/today/polonia_polish_1630.rm](ftp://217.163.8.205/today/polonia_polish_1630.rm) /home/dafydd/polska1630.rm


Thanks for help
Dafydd

---

### Post by suRoot on 2005-11-21
I'm sure some bright person could come up with some bash or perl script or something, but why not try

```
wget -nc http://whatever.ram -O /home/dafydd/whatever.rm &
```

-notice the ampersand (&)- which allows you to background the process & regain your prompt so you can move on to the next thing.

Or, if you know all the URLs you want to download, you could do:

```
wget -nc http://whatever.ram -O /home/dafydd/whatever.rm && wget -nc http://whatever2.ram -O /home/dafydd/whatever2.rm && wget -nc http://whatever3.ram -O /home/dafydd/whatever3.rm
```

Using multiple ampersands (&&) after a command will allow you to run another command after it has finished executing.

---

