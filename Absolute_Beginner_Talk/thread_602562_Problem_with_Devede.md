---
title: "Problem with Devede"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by stueycaster on 2007-11-04
I'm trying to encode an avi file with Devede. I'm pretty sure the avi is good because I tried it out in Windows and it worked fine.  While setting it up it says the finished product will be about 3.5 gigabytes. When it's finished it ends up being only 1.6 gigs. I followed some pretty explicit directions about using Devede and I think I got it right. Then if I burn it to a disk it plays sound but no video in the computer. If I put it in the home DVD player it says the disk is bad.

I got the W64 DVD Codecs and the Restricted Multimedia codecs with Automatix. I got the Medibuntu Repository and I have all the repos in Synaptic activated. Right after I got Medibuntu My computer updated and got a bunch of other codecs. I don't know what else I need to get.

Please be advised that I am a complete newby to Ubuntu. If I need to use commands i really need to be told everything right from the start.

---

### Post by borovy3488 on 2007-11-04
which version of DeVeDe do you have?  Also, how are you trying to encode the video?  What steps are you taking?  Here's a quick step-by-step::

1) When it starts, click Video DVD.
2) Then click add files on the right side.
3) Navigate to the .avi file and select it.
4) Make sure on the "Output Video Format" section you have selected the correct format.  NTSC in America.
5) Then, select to make a preview.  Just to make sure the encoding will work.
6) Watch the preview, and if that video is ok, then click the "OK" button.
7) On the "Action" menu, make sure the "Create an ISO or BIN/CUE image, ready for burning" option is selected.  
8) From here, you can just click "Forward" and it will make an ISO where ever you tell it to.
9 (optional)) If you have a newer version of DeVeDe, you can make a menu as well.

---

### Post by bumanie on 2007-11-04
I have never had any problems with devede once the sound problem (in feisty) was sorted out by a 'fix'. Maybe you have not selected the correct output for your country ie PAL or NTSC. I have found it will encode anything I have tried so far, including rmvb files. Which ubuntu are you using? Did you get devede from synaptic or from the devede website?

---

### Post by stueycaster on 2007-11-04
I guess I might have been wrong about the problem being with Devede. I burned a file made with Devede through Windows using Nero and it worked. I've tried Brasero and Gnomebaker and both of them failed.

Also is it normal for Devede to compress it into such a small file. Won't video quality degrade if it is compressed. I encoded this same avi on windows and it came out a 4.4 gb file. With Devede it comes out to 1.6 gb.

---

### Post by digger95 on 2007-11-06
I have the exact same issue.  The dvd structure it creates only totals 1.5gb.  I set my bitrate and other settings correctly, and before the encoding starts devede reports that it will use about 4.3 gigabyte on the dvd.  But when it's finished encoding, there are only two vob files created, one is about 1gb in size, the other 512 mb.   The whole movie is there in the two files, but there's no way a two-hour movie should take up only 1.5gb of space on a dvd.  I encoded the same avi file with convertxtodvd under wine, and the output used the entire dvd.

---

### Post by bumanie on 2007-11-06
I am unsure what the compression ratio of devede is, however, consider divx and xvid, they compress a dvd to vcd with virtually no loss of video quality. However as much I dislike M$, look at wmv fromat, it also compresses video files well. 
At the end of the day, if you are happy with the final quality output from devede, does it really matter how much it has been compressed? You may be able to fit two movies onto one disc!

---

### Post by digger95 on 2007-11-06
> **bumanie said:**
> At the end of the day, if you are happy with the final quality output from devede, does it really matter how much it has been compressed? You may be able to fit two movies onto one disc!
Well that's the thing.  The quality is not very good.  I encoded the same movie with convertxtodvd, which is very conservative with its bitrate.  It will usually only apply just what it needed to get full quality, and no more.  Often I get movies of 3gb or so.  But never 1.5gb. But regardless, if I set the bitrate in devede to 5000, I expect that to be honored.  But for some reason it's not.

---

### Post by mhouston100 on 2008-05-23
Thought I would add my 2 cents in as well even though this is an old thread I am still having the same problem.

Basically :

700MB XVID file (Excellent quality)

NeroVision 4.4GB (Excellent quality)

CovertXtoDVD 2.8-3GB (Fair quality, the lower the file size the less the quality)

Devede (Never more then 2.6GB (Low Quality)

Basically I have a whole lot (several hundred) of Xvids to convert and I need to find a program that can be either scripted or has a batch queue but also encodes to the highest rate possible for the media (like nerovision)

I know this is an old thread but any one still out there?

---

