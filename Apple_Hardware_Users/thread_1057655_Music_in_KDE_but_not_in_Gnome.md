---
title: "Music in KDE but not in Gnome"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by kduclos on 2009-02-02
I am having a problem playing music in Gnome. I keep my music in a folder on my MacOSX partition, and I set up Rhythmbox to look for the music there. I haven't been able to play any music. When I try to play music stored on my Ubuntu partition, I can play it with no problems.
The weird thing is that it works fine in KDE but not at all in Gnome. I have also tried several other music programs with the same result.
Any suggestions would be greatly appreciated.

---

### Post by sookun on 2009-02-02
Ubuntu doesnt ships with the mp3 etc plugins, just go to applications, add/remove  type gstreamer  and download them, there is for music and video and one i recently foun for .wav formats i fink.
enjoy!

---

### Post by kduclos on 2009-02-02
Thanks, sookun. I have the gstreamer plugins installed, but it still doesn't work. I can play mp3s, just not from my MacOSX partition.

---

### Post by cyberdork33 on 2009-02-02
I don't know why KDE and gnome would treat them differently... can you browse to them and copy them to your local desktop? (testing permissions)

---

### Post by kduclos on 2009-02-04
I tried copying music to my desktop, and that worked fine.

---

### Post by cyberdork33 on 2009-02-04
hmm.. it would seem that is something to do with how you are accessing the files on the HFS+ partition. How are you getting access to the OSX files?

---

### Post by kduclos on 2009-02-04
My OSX partition mounts whenever I log in. I just select the folder in RhymthmBox and set it as my music library.

---

### Post by mfox on 2009-02-05
Could it be a permissions problem on the Mac side?  Perhaps you don't have the file sharing permissions enabled.

---

### Post by kduclos on 2009-02-05
I'm not using file sharing. The files are on a different partition on the same hard drive. Do I need to copy the files to my Ubuntu partition? It seems like it should work the way it is.

---

### Post by cyberdork33 on 2009-02-05
> **kduclos said:**
> I'm not using file sharing. The files are on a different partition on the same hard drive. Do I need to copy the files to my Ubuntu partition? It seems like it should work the way it is.
I would say that it is trying to write some library file or something to the HFS+ partition which is not working because of permissions or journaling. try a simple player like audacious and see if you have the same problem.

---

### Post by kduclos on 2009-02-16
That seemed to fix the problem. Strangely enough, Audacious seems to work in Gnome but not KDE. I guess the solution is to use Audacious in Gnome and Rhythmbox in KDE. Thank you for your help.

---

