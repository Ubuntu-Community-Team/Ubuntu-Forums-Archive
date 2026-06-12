---
title: "Music player &amp; ipod"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by paulgroovy on 2005-12-26
Hi, I'm new to these boards and new to linux.  I'm currently running Breezy Badger on an HP notebook with a P3 processor.

Anyhow, I've been trying  to load the music from my compact discs onto my computer so I could (when I get one) load them onto an ipod, and also have it play continuously on my computer.  I've been using banshee but it's just messing everything up.  It will rip a cd onto the playlist, and then when I rip the next cd it will lose a song from the first cd.  It's quite infuriating actually.  Is there another program that I can use for organizing my music now, and then loading it onto an ipod later.

Thanks

---

### Post by endersshadow on 2005-12-26
Use Sound Juicer to rip the CDs, and then gtkpod to load them up onto the iPod.  Sound Juicer is in the Applications -> Sound & Video menu, as it is installed by default in Ubuntu.

If you have an iPod video, you'll need to compile gtkpod from source, but if you have another type of iPod:

```
sudo apt-get install gtkpod
```

That code will work perfectly and get you the GUI to load up your songs onto your iPod :-D

---

### Post by paulgroovy on 2005-12-26
thanks Mr. Shadow,

I just loaded gtkpod from the repos yesterday.  Is it any good for orangizing and playing the music on the computer?

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=paulgroovy]thanks Mr. Shadow,

I just loaded gtkpod from the repos yesterday.  Is it any good for orangizing and playing the music on the computer?[/QUOTE]

Its not a "be all app" like iTunes. Only thing like that for Linux is Amarok:

```
sudo apt-get install amarok
```

That command installs it.

---

### Post by cstudent on 2005-12-27
Sound juicer doesn't rip in .mp3 or aac formats. It does ogg and flac. I just got a new ipod for Christmas and it does not play ogg or flac. I use Goobox to rip my CD's. I have the mp3 codecs installed and I rip my tunes in mp3. However, I'm currently using iTunes in XP on my notebook to load my ipod.

---

### Post by mcduck on 2005-12-27
Grip is a nice ripper that supports multiple encoders and cdparanoia. I'm not sure if it does .aac, but .mp3 for sure.

[http://nostatic.org/grip/]("http://nostatic.org/grip/")

---

### Post by endersshadow on 2005-12-27
[QUOTE=cstudent]Sound juicer doesn't rip in .mp3 or aac formats. It does ogg and flac. I just got a new ipod for Christmas and it does not play ogg or flac. I use Goobox to rip my CD's. I have the mp3 codecs installed and I rip my tunes in mp3. However, I'm currently using iTunes in XP on my notebook to load my ipod.[/QUOTE]

That is false, you can rip to mp3 format using Sound Juicer.  You just needed to add it:

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

---

### Post by cstudent on 2005-12-27
[QUOTE=endersshadow]That is false, you can rip to mp3 format using Sound Juicer.  You just needed to add it:

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)[/QUOTE]


Thanks for correcting me and thanks for the link. I'm going to give it a try tonight.

---

### Post by endersshadow on 2005-12-27
[QUOTE=cstudent]Thanks for correcting me and thanks for the link. I'm going to give it a try tonight.[/QUOTE]

You're welcome, and it works very well.

Just as a tip, though: Do not try to convert OGG to MP3...if you go from one Lossy to another, you're going to get *really* bad quality...

---

