---
title: "[Help]MP3 problem ..."
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by ChristophorusX on 2005-08-25
I've recently mounted my Windows partitions and everything is working fine, now what I want to do is read MP3 files that are located on my Windows partition, now I go \media\Windows\Documents And Settings\ .... blah blah blah and finally get to the My Music folder ... when I select an MP3 file XMMS opens and just freeze ! I tried to open it with RythmBox but it tells me that it can't hanle MP3 files etc. So I tried to : **Associate XMMS to play MP3/M3U/WAV files**, article found on [http://ubuntuguide.org/](http://ubuntuguide.org/) but didn't work, any suggestions ?

---

### Post by Kvark on 2005-08-25
You need the codecs, do this to install them:
```
sudo apt-get install **w32codecs**
``` 

The reason codecs are not included out of the box is that including them out of the box would make ubuntu illegal in a few countries (USA and Japan plus maybe someplace I don't know of).

---

### Post by Knyven on 2005-08-25
[QUOTE=ChristophorusX]I've recently mounted my Windows partitions and everything is working fine, now what I want to do is read MP3 files that are located on my Windows partition, now I go \media\Windows\Documents And Settings\ .... blah blah blah and finally get to the My Music folder ... when I select an MP3 file XMMS opens and just freeze ! I tried to open it with RythmBox but it tells me that it can't hanle MP3 files etc. So I tried to : **Associate XMMS to play MP3/M3U/WAV files**, article found on [http://ubuntuguide.org/](http://ubuntuguide.org/) but didn't work, any suggestions ?[/QUOTE]
 After installing all codecs/plugins, yes me too, i have problems running XMMS when playing MP3s, it freezes. What i use is the Music Player that comes with when you install Ubuntu, my MP3's works fine with Music Player(Rhythmbox 0.8.8)

---

### Post by kyodi on 2007-05-11
My Rhythmbox won't play mp3's (click on play and it just locks-up) so I tried this codec solution:

```
sudo apt-get install w32codecs
```

and this is the result I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

Am I missing something???

---

### Post by cytutchi on 2007-06-01
I am using Amarok and it is amazing!!!!
it plays mp3 and if it is missing something it is getting it by it self automatically, it just asks you to get it, you say yes, after instalation restart amarok (close it nad re-open) and its really cool player!
you can get it easily through adept manager!!!
let me know if you went for it n u still had problems.

Good luck

---

### Post by zvacet on 2007-06-02
> Am I missing something???

Yes,you are.You are missing medibuntu repository.You can add it to your source list from here(or use complete source list I will give you link to)

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

