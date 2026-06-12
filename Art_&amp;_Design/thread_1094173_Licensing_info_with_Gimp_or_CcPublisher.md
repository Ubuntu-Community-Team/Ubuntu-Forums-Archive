---
title: "Licensing info with Gimp or CcPublisher?"
date: 2009-03-12
forum: Art &amp; Design
---

### Post by jjalocha on 2009-03-12
I'd like to share some images on the web, so I want to attach meta-information to it: At least licensing, and maybe tags. But It seems that Gimp doesn't "support" CC, like Inkscape does, for example (File > Document metadata). At least, I can't find out how to do it in Gimp 2.6.1.

Googling for a solution, I found the CcPublisher application, which does exactly what I need, but for some strange reason is not packaged in Ubuntu. (There exists [old blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/cc-publisher") about that issue, that has been ignored so far.)

And when I try to run the [version downloaded from Creative Commons]("http://wiki.creativecommons.org/CcPublisher_on_Linux"), I get a [FONT="monospace"]'NameError: name 'OverflowWarning' is not defined'[/FONT] error. There is a ['bug report']("https://bugs.launchpad.net/ccpublisher/+bug/181529") about this issue, but everyone on that thread makes clear that this is not actually an error, and I don't really understand anything about it. (All requested dependencies were installed already on my computer.)

So, **back to my original question**: Anyone here knows how to attach licensing information to an image in Ubuntu? What tool do *you* use?

---

### Post by smartboyathome on 2009-03-12
What image type are you trying to use?

---

### Post by jjalocha on 2009-03-12
Probably mostly JPG, but maybe also XCF. I am actually trying to use XMP, since that is the preferred metadata format today.

---

### Post by jjalocha on 2009-03-12
I would like to share with you the different options I have found so far. Sadly enough, nothing looks very promising:

[LIST]
[*][Gimp Metadata Plugin]("http://bugzilla.gnome.org/show_bug.cgi?id=349224"): It should handle licensing information in an user-friendly way. It was targeted for Gimp 2.4, but has been re-targeted for 2.8.
[*][Gimp Image Publishing Plug-in]("http://carol.gimp.org/gimp2/print/license/gipp.html"): Very old alpha software, probably no longer maintained.
[*][Gimp Creative Commons License plugin]("http://lists.ibiblio.org/pipermail/cc-metadata/2005-April/000628.html"): This is announced in a mailing list, but the site seems not to be available.
[*][liblicense / license CLI / default-content-license]("http://wiki.creativecommons.org/Liblicense"): This application seems to be up-to-date, and the library and CLI are available in the [Ubuntu repositories]("http://packages.ubuntu.com/intrepid/liblicense-cli"). I haven't been able to attach a license to an image yet, but I'm still trying. Strangely, the [FONT="monospace"]default-content-license application[/FONT] mentioned in a [Linux.com article]("http://www.linux.com/feature/119963") does not seem to exist in Ubuntu. A detailed [tutorial]("http://wiki.creativecommons.org/Liblicense_tutorial") is aimed at developers but not at users.
[*][license-tagger]("http://wiki.creativecommons.org/License_tagger"): Seems to be a Python GUI for liblicense, but there is no stable download yet?
[*]Exiftool can be used to [manipulate metadata]("http://commons.wikimedia.org/wiki/Commons:Manipulating_meta_data"), but I think this is not XMP. I haven't found more information, yet.
[*][ImageMagick]("http://www.imagemagick.org/pipermail/magick-announce/2007-July/000036.html") handles XMP profiles, but there is no description anywhere on how to do that.
[*][Sagittarius]("http://photobuntu.wordpress.com/2008/04/11/sagittarius-is-out/"): A GUI application in alpha stage.
[*][XMP-Manager]("https://launchpad.net/xmp-manager"): Another application in alpha stage. This one works in Nautilus, and is actually under development.
[/LIST]

I will try to find out how to make any of these work, and report back as I progress. :confused:

[EDIT: Added XMP-Manager]

---

### Post by smartboyathome on 2009-03-12
Have you thought of embedding a rar'd copy of your license into the image? You can do so with JPG, PNG, etc images quite easily. Just run this (ext just stands for extention):
```
cat original.ext license.rar > original_and_license.ext
```

---

### Post by D1ZZ4ZZT3R on 2009-03-12
> **smartboyathome said:**
> Have you thought of embedding a rar'd copy of your license into the image? You can do so with JPG, PNG, etc images quite easily. Just run this (ext just stands for extention):
```
cat original.ext license.rar > original_and_license.ext
```


is this similar to what i've seen done with jpgs of book covers that have rars of the books embedded in them? ever since i found out it was possible to do that, i've been intrigued by the concept. if anyone knows how to do this in linux or, at all, please share. 

sorry to go off subject.

---

### Post by jjalocha on 2009-03-12
Wow, smartboy, this really blows my mind! [In this thread]("http://www.linuxquestions.org/questions/linux-software-2/embed-file-into-image-rar-613323/") is a little bit more information about it.

But this is not really what I am looking for. I really want to add *meta-data* that can be read and written with standard methods and tools. That's also the reason I want to make sure I am actually using correct [XMP]("http://wiki.creativecommons.org/Exif").

---

### Post by jjalocha on 2009-03-12
I thought, exiftool does the job:

```
$ exiftool -ImageDescription="Beautiful Work" -Copyright="Whatever" -Artist="modest Jerzy" image.jpg
```

And when I check with the same tool, the data really seems to be recognized as XMP:

```
$ exiftool -scanForXMP image.jpg
...
Image Description               : Beautiful Work
Artist                          : modest Jerzy
Copyright                       : Whatever
...
```

But liblicense doesn't recognize it:

```
$ license image.jpg
No license found for image.jpg
```

:(

---

### Post by jjalocha on 2009-03-13
I forgot to mention yesterday, that I had no luck with Creative Commons' [License Tagger]("http://wiki.creativecommons.org/License_tagger") software. I installed GIT (git-core), downloaded the thing, but the application doesn't run:

```
$ python tagger.py
Traceback (most recent call last):
  File "tagger.py", line 48, in <module>
    [mylocale.GetCanonicalName()], fallback = True)
  File "/usr/lib/python2.5/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.5/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.5/gettext.py", line 337, in _parse
    tmsg = unicode(tmsg, self._charset)
LookupError: unknown encoding: CHARSET
```

An other Ubuntu user reported [another problem]("https://bugs.launchpad.net/ubuntu/+source/liblicense/+bug/284772/+viewstatus") with this application, so I guess, it is not ready for release, yet.

---

### Post by jjalocha on 2009-03-13
Finally solved:

```
$ exiftool \
> -ImageDescription="My Beautiful Work" \
> -Copyright="Whatever" \
> -Artist="Jerzy" \
> -XMP-xmpRights:Marked="True" \
> -XMP-xmpRights:WebStatement="http://example.com/pdf-metadata.html" \
> -XMP-xmpRights:UsageTerms="This work is licensed to the public under the Creative Commons..." \
> -XMP-cc:License="http://creativecommons.org/licenses/by-sa/2.0/" \
> image.jpg
```

The 'license' tool now correctly recognizes the license.

You can read the [CC Wiki]("http://wiki.creativecommons.org/XMP") for descriptions about how to fill the fields used by Creative commons. I don't know, how they relate to the 'Copyright' and 'Artist' fields.

Note, that cc:morePermissions, cc:attributionURL, and cc:attributionName do not work for me, using exiftool ver 7.30.

---

### Post by D1ZZ4ZZT3R on 2009-03-22
> **jjalocha said:**
> Wow, smartboy, this really blows my mind! [In this thread]("http://www.linuxquestions.org/questions/linux-software-2/embed-file-into-image-rar-613323/") is a little bit more information about it.




thanks. i'll look into it

---

