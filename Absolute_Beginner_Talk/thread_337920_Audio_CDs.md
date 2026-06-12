---
title: "Audio CDs"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by houseisland on 2007-01-13
Hi,

Can anyone point to any good links for help with burning audio CDs.

Serpentine works well with MP3 to WAV coversion but it has no options for closing the CD thus limiting the use of the CD pretty much to PCs.

K3B looks sweet.  But attempts to create audio CDs from MP3s generate an error message saying that the MP3 format is not supported.  Is there some sort of config required here that I am missing.

Thanks.

---

### Post by ComplexNumber on 2007-01-13
> **houseisland said:**
> Hi,

Can anyone point to any good links for help with burning audio CDs.

Serpentine works well with MP3 to WAV coversion but it has no options for closing the CD thus limiting the use of the CD pretty much to PCs.

K3B looks sweet.  But attempts to create audio CDs from MP3s generate an error message saying that the MP3 format is not supported.  Is there some sort of config required here that I am missing.

Thanks.
use gnomebaker. its qute intuitive, so a tutorial isn't necessary.

---

### Post by houseisland on 2007-01-14
> **ComplexNumber said:**
> use gnomebaker. its qute intuitive, so a tutorial isn't necessary.

Gnomebaker didn't work at all.  But that was before the installation of various codecs and lame.

I will go back and have another look.

I am not adverse to learning and am not afraid of tutorials, so don't anyone be shy here.

;)

---

### Post by deadgobby on 2007-01-14
Here is some on line tutorials.
[http://www.linuxreality.com/](http://www.linuxreality.com/)
[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)
[http://ubuntuforums.org/showthread.php?t=99115&highlight=grip](http://ubuntuforums.org/showthread.php?t=99115&highlight=grip)
[http://www.quickones.org](http://www.quickones.org)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
I am sure there is more.
Gobby

---

### Post by houseisland on 2007-01-14
> **ComplexNumber said:**
> use gnomebaker. its qute intuitive, so a tutorial isn't necessary.

No go with Gnomebaker.  Error message with MP3s.  Missing plugin.

:-?

---

### Post by Marsolin on 2007-01-15
You need to install [LAME]("http://linuxappfinder.com/package/lame").  It's in the multiverse repository.  Once you install that then MP3's will be able to be played and [K3b]("http://linuxappfinder.com/package/k3b") won't give you the error any more.

---

### Post by houseisland on 2007-01-16
> **Marsolin said:**
> You need to install [LAME]("http://linuxappfinder.com/package/lame").  It's in the multiverse repository.  Once you install that then MP3's will be able to be played and [K3b]("http://linuxappfinder.com/package/k3b") won't give you the error any more.

Hi.  

Thanks.  

Lame is installed. I can play MP3s.  I can extract MP3 files from WAV files.  I can burn audio CDs with Serpentine, converting MP3s to WAV files in the process, but Serpentine appears not to close the CD.  Neither Gnomebaker of K3b will handle MP3s, though. 

Confused.

:-?

---

### Post by Fitzy_oz on 2007-01-16
> **houseisland said:**
> Hi.  

Thanks.  

Lame is installed. I can play MP3s.  I can extract MP3 files from WAV files.  I can burn audio CDs with Serpentine, converting MP3s to WAV files in the process, but Serpentine appears not to close the CD.  Neither Gnomebaker of K3b will handle MP3s, though. 

Confused.

:-?

That's odd mate,
I use K3b for all my audio cooking duties and it handles MP3's just fine.  There should be a plugin in the repositories for mp3 support in K3b, it's should be called libk3bmp3 or something similar.  Do a search for it in synaptic and it should show up.  Heres my config page for k3b with all the plugins I have installed

---

### Post by houseisland on 2007-01-18
> **Fitzy_oz said:**
> That's odd mate,
I use K3b for all my audio cooking duties and it handles MP3's just fine.  There should be a plugin in the repositories for mp3 support in K3b, it's should be called libk3bmp3 or something similar.  Do a search for it in synaptic and it should show up.  Heres my config page for k3b with all the plugins I have installed

:cool: 

It is working.  Its effectiveness varies with different playback devices, but it does work.  Thank you.

:D

---

### Post by mcduck on 2007-01-18
Gnomebaker uses Gstreamer 0.8-plugins, not 0.10 like most programs in Ubuntu. After installing all Gstreamer 0.8 plugins it burns audio-cd's from mp3-files just fine. ;)

---

### Post by houseisland on 2007-01-18
> **mcduck said:**
> Gnomebaker uses Gstreamer 0.8-plugins, not 0.10 like most programs in Ubuntu. After installing all Gstreamer 0.8 plugins it burns audio-cd's from mp3-files just fine. ;)

:cool: 

Thanks.  I will try this as well.

:D

---

