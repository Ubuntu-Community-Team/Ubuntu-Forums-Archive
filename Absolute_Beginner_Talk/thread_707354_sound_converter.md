---
title: "sound converter"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Dieselguts on 2008-02-25
i need a sound converter for linux that will convert MP3 and WMA, I have tried sound converter and soundkonverter but neither seem to work any thoughts?:-k

---

### Post by SOULRiDER on 2008-02-25
What exactly did you need to convert? Did you make sure you had the necesary encoding libraries?

---

### Post by northern lights on 2008-02-25
I'd recommend audacity. It should be in Synaptic, if you have universe repositories enabled. Alternatively, run ```
sudo apt-get install audacity
```
Open a .wma, choose "Export" from the "File" menu and save as .mp3
Done.

[EDIT]
You can play .mp3s in the first place, right?!
Otherwise, run ```
sudo apt-get install ubuntu-restricted-extras
```
[/EDIT]

---

### Post by Dieselguts on 2008-02-25
i need to convert WMA into MP3 but on sound converter, i get an error message saying GStreamer encountered an internal system error. i don't know why

---

### Post by SOULRiDER on 2008-02-25
Are the WMA files DRMed ?

---

### Post by Syndacate on 2008-02-25
use **Fuoco Tools**.  It's a new proejct since the creator dropped his old one, ConvertIT, and I hold that **** like the holy grail, it's one of the best tools I use and I use it almost daily.

Video, sound, pictures, whatever, it can convert them all.

Assuming you're using gutsy:

Add the reposatory:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Add the GPG Key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install the programs neede to Back Fuoco Tools
```
sudo apt-get install ffmpeg2theora mencoder mplayer  libogg0 libogg-dev libvorbis0a libvorbis-dev vorbis-tools mp32ogg ffmpeg  imagemagick youtube-dl poppler-utils dvdauthor sox mjpegtools ffmpeg toolame gddrescue dvdbackup ccd2iso nrg2iso mdf2iso bchunk transcode k3b kipi-plugins kommander xterm
```

From there you have choice, I recommend the GUI because I love it.

That would be:
[http://www.mediafire.com/?1ymmqtz9sdg](http://www.mediafire.com/?1ymmqtz9sdg)

Download it to your desktop, extract the tar.gz into a folder on your desktop.

in terminal type:
```

cd Desktop/Created_Folder
sudo ./install.sh

```

Replacing "Created_Folder" with the one that you extracted the .tar.gz you downloaded into.

That should be all.

Source:
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

Double thumbups to one of the best programs I've ever used.

---

### Post by Bungo Pony on 2008-02-25
Sound Converter is actually the *only* Linux conversion utility I've successfully used. Unfortunately, it lacks flexibility.

For my MP3 conversion needs, I usually use EAC running in Wine to make MP3s. I'm not sure if it supports WMA files though.

---

### Post by TE7 on 2008-02-26
I installed wine and EAC, but in the EAC setup it says it's searching for lame on the C drive, but just sits there. I downloaded the tar for lame, but I don't know how and where to use the configure and make commands. Can anyone help me with this? Thanks in advance for any help.

---

