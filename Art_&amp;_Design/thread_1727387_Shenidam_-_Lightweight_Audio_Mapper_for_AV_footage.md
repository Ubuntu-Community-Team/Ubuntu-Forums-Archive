---
title: "Shenidam - Lightweight Audio Mapper for AV footage"
date: 2011-04-12
forum: Art &amp; Design
---

### Post by NabilS on 2011-04-12
I am publicizing shenidam, which is a piece of software I wrote:

[http://www.shenidam.org/](http://www.shenidam.org/)

What does it do? It allows to map audio from a good quality source to that of a bad quality source (typically taken from a video camera/DSLR) in order to replace the actual audio from the video. It is an alternative to DualEyes from Singular Software, which is not open source, is ridiculously expensive and does not take into account all the formats/codecs of ffmpeg PyQt as mine does. I do not know about comparing performance (I never tried DualEyes, only looked at their demo video), but, according to my benchmarks, in some cases, can map the footage correctly even with a synthetic noisy track (AWGN) of a standard deviation of 80 (that's right, the noise in 80 times stronger than the signal). Note: It is NOT a denoising application, it's an audio mapper/auto replacer.

Please try it out.

---

### Post by nwistbac on 2011-12-05
> **NabilS said:**
> I am publicizing shenidam, which is a piece of software I wrote:

[http://www.shenidam.org/](http://www.shenidam.org/)

What does it do? It allows to map audio from a good quality source to that of a bad quality source (typically taken from a video camera/DSLR) in order to replace the actual audio from the video. It is an alternative to DualEyes from Singular Software, which is not open source, is ridiculously expensive and does not take into account all the formats/codecs of ffmpeg PyQt as mine does. I do not know about comparing performance (I never tried DualEyes, only looked at their demo video), but, according to my benchmarks, in some cases, can map the footage correctly even with a synthetic noisy track (AWGN) of a standard deviation of 80 (that's right, the noise in 80 times stronger than the signal). Note: It is NOT a denoising application, it's an audio mapper/auto replacer.

Please try it out.

Is this program also able to handle correction of different recording-speeds as DualEyes does? The problem for most DSLR users is that the DSLR records in a time-speed for film that is 23,95 fps, while most recorders records for virtually 24 fps. If i put the audiofile on top of the film in say Adobe Premiere the tracks will be matched in the beginning, but after a while they will differ.

DualEyes can map and make corrections for this kind of problem. Does Shenidam do the same?

Is Shenidam going to be released for Windows? It would be awesome to have it for Windows aswell (and perhaps even for Mac) as I am mainly a Windows-user.

Best Regards

---

### Post by NabilS on 2011-12-05
Shenidam works based on the audio track only, where there is such thing as frames (so 24 and 23.95 don't  even exist (notions of samplerate do however, and are handled properly with resampling). So there is no such thing as a 24fps audio recorder. Shenidam gives you as output audio streams (optionally remixed with the original video stream), and the latest shenidam-av can give you a mapping in   samples (not frames - based on the base track's sample rate) between tracks and a base track (so for now we need to convert to frames "by hand" - I use libreoffice calc for that). 

As for windows, it should work with a few tweaks in the buildfile.

---

### Post by nwistbac on 2012-04-16
> **NabilS said:**
> Shenidam works based on the audio track only, where there is such thing as frames (so 24 and 23.95 don't  even exist (notions of samplerate do however, and are handled properly with resampling). So there is no such thing as a 24fps audio recorder. Shenidam gives you as output audio streams (optionally remixed with the original video stream), and the latest shenidam-av can give you a mapping in   samples (not frames - based on the base track's sample rate) between tracks and a base track (so for now we need to convert to frames "by hand" - I use libreoffice calc for that). 

As for windows, it should work with a few tweaks in the buildfile.

Sorry if this may sound like a really stupid question, but I'm a total noob to the Linux world (I only have linux because there are some free open source programs, Like Shenidam, that I MIGHT need).

The question is: I run Fedora 13. Will I be able to install shenidam on that, or do I need Ubuntu for it?

As I said: I'm totally noob and do not understand anything about OS-compabilities when it goes down to code-level.

Kind Regards

---

### Post by NabilS on 2012-04-18
Concerning Platform X (in the case Fedora), it should work, however it might require a few tweaks in the build file.

---

