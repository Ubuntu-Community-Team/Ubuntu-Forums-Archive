---
title: "soundkonverter help"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2007-08-04
hi there

i am in feisty for some hours now and i want to rip my cd's to mp3 files. i installed soundkonverter but the only output extension i am able to create is wav.. can anyone help me here? i want to create mp3 files from a CD source..

i am a noob in linux so be patient with me please.. thanks in advance for all of you.

---

### Post by Aurdal on 2007-08-04
You can rip your disk with Sound Juicer CD Extractor, you can find it in Applications > Sound & Video > Sound Juicer CD Extractor. If you want it to save as mp3 files you need to go into the preferences and change the output format.

---

### Post by cmaranhao on 2007-08-04
i already looked into sound juicer but i don't like the overall look of it.. besides, it also didn't support mp3 files.

that's why i searched for other applications.. i really like the look of soundkonverter but also the mp3 support is missing :(

---

### Post by Aurdal on 2007-08-04
If it didn't support mp3 files you'll need to install the multimedia codecs. Take a look here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by cmaranhao on 2007-08-04
thanks for that link :)

i installed this:

sudo apt-get install ubuntu-restricted-extras

but i still don't have support for the mp3 file under soundkonverter. i know i must be missing some basic step but i don't know that much about this :(

can you give me further help?

---

### Post by Aurdal on 2007-08-04
```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs
```

That should take care of your problem, you'll also need to restart the ripping application afterwards (if you have it open that is..). :)

---

### Post by cmaranhao on 2007-08-04
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

still not working :(

---

### Post by Aurdal on 2007-08-04
try "sudo apt-get install soundconverter" it's another program, it doesn't look the same, but at least it works. (for me at least [I couldn't get soundkonverter functioning properly]) :)

---

### Post by cmaranhao on 2007-08-05
isn't there a way to use soundkonverter instead of that one? i really like its layout..

---

### Post by cmaranhao on 2007-08-05
bump

---

### Post by cmaranhao on 2007-08-05
bump

---

### Post by cmaranhao on 2007-08-05
no one uses SK?

---

### Post by cmaranhao on 2007-08-05
bump

---

### Post by cmaranhao on 2007-08-06
bump

---

### Post by sbazin on 2007-08-06
I used to use soundkonverter but I ran into the same problem you have so I've since found a much easier way to rip CDs to MP3 using Konqueror instead.  Simply insert an audio CD in your CD drive and type " audiocd:/ " in Konqueror's address bar.  There is be a folder there called MP3.  You just have to copy the files from this folder to the desired location on your computer and the CD will be automatically ripped in MP3 format.
Hope this helps

---

### Post by bluenova on 2007-08-27
sudo aptitude install lame lame-extras

That'll give you mp3 support in soundKonverter

---

### Post by cmaranhao on 2007-09-03
> **sbazin said:**
> I used to use soundkonverter but I ran into the same problem you have so I've since found a much easier way to rip CDs to MP3 using Konqueror instead.  Simply insert an audio CD in your CD drive and type " audiocd:/ " in Konqueror's address bar.  There is be a folder there called MP3.  You just have to copy the files from this folder to the desired location on your computer and the CD will be automatically ripped in MP3 format.
Hope this helps

thanks for the effort but i prefer soundkonverter.. i will keep trying, if nothing else works i will look into it.

> **bluenova said:**
> sudo aptitude install lame lame-extras

That'll give you mp3 support in soundKonverter

in output i only have wave format as a supported file and i already did what you said...

---

### Post by gsanders99 on 2007-12-08
I was having the same problem, but was able to get MP3 encoding working by installing Lame.

I used KMenu-System-Adept Manager, searched for Lame, selected lame, lame-extras, and liblame for installation then hit Apply changes.

When I opened Soundkonverter again, the MP3 stuff worked.

I'm using Gutsy.

---

### Post by Ron F. on 2007-12-14
In addition to lame, I recommend you also install ffmpeg - (soundKonverter does not use gstreamer,) mp3gain, and faac - (if you also want to encode aac at some point.) I use the ogg format, and if you want that, install vorbis-tools. I hesitate to recommend faad, as I am having trouble with it.

Restart soundKonverter.

-Ron

---

