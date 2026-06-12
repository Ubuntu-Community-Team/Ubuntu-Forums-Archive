---
title: "Open AI files in Inkscape?"
date: 2007-01-14
forum: Art &amp; Design
---

### Post by oroboro on 2007-01-14
Hi, I'm having problems opening Adobe Illustrator files (.ai) in Inkscape. I can save them perfecty fine, but for some reason, Inkscape says that it "failed to open" the file. I tried Xara Xtreme and it said that I needed to install imagemagick. I installed imagemagick from the source and now Xara will still not open them and when Inkscape attempts to, it hogs up all my memory so that I have to restart my computer. I get the same result when trying to open the very same ai files saved by Inkscape. Do I need some external libraries or something?

---

### Post by deanjm1963 on 2007-01-14
There's a few extra things you need to install for inkscape to open AI files correctly.

open synaptic and search for inkscape, right click on "inkscape" and look at Mark Suggested for Installation.

Install, psotedit (which turns postscript to editable format), libwmf-bin, sketch (if you're using dapper) or skencil (if you're using edgy), perlmagic and imagemagic.

Works for me.

---

### Post by hermzz on 2007-01-23
> **deanjm1963 said:**
> 
Install, psotedit (which turns postscript to editable format), libwmf-bin, sketch (if you're using dapper) or skencil (if you're using edgy), perlmagic and imagemagic.


I think you meant to say pstoedit, perlmagick and imagemagick, in any case it didn't work for me, but I found this app that got me further: 

[http://wiki.inkscape.org/wiki/index.php/Tools#ai2svg.py](http://wiki.inkscape.org/wiki/index.php/Tools#ai2svg.py)

---

### Post by silbar on 2007-06-15
Perhaps related.  The Inkscape I installed today does not want to read EPS (encapsulated postscript) files.  And when I looked at Mark Suggested for installation in Synaptic, it didn't give me options to install things like pstoedit, just perl and python.

I would have thought a vector graphics drawing program would LOVE to import EPS files.  Any suggestions?

   Rico Silbar

Update: 6/8/10.  This problem seems to no longer be there in Inkscape 0.47pre4 r22446, built Oct 14 2009.  It opens EPS files just fine.

---

### Post by CheAziz on 2008-01-27
> **silbar said:**
> Perhaps related.  The Inkscape I installed today does not want to read EPS (encapsulated postscript) files.  And when I looked at Mark Suggested for installation in Synaptic, it didn't give me options to install things like pstoedit, just perl and python.

I would have thought a vector graphics drawing program would LOVE to import EPS files.  Any suggestions?

   Dick Silbar

I followed the earlier suggestion to use Synaptic and all the options that dont show up on your PC show on mine. Perhaps you're not using the new and updated version of Ubuntu, that is, 7.10?

Just a suggestion,

./cheaziz

---

### Post by prokoudine on 2008-01-28
> **oroboro said:**
> Hi, I'm having problems opening Adobe Illustrator files (.ai) in Inkscape.
There are PostScript based AI files and PDF based AI files (since 9.0). For the latter you want Inkscape 0.46 (pre0 version is available). Go to [www.inkscape.org](www.inkscape.org) for details ;-)

---

### Post by lvlo on 2008-01-28
Maybe this help - [**Uniconverter**:]("http://sk1project.org/modules.php?name=Products&product=uniconvertor")
[B]
Import filters[/B]: 
- CorelDraw ver.7-X3 (CDR/CDT/CCX/CDRX/CMX)
- Adobe Illustrator up to 9 ver. (AI postscript based)
- Postscript (PS)
- Encapsulated Postscript (EPS)
- Computer Graphics Metafile (CGM)
- Windows Metafile (WMF)
- XFIG
- Scalable Vector Graphics (SVG)
- Skencil/Sketch/sK1 (SK and SK1)
- Acorn Draw (AFF)

**Export filters**:
- AI (Postscript based Adobe Illustrator 5.0 format)
- SVG (Scalable Vector Graphics)
- SK (Sketch/Skencil format)
- SK1 (sK1 format)
- CGM (Computer Graphics Metafile)
- WMF (Windows Metafile)

---

### Post by santiagogaitan@gmail.com on 2008-05-19
Hi!

I would be gratefully if you can help me with the installation of the uniconvertor on my inkscape.

I'm on a ubuntu 8.04 - 64 bits.

Thanks.

---

### Post by kavoura on 2008-07-25
I am also using Ubuntu 8.04 64-bit version, and cannot install SK1 or Uniconverter, as they are only i386 versions.

Are there any other programs that can convert an Adobe Illustrator 8.0 file to a format usable by Inkscape? I have an old .ai file that I created many years ago in Illustrator 8, and now need to edit it in Linux.

---

### Post by sunny_nwho on 2008-08-12
The developers are also not sure if they will make a 64bit package. They suggest that our community does it. It would be great if any good person can make a deb for the rest of us

---

### Post by Ace2016 on 2008-08-15
I'm in debian sid at the moment and they have python-uniconverter, maybe you could just grab the debs from there

---

### Post by santiagogaitan@gmail.com on 2008-09-19
I've found this package of Uniconverter to 64bit plataform:

[http://security.ubuntu.com/ubuntu/pool/universe/p/python-uniconvertor/python-uniconvertor_1.1.2-1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/p/python-uniconvertor/python-uniconvertor_1.1.2-1_amd64.deb)

 I just installed it, but i don't found it in the Appplications menu. Neither the .cdr files are observed as openable when i double click on them.

Any help?

---

### Post by santiagogaitan@gmail.com on 2008-12-02
Hi every one. I'm on Hardy 8.04.1 desktop 64bits with a core2duo processor.

I found this debian package:

[http://http.us.debian.org/debian/pool/main/p/python-uniconvertor/python-uniconvertor_1.1.2-1_amd64.deb](http://http.us.debian.org/debian/pool/main/p/python-uniconvertor/python-uniconvertor_1.1.2-1_amd64.deb)

It's python-uniconvertor_1.1.2-1_amd64.deb. I've just installed it with one click and is working fine although the conversion is less efficient than i hoped.

I'm sad while thinking that even tough 8.04.x Hardy Heron is the curently Long Term Support version of Ubuntu, the unique ubuntu package of uniconvertor is aimed to the 8.10 Intrepid Ibex.

... Thanks to the Official Debian support.

---

### Post by lbharti on 2009-05-27
Files prior to AI 9.0 are PostScript files. They can be converted using pstoedit to svg, and opened in Inkscape.

---

### Post by jeremyjared74 on 2010-08-11
Have you tried saving them as an EPS. I think this will work. I read when installing Inkskape that it would open them, but it won't open mine either.

---

### Post by davewex26 on 2013-04-30
good post

---

