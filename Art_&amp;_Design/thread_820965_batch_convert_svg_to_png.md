---
title: "batch convert svg to png"
date: 2008-06-06
forum: Art &amp; Design
---

### Post by NoSmokingBandit on 2008-06-06
whats the easiest way to do this? I have a ton of svg i would like to convert, but so far havent found an easy way to do this. I hace access to OSX, XP, and Ubuntu on this box, so whatever OS does it the easiest...
Thanks for any help, i've googled for an hour and couldnt find anything, so any help is very welcome! :guitar:

---

### Post by forger on 2008-06-06
I just opened gnome-terminal and searched:
```
$ apt-cache search svg.*png
inkscape - vector-based drawing program
librsvg2-bin - command-line and graphical viewers for SVG files
scribus - Open Source Desktop Page Layout
...
```

my eye caught librsvg2-bin
```

$ apt-cache show librsvg2-bin
...
Description: command-line and graphical viewers for SVG files
 The rsvg library is an efficient renderer for Scalable Vector Graphics
 (SVG) pictures.
 .
 This package includes a command-line utility to convert the SVG files
 to the PNG format and a graphical SVG viewer.

```

afterwards, i checked out the package to see the command for it:
```
$ sudo apt-get install librsvg2-bin
...

$ dpkg -L librsvg2-bin
...
/usr/bin/rsvg-convert
/usr/bin/rsvg-view
/usr/bin/rsvg
...

```

Cool, now we know the commands included :)
```
$ rsvg-convert --help
Usage:
  rsvg-convert [OPTION...] [FILE...] - SVG Converter
Help Options:
  -?, --help                           Show help options
Application Options:
  -d, --dpi-x=<float>                  pixels per inch [optional; defaults to 90dpi]
  -p, --dpi-y=<float>                  pixels per inch [optional; defaults to 90dpi]
  -x, --x-zoom=<float>                 x zoom factor [optional; defaults to 1.0]
  -y, --y-zoom=<float>                 y zoom factor [optional; defaults to 1.0]
  -z, --zoom=<float>                   zoom factor [optional; defaults to 1.0]
  -w, --width=<int>                    width [optional; defaults to the SVG's width]
  -h, --height=<int>                   height [optional; defaults to the SVG's height]
  -f, --format=[png, pdf, ps, svg]     save format [optional; defaults to 'png']
  -o, --output                         output filename [optional; defaults to stdout]
  -a, --keep-aspect-ratio              whether to preserve the aspect ratio [optional; defaults to FALSE]
  -v, --version                        show version information
  -b, --base-uri                       base uri


```

With some bash scripting you have a script:
```
$ cd your-directory-with-the-svgs/
$ for i in *; do rsvg-convert $i -o `echo $i | sed -e 's/svg$/png/'`; done
```

cheers! :KS

P.S. you can do a similar conversion using inkscape's command line:
```
$ cd your-directory-with-the-svgs/
$ for i in *; do inkscape $i --export-png=`echo $i | sed -e 's/svg$/png/'`; done
```

---

### Post by NoSmokingBandit on 2008-06-06
I love you.

Ill get that package and give it a shot. Thank you so much :KS

---

### Post by acelin on 2008-06-07
> **NoSmokingBandit said:**
> I love you.

Ill get that package and give it a shot. Thank you so much :KS

I know wow... this is great.

---

### Post by NoSmokingBandit on 2008-06-07
apt-get cant find that package for me, what repo is it in? Im on kubuntu 8.04 and have all the standard repos enabled.

---

### Post by arigram on 2008-06-07
If you want a GUI, how about Phatch?
It can do a lot more than simple conversion too.
[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by borobudur on 2008-10-28
Hi [forger]("http://ubuntuforums.org/member.php?u=178447"), could you help to change your nice little script to a whole file structure with directories and subdirectories?

```
for i in *; do rsvg-convert $i -o `echo $i | sed -e 's/svg$/png/'`; done
```

Thanks!

---

### Post by forger on 2008-10-28
use find:
```

myfolder=/path/to/your/folder
for i in `find $myfolder -depth -name '*.svg'`; do rsvg-convert $i -o `echo $i | sed -e 's/svg$/png/'`; done

```
The code above is not tested, I just assume that *it should* work :)

In ubuntu 8.04.1 (hardy heron) or 8.10 (intrepid ibex) you have phatch:
```
sudo apt-get install phatch
```

---

### Post by forger on 2008-10-28
> **NoSmokingBandit said:**
> apt-get cant find that package for me, what repo is it in? Im on kubuntu 8.04 and have all the standard repos enabled.

a bit late answer, but:
[http://packages.ubuntu.com/librsvg2-bin](http://packages.ubuntu.com/librsvg2-bin)

---

### Post by borobudur on 2008-10-29
> **forger said:**
> use find:
```

myfolder=/path/to/your/folder
for i in `find $myfolder -depth -name '*.svg'`; do rsvg-convert $i -o `echo $i | sed -e 's/svg$/png/'`; done

```The code above is not tested, I just assume that *it should* work :)

In ubuntu 8.04.1 (hardy heron) or 8.10 (intrepid ibex) you have phatch:
```
sudo apt-get install phatch
```

Thanks!

---

### Post by Jameshardy88 on 2009-03-13
I also wish to convert lots of svg and svgz (not sure exactly what these are really and how they are different from svg's but anyway) files into png, i tried using phatch and it seemed to work fine for lots of file types however svg's did not seem to be among the files that it can convert to or from, am i just missing something? if not can somebody recommend another gui method of converting them as i am not yet proficient enough to use the command line (unless VERY basic).

---

### Post by ilpillo on 2009-10-05
> **forger said:**
> 
In ubuntu 8.04.1 (hardy heron) or 8.10 (intrepid ibex) you have phatch:
```
sudo apt-get install phatch
```

Unfortunately phatch is not able to manage svg files

---

### Post by stani on 2009-10-05
> **ilpillo said:**
> Unfortunately phatch is not able to manage svg files
Phatch 0.2 handles svg files and is available in Ubuntu Karmic. For older Ubuntu versions you can use:
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)

---

### Post by kperkins on 2009-10-08
You can convert svgs using imagemagick
All svgs in one folder and via commandline run
mogrify -format png *.svg
Change the png to wahtever image format you want.  Really quite easy.

---

### Post by mcduck on 2009-10-09
I'd really use Inkscape's CLI tools to convert from SVG. Simply because while many programs have *some level* of SVG support, most of them don't actually have *full* support for all SVG features.

For example Imagemagick works fine for basic SVG files, but if you have any blur or other effects in your SVG images it will not be able to include those into the result. Inkscape will.

---

### Post by vinutux on 2009-10-11
+1 for Phatch:P

---

### Post by stani on 2009-10-11
> **mcduck said:**
> I'd really use Inkscape's CLI tools to convert from SVG. Simply because while many programs have *some level* of SVG support, most of them don't actually have *full* support for all SVG features.

For example Imagemagick works fine for basic SVG files, but if you have any blur or other effects in your SVG images it will not be able to include those into the result. Inkscape will.
The new version Phatch 0.2 uses Inkscape CLI for batch converting SVG. If Inkscape is not installed, it will use ImageMagick as a fallback. Phatch 0.2 is available in Ubuntu Karmic or through a PPA for Jaunty, Intrepid and Hardy:
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)

---

### Post by mcduck on 2009-10-12
> **stani said:**
> The new version Phatch 0.2 uses Inkscape CLI for batch converting SVG. If Inkscape is not installed, it will use ImageMagick as a fallback. Phatch 0.2 is available in Ubuntu Karmic or through a PPA for Jaunty, Intrepid and Hardy:
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)

That's good news, the SVG support in Imagemagick was always way too limited to be any use.

..although I still prefer command-line tools in my own use. But I always recommend Phatch for people who need to handle large amounts of images; for some reason most people don't seem to share my love for scripted image processing.. ;)

---

### Post by kendhia on 2011-11-29
Thank you very much .

---

