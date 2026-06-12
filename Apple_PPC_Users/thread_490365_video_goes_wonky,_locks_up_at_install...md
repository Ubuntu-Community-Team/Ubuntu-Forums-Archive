---
title: "video goes wonky, locks up at install.."
date: 2007-07-02
forum: Apple PPC Users
---

### Post by scowan007 on 2007-07-02
powerpc Ti Powerbook 1GHz, 1GB.
This happens with every mode of install on both ubuntu 7.04 and 7.10.

I get to the "boot:" prompt, and no matter which option I select, I get a few lines that something is loading (goes by pretty quick), and then the screen goes to what I can only describe as looking like a tv tuned to a wrong channel.  snowy static.  The CD continues to spin for about 30 seconds, then nothing.  I have let it sit for over five minutes, and no activity.

Any thoughts?

Thanks!

---

### Post by scowan007 on 2007-07-02
PS - it does the same thing with the alternate discs.

---

### Post by tcrroadie on 2007-07-02
The live cd may be choosing the incorrect display driver for your PowerBook.  You can try passing a boot option to force a video driver of your choosing.  For example to force the loading of the fbdev driver you would enter

```
xserver=fbdev
```

or
```
xmodule=fbdev
```

If your PowerBook has a Nvidia graphics card you could try nv. 

```
xserver=nv
```

or
```
xmodule=nv
```

---

### Post by scowan007 on 2007-07-03
Thanks - where/when do I enter one of those? at the "boot:" prompt before selecting one of the installs (selected by hitting tab)?

---

### Post by stmiller on 2007-07-03
7.10 is going to be hit or miss, at the present time. Unless you are making a test machine, I would avoid gutsy right now.

There is a PowerPC alternative CD you can download. It goes straight to an installer (no pretty live CD). So try that if the live CD won't work. Feisty works great on my TiBook, other than a current sound issue. See this mega thread: 
[http://ubuntuforums.org/showthread.php?t=412151](http://ubuntuforums.org/showthread.php?t=412151)

---

### Post by scowan007 on 2007-07-03
Thanks again, Unfortunately I am using the alternate install CD.  After I select how i want it to boot (even the cli modes), it goes byebye.  :-(

---

### Post by scowan007 on 2007-08-23
Bump

---

