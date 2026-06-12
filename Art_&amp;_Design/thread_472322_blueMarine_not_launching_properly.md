---
title: "blueMarine not launching properly"
date: 2007-06-12
forum: Art &amp; Design
---

### Post by Kundalinux on 2007-06-12
When I launch my newly installed blueMarine I can see it's splash screen which says the program is loading, along with Terminal doing some stuff in the background. After a few seconds what should be blueMarine main window appears blank, with no menus or anything else, just a white window. So I still haven't been able to use the program once. Anyone else experiencing this? Please help :)

---

### Post by JurB on 2007-08-31
Similar problem here: 
```
 Exception in thread "main" java.lang.NoClassDefFoundError: it/tidalwave/netbeans/boot/Main

```

---

### Post by hxall on 2007-10-17
Perhaps this addresses the problem you are having:

A patched 0.9.RC2b release is now available for download.  It fixes a blocking problem with 0.9.RC2 startup (all operating systems)...

Cheers.

---

### Post by hxall on 2007-10-19
Sadly the current version (0.9.RC2b) does not seem to be working on 64bit Gutsy as of yet, I have informed the developers and a bug report has been submitted...

             [http://bluemarine.tidalwave.it/issues/browse/BM-602](http://bluemarine.tidalwave.it/issues/browse/BM-602)

From Giudici:
*"Hmm... 64bit JVM... I've never tested on a 64bit JVM and there are some native libraries in blueMarine, so it could be a problem (maybe)."*

btw, seen reports that it works well for Vista and WinXP users, latest version can be downloaded from here:  [http://bluemarine.tidalwave.it/download](http://bluemarine.tidalwave.it/download)

This project looks very promising for those looking for Adobe Lightroom functionality for Linux, stay tuned...

---

### Post by GraFF on 2007-11-02
> **hxall said:**
> S
From Giudici:
*"Hmm... 64bit JVM... I've never tested on a 64bit JVM and there are some native libraries in blueMarine, so it could be a problem (maybe)."*


and damn sure there _is_ a problem. I wish they'd get it fixed, cuz Picasa on linux is not something that I'm willing to use for a long time)

---

### Post by jcornuz on 2007-11-03
Have you already tried using BlueMarine? I did (with chroot) and honeslty, at that time, it doesn't do a lot. Just load images (sometimes) wants to copy everything in other folders and I haven't found a way to do proper RAW edition with it.

An interesting project, but not there yet, IMHO. Although I would be very glad to be proved wrong :)

Take care,

Joel

PS: have a look at my blog - I am trying to load it with as much Linux photography tricks as possible

---

### Post by djxcon on 2008-03-28
I was able to get past this error in Feisty using the following:


```
sudo chmod -R 755 /usr/share/blueMarine/
```

```
sudo chown -R root:root /usr/share/blueMarine/
```

```
cd /usr/bin
```

```
blueMarine
```

Once the splash screen loads, it appears to hang at the point where the status indicator reads: Starting Modules, but behind the splash is another dialog asking for you to set up the workspace.  If you choose to change the default directory, the Next button will no longer be enabled.  Accept the default and restart blueMarine.

---

### Post by djxcon on 2008-03-28
Forgot to mention that I had to disable Beryl and fall back to Metacity.  While I was using Beryl, the interface was completely white.

---

### Post by heraclites on 2008-10-23
I managed to run blueMarine on hardy 64 bit using Fabrizzio's instructions here: [http://www.intilinux.com/software/554/bluemarine-open-source-photo-workflow/]("http://www.intilinux.com/software/554/bluemarine-open-source-photo-workflow/") to solve a java exception issue.
Then I had to completely disable compiz to avoid the blank window I was having after the splash screen.

Hope that helps.

---

### Post by de_valentin on 2009-08-31
Hi,

I'm not sure if my problem is the same as that of the others. But if I try to start up blueMarine in the 'terminal' I get the following error message.


```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fec9ce7758f, pid=5345, tid=140653380041040
#
# JRE version: 6.0_14-b08
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.0-b16 mixed mode linux-amd64 )
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f
#
# An error report file with more information is saved as:
# /home/valentin/hs_err_pid5345.log
[thread 140653390731600 also had an error]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted
```

Can anyone help me with that?

It seems more of a java problem than anything else

Thanks.

---

### Post by AJB2K3 on 2009-08-31
Its just no ware near as usefull as rawtherapee its far to buggy and incomplete.

---

### Post by stafio on 2009-10-20
I have the same issue as de_valentin and haven't been able to find a fix.

---

### Post by graphius on 2009-10-25
> Its just no ware near as usefull as rawtherapee its far to buggy and incomplete.

I agree!!!
now if only RawTherapee had area selection, I would be happy...

---

### Post by blur xc on 2009-11-12
I just tried Rawtherapee for the first time, and it's nice to have a free raw editor, but it far to slow and clunky for any serious work, so far, from what I've found.

Is there a way to get filmstrip view and to browse large previews of raw files with the arrow keys like in lightroom and bibble?

Like for instance, I took 300 family photos on sunday, and I need to quickly view all the photos to flag keepers and unflag throw-aways, and mabye rate a few gems (stars), so that I can process all the good shots in a batch.  How can you do that in Rawtherapee?  And small thumbnails don't cut it when judging a photo as a keeper or destined for the trash bin.  I ofen need to zoom in a bit to check out details and accuracy of focus as well.

BM

---

### Post by graphius on 2009-11-12
RawTherapee works great for me. It is fast (on a dual core laptop, 4Gb ram)
I don't find it very buggy at all. no crashing, no glitches. I am using 2.4.1.

---

### Post by blur xc on 2009-11-13
> **graphius said:**
> RawTherapee works great for me. It is fast (on a dual core laptop, 4Gb ram)
I don't find it very buggy at all. no crashing, no glitches. I am using 2.4.1.

I know we are going on a bit of a thread derail here- my apologies to the op...

I've got a core 2 duo 3ghz, 4gig ram machine here.  When scrolling through thumbnails of folders w/ many files (~300), it chugs, a lot.  By chugs, I mean it doesn't scroll smoothly.  It hasn't crashed on me, and I'm sure if I use it a lot, I'd get faster w/ it, but it seems slow compared to Bibble or Lightroom.  And of those two, I'd say Bibble is quite a bit faster.

But all that aside- how can you scroll through a bunch of pictures looking at full screen previews of each photo, like you can in LR and Bibble?  If there's a way, I'd love to hear it.

BM

---

### Post by graphius on 2009-11-13
Again, apologies to the OP, but I really don't think Bluemarine is going to be ready any time soon.

> But all that aside- how can you scroll through a bunch of pictures looking at full screen previews of each photo, like you can in LR and Bibble? If there's a way, I'd love to hear it.


RawTherapee is a very "Unixy" program. It does one thing very well, that is process raw files. for browsing I use DigiKam, then right click and open in RT.
I will agree in that respect it is not as good as Bibble, or Lightroom, but I will argue that the raw processing engine in RT is second to none.

---

