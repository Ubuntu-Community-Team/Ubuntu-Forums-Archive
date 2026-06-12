---
title: "Photo database ???"
date: 2005-10-24
forum: Art &amp; Design
---

### Post by dbee on 2005-10-24
Does anyone know where I can get a good photo stable ???

I came across a cool free professional photo database a couple of weeks ago and I finally got around to using it the other day, only to find that I've lost it :( 

Anyone know a good one ?? Pls ??

---

### Post by PaulBillett on 2005-10-28
[QUOTE=dbee]Does anyone know where I can get a good photo stable ???

I came across a cool free professional photo database a couple of weeks ago and I finally got around to using it the other day, only to find that I've lost it :( 

Anyone know a good one ?? Pls ??[/QUOTE]

gthumb?  [http://gthumb.sourceforge.net/](http://gthumb.sourceforge.net/)

---

### Post by UbuWu on 2005-10-28
F-spot?

---

### Post by etc on 2005-11-09
imgSeek?

---

### Post by nwillis on 2005-11-10
Second that vote for imgSeek.  It's the only one that handles IPTC metadata, which is a *must* for serious usage.

Frankly it's the only one that qualifies as a photo management application in my book.  gThumb, F-spot and gqview are nothing but thumbnail displayers.  For all the good they do, you'd might as well look at a directory of thumbnails in Nautilus.  In fact, that'd be better, since you won't have to install anything to do it.

Unfortunately imgSeek development has slowed down recently; during a rewrite I believe.  Some commercial juggernaut needs to pour money all over it.  And it'd be nice to have color-management.  But even as-is, there's nothing better for organizing, searching and managing your photos.

If you haven't seen it, the wavelet-based "find by rough-sketching" feature will blow you away.

dbee, what was this free professional database you saw?  What can you tell us about it?

N

---

### Post by poptones on 2005-11-10
Problem is "imgSeek" doesn't bloody work. I've tried installing it many times and no matter what it comes up with errors.

:~/wallpapers$ imgSeek
Traceback (most recent call last):
  File "/usr/bin/imgSeek", line 26, in ?
    from imgSeekLib import imgSeekApp
ImportError: No module named imgSeekLib

---

### Post by etc on 2005-11-10
[QUOTE=poptones]Problem is "imgSeek" doesn't bloody work. I've tried installing it many times and no matter what it comes up with errors.

:~/wallpapers$ imgSeek
Traceback (most recent call last):
  File "/usr/bin/imgSeek", line 26, in ?
    from imgSeekLib import imgSeekApp
ImportError: No module named imgSeekLib[/QUOTE]
That used to annoy me to death in Hoary.  Try using the one in the repo's if you haven't because they work for me.

---

### Post by poptones on 2005-11-10
What "repos?" That is what I get after running apt-get install imgseek

---

### Post by sb73542 on 2005-11-13
[QUOTE=poptones]What "repos?" That is what I get after running apt-get install imgseek[/QUOTE]

Could somebody please try running "apt-get install imgseek" to see if this program works now?  I'm currently using Mandrake, partially because imgseek works with it.  Last time I tried imgseek with Hoary, it wouldn't start up.  I'd install Breezy if I knew that imgseek worked.

---

### Post by mcduck on 2005-11-14
[QUOTE=sb73542]Could somebody please try running "apt-get install imgseek" to see if this program works now?  I'm currently using Mandrake, partially because imgseek works with it.  Last time I tried imgseek with Hoary, it wouldn't start up.  I'd install Breezy if I knew that imgseek worked.[/QUOTE]I just tried it and it works for me, so you start can start looking for your Ubuntu CD. :D

---

### Post by sb73542 on 2005-11-14
Cool, thank you mcduck!

---

### Post by poptones on 2005-11-14
I'd still like to know which "repo" etc was talking about. I got this working in hoary once a long time ago but never since - the one in the hoary repo is definitely borked.

---

### Post by sb73542 on 2005-11-15
Debian's version during that time period was also broken.  I haven't tried it recently.

---

### Post by claydoh on 2005-11-16
Works wonderfully here. In Hoary, imgSeek was built using python 2.3 iirc, and we use python2.4 by default. I would guess the Debian version at the time was built against python2.3 and it "slipped through the cracks" Luckily you can have both versions of python installed together. 

In breezy, it is working fine. it is found in the universe repository.
It requires among other things, python-qt3, and python-imaging, which should be installed automatically if they aren't already.
If you are still running hoary, try installing python2.3, python2.3-imaging and python2.3-qt3. I think that is what I used to get it working there

---

### Post by Martin-Herrmann on 2006-05-02
Hi,

Mapivi ([http://mapivi.de.vu]("http://mapivi.de.vu")) may be worth a look. It stores all meta information where it belongs to, in the pictures.
It is able to add, edit, copy, search and remove JPEG comments, EXIF and IPTC data.

Regards,  Martin

---

