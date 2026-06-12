---
title: "How can I get RhythmBox to play RealAudio .rmj files?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-06-03
I'm running 6.10 and want to play my RealAudio (.rmj) music files.

When I try to open a .rmj file Rhytmbox gives Error Message:
The GStreamer plugins to decode "Unknown" files cannot be found

What do I need to do to get RhythmBox to play these files?
Thanks for any help you can offer.
KiwiPete

---

### Post by KiwiPete on 2007-06-06
Bump

---

### Post by GTvulse on 2007-06-06
The gstreamer0-10-pitfdll plug in and the win32codecs all bundle from the mplayerhq website. No there is no .deb for the all package; either you build it using fhe debdiffs from debian-multimedia.org or install it by hand by copying them to /usr/lib/codecs and making a /usr/lib/win32 symbolic link for the sake of old applications that may look for the files there..

---

### Post by mcduck on 2007-06-06
> **dradul said:**
> The gstreamer0-10-pitfdll plug in and the win32codecs all bundle from the mplayerhq website. No there is no .deb for the all package; either you build it using fhe debdiffs from debian-multimedia.org or install it by hand by copying them to /usr/lib/codecs and making a /usr/lib/win32 symbolic link for the sake of old applications that may look for the files there..

yes, there is a .deb available. Just get it from Medibuntu: [http://medibuntu.sos-sts.com/]("http://medibuntu.sos-sts.com/")

Easiest way is to follow instructions on their page to add medibuntu repository, and then just get the packages with apt-get/Synaptic.

---

### Post by GTvulse on 2007-06-06
[quote=mcduck]
yes, there is a .deb available. Just get it from Medibuntu: [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)
[/quote]

Looking at the size of the deb in their pool directories, yes, it is a package of the all win32 codecs pack.

---

### Post by KiwiPete on 2007-06-07
Thanks for the advice.
I have installed the medibuntu repositories as instructed on their site, but the rmj (RealAudio) files still will not play in either Rythbox or Amarok. Wma and .mp3 files will play, but not .rmj files
Any other suggestions...?

---

### Post by KiwiPete on 2007-06-14
Can anyone help with this?

---

### Post by FuturePilot on 2007-06-14
It sounds like you just added the repositories. Did you install the W32 codecs?

---

### Post by KiwiPete on 2007-06-14
How do I install the codecs you refer to?
I understood from previous posts that the codecs were included in the Medibuntu package.
How can I check?

---

### Post by mcduck on 2007-06-14
> **KiwiPete said:**
> How do I install the codecs you refer to?
I understood from previous posts that the codecs were included in the Medibuntu package.
How can I check?

Medibuntu is not a package, it's a 3rd party repository that provides lots of media-related packages that are not available in Ubuntu's official repositories.

Just use the link in my previous post, and follow their instructions how to add the repository. After that you can just find the w32codecs package with Synaptic, or run 'sudo apt-get install w32codecs' in a terminal.

---

### Post by KiwiPete on 2007-06-14
Thanks for the advice McDuck.

I have already followed instructions on the Medibuntu site and used apt-get for Win32 codecs.
they are all installed, but still neither of my music players (Amarok and RhythmBox) will play RealAudio .ra or .rmj audio files.

Any other suggestions from anyone?

kiwiPete

---

### Post by mcduck on 2007-06-14
Do you have gstreamer0.10-pitfdll installed? You probably need that to get Rhythmbox understand those windows codecs.

---

### Post by KiwiPete on 2007-06-14
Yes gstreamer0.10-pitfdll is installed

---

### Post by KiwiPete on 2007-06-18
Any other ideas anyone?

---

### Post by dutch1918 on 2007-06-19
> **mcduck said:**
> Medibuntu is not a package, it's a 3rd party repository that provides lots of media-related packages that are not available in Ubuntu's official repositories.

Just use the link in my previous post, and follow their instructions how to add the repository. After that you can just find the w32codecs package with Synaptic, or run 'sudo apt-get install w32codecs' in a terminal.

[http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) is now [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by olvlo on 2008-04-29
I believe that what has failed to be said is that once you install the aforementioned codecs, you'll be able to play the .rmj files with MPlayer; at least, that's what has happened in my case: no luck with Rhythmbox or XMMS, only with MPlayer. Hope it helps...

---

