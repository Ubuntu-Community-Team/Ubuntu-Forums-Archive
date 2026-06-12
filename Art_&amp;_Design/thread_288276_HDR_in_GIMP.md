---
title: "HDR in GIMP?"
date: 2006-10-29
forum: Art &amp; Design
---

### Post by JNasci7906 on 2006-10-29
Hey all, So i just got a new digital camera and want to make some HDR images. However, after searching endless pages on the net for howto's, tips, tricks, and more importantly a basic tutorial....im lost. Im just curious if anybody out there has a link(s) to good basic pages about getting hdr in gimp 2.2? Also, any HDR introduction links are also appreciated. THANKS!

Nash

---

### Post by roderikk on 2006-10-31
From the top of my head, HDR requires 16 bit support and I believe the Gimp doesn't do that yet. However, I just read that CinePaint (a gimp spin off for movies) does do 16 bit, I have never used this so I don't know whether this is suitable for still images but you could try it out and tell us :-). Good luck!

---

### Post by JNasci7906 on 2006-10-31
yea ive noticed that cinepaint seems to be the program to use, ill try to get it installed and running and such, however, i am new to linux and installing from tarballs and compiling isnt quite in my bag of tricks yet, but ill try it out, thanks!

Nash

---

### Post by roderikk on 2006-10-31
```
sudo aptitude show cinepaint

Package: cinepaint
New: yes
State: not installed
Version: 0.20-1-2
Priority: optional
Section: universe/graphics
Maintainer: Andrew Lau <netsnipe@users.sourceforge.net>
Uncompressed Size: 3072k
Depends: libc6 (>= 2.3.4-1), libcinepaint0 (>= 0.20-1), libfltk1.1 (>= 1.1.7),
         libgcc1 (>= 1:4.0.2), libglib1.2 (>= 1.2.0), libgtk1.2 (>= 1.2.10-4),
         libgutenprint2 (>= 5.0.0~rc2), libgutenprintui1-1 (>= 5.0.0~rc2),
         libice6, libjpeg62, liblcms1 (>= 1.08-1), libopenexr2c2a (>= 1.2.2),
         libpng12-0 (>= 1.2.8rel), libsm6, libstdc++6 (>= 4.0.2-4), libtiff4,
         libx11-6, libxext6, libxi6, libxmu6, libxt6, zlib1g (>= 1:1.2.1),
         cinepaint-data (= 0.20-1-2)
Description: motion picture image painting and retouching tool
 CinePaint is a painting and image retouching program designed to work best with
 35mm film and other high resolution high dynamic range images. Through its
 frame manager and flipbook player, CinePaint can be used for painting of
 background mattes and for the frame-by-frame retouching of movies. Its studio
 developers incluce Rhythm & Hues, Sony Pictures Imageworks, DreamWorks and ILM.
 
 The 32-bit per channel color range of CinePaint appeals to 35mm
 cinematographers and professional still photographers because film scanners are
 capable of greater color bit-depth than can be displayed on an 8-bit per
 channel monitor or can be manipulated in typical programs. However, CinePaint
 is a general-purpose tool useful for working on images for motion pictures,
 print, and the Web. 
 
 Apart from conventional image formats (eg. JPEG, PNG, TIFF, and TGA) CinePaint
 also has support for specialised motion picture formats such as Kodak Cineon,
 ILM OpenEXR, Maya IFF and 32-bit TIFF. Specialised colour management is also
 available through CinePaint's Gutenprint and LittleCMS support. 
 
 This project was formerly known as Film Gimp. 
 
 Homepage: http://cinepaint.org

```

Not really necessary ;-)

---

### Post by yabbadabbadont on 2006-10-31
Hey thanks.  I was wondering if there was HDR capapble software in Linux too.  As for a tutorial, [this](http://graphics.stanford.edu/~mhouston/school/digital-photo/) is one that I think is useful.

---

### Post by mercury80 on 2009-08-17
Might be a bit late... but for people looking for the same thing, check out [Qtpfsgui]("http://qtpfsgui.sourceforge.net/")

CinePaint, a "movie-maker"-edition of GIMP could also do the trick...

---

### Post by AJB2K3 on 2009-08-17
> **mercury80 said:**
> Might be a bit late... but for people looking for the same thing, check out [Qtpfsgui]("http://qtpfsgui.sourceforge.net/")

CinePaint, a "movie-maker"-edition of GIMP could also do the trick...

If you want a quick guide to hdr look in my sig.

---

### Post by mcduck on 2009-08-17
The best tool for HDR imaging in Linux would be Qtpfsqui.

There's a thread about HDR imaging and applications & tips here: [http://ubuntuforums.org/showthread.php?t=1185859]("http://ubuntuforums.org/showthread.php?t=1185859")

---

### Post by bapoumba on 2009-08-18
This thread is really old. Please refer to the one linked in the post above, thanks.

---

