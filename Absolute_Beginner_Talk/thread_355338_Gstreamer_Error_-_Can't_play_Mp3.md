---
title: "Gstreamer Error - Can't play Mp3"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-02-07
Hey.. 

When i try to play mp3s, i get the error:

```
The GStreamer plugins to decode "MP3" files cannot be found 
```

Help?..

---

### Post by etank on 2007-02-07
Take a look at this page. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats). MP3 playback is disabled in a default install of Ubuntu.

---

### Post by cmol on 2007-02-07
I fixed the problem..
I installed Amarok...

:-)

---

### Post by etank on 2007-02-07
Just my .02 but if you use Gnome then you may like [Exaile Media Player]("http://www.exaile.org/trac").

---

### Post by paulozzzz on 2007-02-07
> **cmol said:**
> I fixed the problem..
I installed Amarok...

:-)

I did the same thing, but...:( 

It says "media not playable" for all my MP3 files.

What am I might be doing wrong?:confused:

---

### Post by paulozzzz on 2007-02-08
Does somene have a clue?

---

### Post by NicePics13 on 2007-02-08
(*I'm testing Ubuntu 7.04 so the packages might have a slightly different name in 6.10*)

Download the following packages via Synaptic (or apt-get)
[B]libmad0
libfaad2-0
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
[/B]
Those will enable playback of different media formats, open and closed source. You could also try the **gstreamer0.10-plugins-bad** packages for even more formats even if it's not 100% recommended.
Amarok is nice, but more a thing for Kubuntu. Try Banshee, Listen or Exaile :)

---

### Post by AndyCooll on 2007-02-08
> **NicePics13 said:**
> (*I'm testing Ubuntu 7.04 so the packages might have a slightly different name in 6.10*)

Download the following packages via Synaptic (or apt-get)
[B]libmad0
libfaad2-0
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
[/B]
Those will enable playback of different media formats, open and closed source. You could also try the **gstreamer0.10-plugins-bad** packages for even more formats even if it's not 100% recommended.
Amarok is nice, but more a thing for Kubuntu. Try Banshee, Listen or Exaile :)

Ignore that last comment. Amarok is good with Ubuntu too. While it is true that Amarok is a KDE app, it works perfectly ok with the GNOME desktop environment. 

I prefer the default GNOME setup but none of those GNOME based music players are as good as Amarok IMHO. But then that's the beauty of Linux ...you have choice and can pick the one most suited to you.

Have a look at the "Restricted Formats" link in my signature (the same one already posted in this thread), that shows you how to install all the relevent codecs to play your audio files.

:cool:

---

### Post by NicePics13 on 2007-02-08
AndyCooll is right, Amarok depends on the KDE libraries but is perfectly usable in Gnome 8-)

---

### Post by paulozzzz on 2007-02-08
> **NicePics13 said:**
> (*I'm testing Ubuntu 7.04 so the packages might have a slightly different name in 6.10*)

Download the following packages via Synaptic (or apt-get)
[B]libmad0
libfaad2-0
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
[/B]
Those will enable playback of different media formats, open and closed source. You could also try the **gstreamer0.10-plugins-bad** packages for even more formats even if it's not 100% recommended.
Amarok is nice, but more a thing for Kubuntu. Try Banshee, Listen or Exaile :)

Mine is 5.10.  I'll try to find the matching packages.  I'll try them as soon as I reboot and load Linux.  Thanks for the help.  I'll report back as soon as I get the results.

:guitar:

---

### Post by paulozzzz on 2007-02-08
> **AndyCooll said:**
> Ignore that last comment. Amarok is good with Ubuntu too. While it is true that Amarok is a KDE app, it works perfectly ok with the GNOME desktop environment. 

I prefer the default GNOME setup but none of those GNOME based music players are as good as Amarok IMHO. But then that's the beauty of Linux ...you have choice and can pick the one most suited to you.

Have a look at the "Restricted Formats" link in my signature (the same one already posted in this thread), that shows you how to install all the relevent codecs to play your audio files.

:cool:

I'll try those too.  Thanks!  :)

---

### Post by paulozzzz on 2007-02-08
> **NicePics13 said:**
> (*I'm testing Ubuntu 7.04 so the packages might have a slightly different name in 6.10*)

Download the following packages via Synaptic (or apt-get)
[B]libmad0
libfaad2-0
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
[/B]
Those will enable playback of different media formats, open and closed source. You could also try the **gstreamer0.10-plugins-bad** packages for even more formats even if it's not 100% recommended.
Amarok is nice, but more a thing for Kubuntu. Try Banshee, Listen or Exaile :)

NicePics,

from those cited, the following I could not find:

[B]libfaad2-0
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
[/B]

But with the remaining two it was possible to play the MP3 files.  Thanks a lot!

:guitar:

---

### Post by paulozzzz on 2007-02-08
Of course in my older Ubuntu version the names of the gstreamer's packages are

**gstreamer[COLOR="Red"]0.8[/COLOR]-plugins-good** instead of **gstreamer[COLOR="Red"]0.10[/COLOR]-plugins-good**, for instance.

---

### Post by NicePics13 on 2007-02-08
Yeah, you have an older Ubuntu version so just ignore my package version numbers :)

---

### Post by paulozzzz on 2007-02-09
\\:d/

---

