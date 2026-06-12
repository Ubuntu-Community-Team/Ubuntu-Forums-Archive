---
title: "Xubuntu MP3 Audio Ripper"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-10
I'd like to put some of my CD's onto my Laptop and I'm looking for
a CD Ripper that works on XFCE.  My Laptop is only 400mhz with 192 megs
so it can really run Gnome or KDE without a huge Performance hit.

I just installed Xubuntu onto it and it's still slow.

I'd like Mp3 format so after I install what ever you suggest
will I need any codes or anything?

Thanks.

---

### Post by diatribe on 2007-09-10
sound juicer is prolly your best bet, in the repos

check this thread also:  [http://ubuntuforums.org/archive/index.php/t-429884.html](http://ubuntuforums.org/archive/index.php/t-429884.html)

---

### Post by Orbital75 on 2007-09-10
If I install Sound Juicer want it install Gnome or KDE?
I thought it needed those Library's to run?
Also I'm thinking Sound Juicer only does .ogg, right?

Someone told me that RipperX is good but when I search
in Synaptic nothing comes up.

---

### Post by diatribe on 2007-09-10
it won't install gnome, it will install gnome libraries, they are two different things.  and I think the package is called ripper

---

### Post by x1a4 on 2007-09-10
ripperx is a good, light-weight, GTK audio cd ripper/encoder.  

On another note, if your computer runs slow even with Xfce, use one of the many light-weight GUIs.  AfterStep is quite nice, as are fvwm-crystal, OpenBox, FluxBox, WindowMaker.

---

### Post by Orbital75 on 2007-09-10
Yeah, XFCE may be a little to much for it to run Smooth and not take 15 seconds to
open a window.

I Downloaded both RipperX and Sound Juicer.

**RipperX: ** I opened the Gui up and choose Config.
for some reason, my changes won't save.
I have choose a folder in my Home to save to
but RipperX won't save my changes.

**Sound Juicer**: I don't see how to Rip to Mp3
It only has ogg, Flac, and wav

Sound Juicer takes 6 minutes a song.

---

### Post by picpak on 2007-09-10
I rip my CDs with Grip, along with [this guide](http://ubuntuforums.org/showthread.php?t=183125).

Hope that helps!

---

### Post by Orbital75 on 2007-09-10
I searched for Lame but it says that its known by another package
but doesn't give me the name.

---

### Post by nonewmsgs on 2007-09-10
> **Orbital75 said:**
> I searched for Lame but it says that its known by another package
but doesn't give me the name.

sudo apt-get install lame doesnt work?

---

### Post by Orbital75 on 2007-09-10
nope..... I think it's called libmp3lame.su or something?
I think this may have something with me using Xubuntu 6.06 LTS
my Laptop won't run anything else. I have all the repositories
enabled.

```
Package lame is not available, but is referred to by another
package. This may mean that the package is missing, had been
obsoleted, or is only available from another source.


```

---

### Post by ChillMonkey on 2007-09-19
> **Orbital75 said:**
> 

**Sound Juicer**: I don't see how to Rip to Mp3
It only has ogg, Flac, and wav

Sound Juicer takes 6 minutes a song.

i use fvwm on a powerbook g4, SoundJuicer works nicely for me.

to get mp3 you need to install the lame pluging for gstreamer.

for feisty this worked:

```
sudo apt-get install -y gstreamer0.10-plugins-ugly-multiverse
```

mp3 will be an option then.
of course multiverse repository has to be enable.

---

### Post by andrew.46 on 2007-09-20
Hi,

 For a low-end system the best solution is the command-line abcde. There is a small walkthrough at:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 I see you are having trouble getting lame. It is _definitely_ in the repositories:

```
andrew@ilium:~$ apt-cache search lame | grep Encoder
lame - LAME Ain't an MP3 Encoder
lame-extras - LAME Ain't an MP3 Encoder
liblame-dev - LAME Ain't an MP3 Encoder
liblame0 - LAME Ain't an MP3 Encoder

```

 Check your sources.list, you must be missing the required one.

                   Andrew

---

