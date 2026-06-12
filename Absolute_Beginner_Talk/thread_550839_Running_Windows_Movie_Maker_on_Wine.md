---
title: "Running Windows Movie Maker on Wine?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-09-14
Has anyone been able to get Windows Movie Maker to work using Wine?

I installed Wine using these instructions:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

And I downloaded Movie Maker from here:
[http://www.download.com/Windows-Movie-Maker/3000-2194_4-10187903.html](http://www.download.com/Windows-Movie-Maker/3000-2194_4-10187903.html)

I was able to install the .exe file using wine without having any problems.

But now, I can't figure out how to **start** Movie Maker. When I navigate to the /.wine/drive_c/Program Files/Movie Maker/ folder, there is no .exe file to run the application.

Any help on this would be appreciated!

---

### Post by por100pre1 on 2007-09-14
Check if it is in the /.wine/drive_c/Windows folder. Otherwise you can try **Kino**:

```
sudo aptitude install kino
```

---

### Post by Odd-rationale on 2007-09-15
No, unfortunately, it is not in there either.

I'm more used to Movie Maker. But I guess I could use Kino if I can't get Movie maker to work.

Has anyone else been successful in installing Movie Maker using Wine?

Thanks!

---

### Post by caricc on 2007-09-15
How about an .msi file in movie maker? or even a .com. .bat....?

---

### Post by Kilz on 2007-09-15
For the most part Microsoft does its absolute best to make sure its proprietary applications never run under wine. After all how else are they going to lock you into using Windows so they can limit your freedom and maintain their predatory monopoly.

---

### Post by lisati on 2007-09-15
> **Kilz said:**
> For the most part Microsoft does its absolute best to make sure its proprietary applications never run under wine. After all how else are they going to lock you into using Windows so they can limit your freedom and maintain their predatory monopoly.

Well noted. There have been a couple of times when I've downloaded stuff from Microsoft's website, and they've put me through a process of "Your copy of Windows needs to be validated" or some such nonsense before letting me actually start the download.

BTW, I think there used to be more than one version of MovieMaker available for download, I don't know if that's still the case. I never bothered since it came preinstalled on two of my machines, and the one it didn't come on probably couldn't handle video editing (too old, slow etc etc)

---

### Post by stinger30au on 2007-09-15
i suggest you [install Automatix 2]("http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html")

then install ["Virtual Box"]("http://www.virtualbox.org/")


Virtual box allows you to install windows from its install cd and it thinks it is the only OS running...infact its running in a "shell" inside of Ubuntu.

you cna then do what you like. and you can share a directory on your hdd and copy/paste stuff from Ubuntu to Windows and vise versa... easy peasy

---

