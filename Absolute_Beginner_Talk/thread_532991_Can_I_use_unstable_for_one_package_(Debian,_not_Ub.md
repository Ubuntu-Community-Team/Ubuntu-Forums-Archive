---
title: "Can I use unstable for one package? (Debian, not Ubuntu)"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Stringsy on 2007-08-23
I can't get my head round this nonsense.

[B]deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch main contrib non-free
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free[/B]

That's what I have in my sources.list file atm.

I'm running Etch on a dedicated server... so I don't need to be on testing/unstable but there IS some things from testing that I would like.

I've tried adding new stuff in the sources.list file, but it doesn't seem to work. Is it even safe to just temporarily add a repository for an updated package? 

I don't really want to have to compile rtorrent from source...

I know it's Debian, but I can't find help any where else :(

Edit: Apparently pinning might be useful, how does this work?

---

### Post by bodhi.zazen on 2007-08-23
What repo are you wanting to add ?

It can be problematic to mix Debian/Ubuntu repo's, or even stable/testing in Debian.

Pinning is the way to go if you do, and yes, install only what is needed.

Mixing repos and doing apt-get update && apt-get upgrade is asking for problems :twisted:

Pinning is not too hard, but you will want to read up on it first ...

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu](http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu)

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by Stringsy on 2007-08-23
Cheers.

Is there any way for me to use the pinning method with Aptitude? I've been using it primarily so far so it'd to be able to maintain that.

---

### Post by kerry_s on 2007-08-23
> **Stringsy said:**
> Cheers.

Is there any way for me to use the pinning method with Aptitude? I've been using it primarily so far so it'd to be able to maintain that.

in aptitude use the "F" option, "shift ?" if you don't know what that is.
i use etch/lenny, which shows as lenny/sid, hmm go figure. :) what ever you do, do not update aptitude, it only works correctly in etch, lenny and sid it freezes after each install, you have to switch consoles to kill it. :mad:

```

deb http://mirrors.kernel.org/debian/ etch main contrib non-free
deb http://security.debian.org/ etch/updates main contrib non-free
deb http://mirrors.kernel.org/debian/ lenny main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

#deb-src http://mirrors.kernel.org/debian/ etch main contrib non-free
#deb-src http://security.debian.org/ etch/updates main contrib non-free
#deb-src http://mirrors.kernel.org/debian/ lenny main contrib non-free
#deb-src http://security.debian.org/ lenny/updates main contrib non-free


```

---

