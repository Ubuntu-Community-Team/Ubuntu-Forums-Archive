---
title: "streaming problems"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-05-22
Hi all

I just upgraded to feisty in a pleasingly hassle-free way. I followed the how-to for enabling multimedia from here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

But still having problems with streams. In particular, .wmv streams don't have sound.

Any help with this? Much appreciated if there is any...

griffiss

---

### Post by Pragmatist on 2007-05-24
> **Griffiss said:**
> ...In particular, .wmv streams don't have sound...

What player are you using?

---

### Post by Griffiss on 2007-05-29
vlc and totem. when I use firefox vlc is default for these file types, and totem in opera. I don't actually know how to change this is opera:confused:

---

### Post by Pragmatist on 2007-05-29
I'm assuming that you can see the .wmv video, but you just can't hear any sound.  Why not try another video player?  It will at least help to figure out the problem.  Try installing mplayer and xine.  For xine, install the "xine-ui" and "libxine1" packages.  For mplayer you need to install the "mplayer" package

---

### Post by Griffiss on 2007-05-30
thanks for your suggestions pragmatist. no joy with mplayer either. and when i tried to install xine using ```
sudo aptitude install xine-ui libxine-extracodecs
```it told me there were untrusted packages which might compromise my system, so i aborted. I tend to err on the side of caution until profficient enough to sort out potential headaches.

I noticed a new twist as well - the streams i've been trying to play are .asx - windows media but a different format or something? I've read elsewhere that there is less support for .asx on ubuntu

---

### Post by Griffiss on 2007-05-30
well, i found gxine in add/remove... installed that and it's played everything i''ve thrown at it!:D

the .asx files didn't have good sync between audio and visual and 'stuttered' occasionally but is still very watchable.

can now play .ram media too!

---

### Post by noMScraig on 2007-06-04
bump...

I have the same problem....any help?

installed xine, vlc, mplayer and have video with no sound with xine.

Will try codecs above.

-c

---

