---
title: "MP3 encoding"
date: 2004-11-26
forum: Apple PPC Users
---

### Post by z0mbix on 2004-11-26
I understand from the wiki ([http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)) that I need gstreamer*-lame to encode CD's

I've got gstreamer-mad installed and can play mp3's fine, but I want to be able to encode CD's to MP3 so I can put them on my iPod. I know x86 users can install gstreamer*-lame but this package is not available for PPC. Anyone know where to get this package for PPC?

---

### Post by slux on 2004-11-26
Is it in the universe source packages? You could get it there if it is and compile your own package.

<edit>
Ah, it's not in the universe at all and seems the source package is not offered (which is strange...). Well, I guess you could bug the creator of the repository, build it from source or just use something else.

grip is one package that easily do lame encoding and works pretty well, then you just need lame itself.
</edit>

I have to ask, though: why not use ogg vorbis for your encoding needs instead?
It's free, unencumbered by patents and offers superior quality to mp3.

Having a portable mp3 player that doesn't support it would be a reason I guess, but even that area is starting to be pretty well covered...

---

