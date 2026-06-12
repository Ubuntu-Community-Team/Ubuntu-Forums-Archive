---
title: "The question to end all questions"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-08
...probally not, but here goes anyway.

Mozilla. Won't play imbedded sounds. I mean pages with WAV/MP3 format sounds on them. a small, practically insignifcant thing... unless you're into [www.ytmnd.com](www.ytmnd.com) . And losing those fills all my old dead time with... well, with nothingness. ;_;

The quicktime / java helps on ubuntuguide.org don't seem to be of much help. Should I have certain repositories to be able to apt-get whatever I need?

---

### Post by aysiu on 2005-10-08
The Ubuntu Guide is undergoing a transition, as we're nearing the official release of Breezy. In the meantime, you can follow [these instructions](http://www.psychocats.net/sources.html) to enable extra repositories. As far as I know, that should get you all the proprietary codecs you need, except libdvdcss2 and w32codecs. Otherwise,

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

should be fine.

---

### Post by nerdman on 2005-10-08
I have all the codecs, but I'm talking about a Mozilla plug in. Evidently there are no linux versions for Quicktime / Windows Media Player, and somehow I guess its one of those I'd be needing V.V

Embeded Sound for Mozilla. ...Does anyone have it working?

---

### Post by aysiu on 2005-10-08
I have it working. Have you tried the mplayer mozilla plugin? ```
sudo apt-get install mozilla-mplayer
```

---

### Post by mlomker on 2005-10-08
> Embeded Sound for Mozilla. ...Does anyone have it working?

I thought that mplayer supported all of the Windows codecs.  Do you have the **mozilla-mplayer** package installed?

---

### Post by nitricacid on 2005-10-08
I use Mplayer for pretty much everything and it is support on Mozilla to play embeded files, granted you are not playing a RealPlayer Embeded file

---

### Post by Mustard on 2005-10-08
[quote=ubotu in irc]from memory, javadeb is for sun java debs packaged for ubuntu, Install from [http://tinyurl.com/bwomt](http://tinyurl.com/bwomt) (Hoary), or [http://tinyurl.com/87ofx](http://tinyurl.com/87ofx) (Breezy) 64-bit? See [https://wiki.ubuntu.com/RestrictedFormats#java](https://wiki.ubuntu.com/RestrictedFormats#java)[/quote]

This is the answer to the Java question from the bot on IRC.  Have you tried IRC for help before?

My embedded sound is working for flash.  I just went and tested some sound loops at the Flashkit site  if thats valid test.

---

### Post by nerdman on 2005-10-08
*scratches head furiously*

it tells me it can't find the package. Is there sources for repositories I'm missing out on? I got the extra repositories from Ubuntuguide.org...

---

### Post by mlomker on 2005-10-08
> extra repositories from Ubuntuguide.org...

It is in multiverse.  You should have these for each repository:

```

main restricted universe multiverse

```

---

### Post by Mustard on 2005-10-08
Post your source.list up if you like, nerdman.

---

### Post by nerdman on 2005-10-08
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

I took the comments out because they made it look cluttered.

---

### Post by Mustard on 2005-10-08
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu hoary main restricted
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb http://archive.ubuntu.com/ubuntu hoary-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse
#deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu hoary-updates universe multiverse


## Backports - package version from a newer release build to work on the current
## no guarantees on working - not enabled by default
#deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

## The source packages
#deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

I did post up mine, but it was a mess.

Here is an example one so you can see what you migh be missing.  Some are not enabled (commented out), but you could easily enable them by removing the comments.  Ive edited this somewhat from the original that I found.  I added the restricted sections to the official backports.  I am not sure whether the backports source packages are available.

---

### Post by nerdman on 2005-10-09
what reasons would there be to disable a repository? it seems the more places your OS has to look, the better chances of finding it. Some aren't trustworthy?

---

### Post by mlomker on 2005-10-09
> Some aren't trustworthy?

If it's a non-Ubuntu repository then there could be a package with the same name in another repo.  Ubuntu has quite a few packages that are not safe to upgrade to non-Ubuntu packages.

---

