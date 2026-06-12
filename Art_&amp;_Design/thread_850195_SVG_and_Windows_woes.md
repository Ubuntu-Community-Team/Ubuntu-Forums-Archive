---
title: "SVG and Windows woes"
date: 2008-07-05
forum: Art &amp; Design
---

### Post by eilu on 2008-07-05
I made a very nice logo for a client, and since he is planning to put it in things like brochures, posters and banners, I suggested a vector (so one file can be as small or as big as needed without getting pixelated)

Here's the rub- he's using Vista and can't open it (the svg). I've emailed him .eps, .png and .xaml versions (save as/exported from inkscape). Not sure if he can open the .eps, no idea what the .xaml looks like on his end and .png defeats the purpose of vector.

I'm thinking .wmf is probably the most idiot-proof way to go, since they'll be slapping it in powerpoint presentations and (likely) using word or MS publisher for their layouts (or even powerpoint itself), so I can just say "it's a clipart" and leave it at that. Is there any way to convert an svg to a wmf?

Sheesh, I wouldn't be jumping through hoops trying to get this to work if Vista just supported the darned global standard in the first place... Of course *he* will be thinking that it's a Linux thing (rather than what it actually is, which is a Windows thing) but I digress... ](*,)

---

### Post by hugmenot on 2008-07-05
Uniconvertor is supposed to serve as a format plugin for Inkscape.
[This guy has a package in his PPA]("https://edge.launchpad.net/~leleobhz/+archive"). I installed it to see if it works. It was able to convert from SVG to wmf on the command line. But I don&#8217;t knwo how lossy the conversion is. It&#8217;s fairly certain that WMF doesn't support all features of SVG.

---

### Post by Merk42 on 2008-07-06
Wouldn't converting it to a pdf retain its vector information and easily be viewable?

---

### Post by eilu on 2008-07-06
I suppose, but he can't use the (image in the) pdf to put it in his brochures and banners. I'll give uniconvertor a try and see if it is adequate.

Edit: well got the repo and installed with no trouble, but once I run it on the command line it spits this out:
```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 979, in Load
    xml_reader.parse(input_source)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 107, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/xml/sax/xmlreader.py", line 123, in parse
    self.feed(buffer)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 207, in feed
    self._parser.Parse(data, isFinal)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 301, in start_element
    self._cont_handler.startElement(name, AttributesImpl(attrs))
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 338, in startElement
    getattr(self, method)(attrs)
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 853, in image
    image = load_image(os.path.join(self.loader.directory, href)).image
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/Graphics/image.py", line 87, in load_image
    image = PIL.Image.open(filename)
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 1889, in open
    fp = __builtin__.open(fp, "rb")
IOError: [Errno 2] No such file or directory: 'out.jpeg'
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/uniconvertor/__init__.py", line 70, in <module>
    doc = load.load_drawing(sys.argv[1])
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/io/load.py", line 364, in load_drawing
    return load_drawing_from_file(file, filename)
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/io/load.py", line 337, in load_drawing_from_file
    doc = loader.Load()
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 979, in Load
    xml_reader.parse(input_source)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 107, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/xml/sax/xmlreader.py", line 123, in parse
    self.feed(buffer)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 207, in feed
    self._parser.Parse(data, isFinal)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 301, in start_element
    self._cont_handler.startElement(name, AttributesImpl(attrs))
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 338, in startElement
    getattr(self, method)(attrs)
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/plugins/Filters/svgloader.py", line 853, in image
    image = load_image(os.path.join(self.loader.directory, href)).image
  File "/usr/lib/python2.5/site-packages/uniconvertor/app/Graphics/image.py", line 87, in load_image
    image = PIL.Image.open(filename)
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 1889, in open
    fp = __builtin__.open(fp, "rb")
IOError: [Errno 2] No such file or directory: 'out.jpeg'
```

Just running $uniconv -h launches:
```
 UniConvertor 1.1.2

USAGE: uniconvertor [INPUT FILE] [OUTPUT FILE]

Converts one vector graphics format to another using sK1 engine.
sK1 Team (http://sk1project.org), copyright (C) 2007,2008 by Igor E. Novikov

 Allowed input formats:
     AI  - Adobe Illustrator files (postscript based)
     CDR - CorelDRAW Graphics files (7-X3,X4 versions)
     CDT - CorelDRAW templates files (7-X3 versions)
     CCX - Corel Compressed Exchange files
     CMX - Corel Presentation Exchange files (CMX1 format)
     SVG - Scalable Vector Graphics files
     FIG - XFig files
     CGM - Computer Graphics Metafile files
     AFF - Draw files
     WMF - Windows Metafile files
     SK  - Sketch/Skencil files
     SK1 - sK1 vector graphics files

 Allowed output formats:
     AI  - Adobe Illustrator files (postscript based)
     SVG - Scalable Vector Graphics files
     CGM - Computer Graphics Metafile files
     WMF - Windows Metafile files
     SK  - Sketch/Skencil files
     SK1 - sK1 vector graphics files

Example: uniconvertor drawing.cdr drawing.svg
```
So I guess the install worked, so what's wrong?

---

### Post by AJB2K3 on 2008-07-06
Has he even tryed to install the necessary codex/plugings for vista?
It would be the easer option.
[http://wiki.svg.org/Viewer_Implementations]("http://wiki.svg.org/Viewer_Implementations")

---

### Post by hugmenot on 2008-07-06
Well, it was the first time using uniconv for me too. I noticed later that it also outputs errors when there are some font-family styles in the SVG it doesn't find.

How did you call the command? "uniconv in.svg out.wmf"?

What you can try next is do Vacuum defs in the file menu of Inkscape and then save as Plain SVG not as Inkscape SVG.

EDIT: In general EPS should do it. It&#8217;s the standard delivery file format. What I don&#8217;t know is if MS Office displays it nicely and antialiased. IT shoudl certainly be able to print it properly.

---

### Post by eilu on 2008-07-06
> **hugmenot said:**
> ...

What you can try next is do Vacuum defs in the file menu of Inkscape and then save as Plain SVG not as Inkscape SVG.

Tried that, didn't work. Keeps spitting out the same error (looking for out.jpeg). Didn't know there was a difference between an "Inkscape SVG" and a "plain SVG" (since they have the same extension).

I think I'll just tell him to install the Vista plugins...

---

### Post by stinkyfishheadisred on 2009-11-25
I suggest the following possibilities:

1) Export .png files at different resolutions.  Some high-res, some lower res.  This probably will make your client happiest, as he probably doesn't really care about having the vector file. If you have a high enough resolution file to begin with he can always down-sample it and throw out resolution.  However this is the least elegant solution and the most space-intensive.

2) Have your client install Inkscape on his windows computer.  There are binary windows installation files available (eg. [http://sourceforge.net/projects/inkscape/files/inkscape/0.47/Inkscape-0.47-3.exe/download](http://sourceforge.net/projects/inkscape/files/inkscape/0.47/Inkscape-0.47-3.exe/download) ) .  This way he will be able to keep it in vector format.  I often use Inkscape on Windows XP and the files are completely compatible with the Ubuntu version (with the possible exception of fonts).

3) Have your client use Firefox to view the .svg files.  Firefox handles svg graphics slightly differently than Inkscape, so you may have problems there.  I think there are also plug-ins for IE.

If it were me, I would give the client a series of .png files (20x20, 100x100, 200x200, 800x800) in addition to the original .svg file.

---

### Post by Newfoundlander on 2009-11-25
Are you saying that Vista will not install Inkscape?  What program is he using for the layout.  If he would get Inkscape to run, he could either edit the svg himself or export it as a raster image.

---

