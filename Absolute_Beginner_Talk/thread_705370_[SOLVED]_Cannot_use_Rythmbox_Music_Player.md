---
title: "[SOLVED] Cannot use Rythmbox Music Player"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Arrgoss on 2008-02-23
Hello,
I just installed Ubuntu 7.10 AMD64, and I'm trying to use Rythmbox Music Player to listen to my mp3 music. It doesn't work; when I try to load a song or a folder into the program, nothing happens. Is there anything I should do?
I installed the essential media packages following the first step of this post:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
but nothing changed. I can, though, listen to the radio.

---

### Post by Moop on 2008-02-23
Do you have the w64 codecs package installed?

[http://packages.medibuntu.org/pool/non-free/w/w64codecs/]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/")

---

### Post by sayakb on 2008-02-23
Banshee music player would be a good alternate to Rhythmbox.. Even the UI is quite similar..

---

### Post by Arrgoss on 2008-02-23
> **Moop said:**
> Do you have the w64 codecs package installed?
I'm sorry for this question, I'm a newby, but how do I check? And, if not, how do I install them?
Linuxisinnovation, as an alternative I was thinking of Amarock, but I want to know why Rythmbox is not working.

---

### Post by Arrgoss on 2008-02-23
> **Moop said:**
> Do you have the w64 codecs package installed?
I'm sorry for this question, I'm a newby, but how do I check? And, if not, how do I install them?
Linuxisinnovation, as an alternative I was thinking of Amarock, but I want to know why Rythmbox is not 

EDIT:
I installed the w64 codecs using Synaptics, but still the problem remains.

---

### Post by divindavid on 2008-02-23
i think you are adding music wrong (correct me if i am wrong) Music-import file or folder than find you music it may ask you that you dont have the propper codec to play mp3s but it will promped you how to get the mp3 codec (thats what happened to me)

rythmbox is way better than all of the other jukboxes out there and it is really low on system resourses

---

### Post by sayakb on 2008-02-23
> **Arrgoss said:**
> I'm sorry for this question, I'm a newby, but how do I check? And, if not, how do I install them?
Linuxisinnovation, as an alternative I was thinking of Amarock, but I want to know why Rythmbox is not 

EDIT:
I installed the w64 codecs using Synaptics, but still the problem remains.

Amarok is excellent, but its a bit laggy with Ubuntu (NOT kubuntu).. Also, it crashes sometimes on gnome..

---

### Post by Arrgoss on 2008-02-23
> **divindavid said:**
> i think you are adding music wrong (correct me if i am wrong) 


I just use the Music-->Import file/folder. Then choose the file and nothing happens in the Rythmbox :confused:


> **divindavid said:**
> rythmbox is way better than all of the other jukboxes out there and it is really low on system resourses

Another reason to solve this problem.

---

### Post by Arrgoss on 2008-02-24
No one out there who could help me with the Rythmbox :(?

---

### Post by zvacet on 2008-02-24
```
sudo apt-get install ubuntu-restricted-extras
```

That should give you plugins,flash,java.......

---

### Post by Arrgoss on 2008-02-24
That helped, thanks zvacet!

---

