---
title: "How to get Uniconvertor 1.1.5"
date: 2011-10-20
forum: Art &amp; Design
---

### Post by samigina on 2011-10-20
Hi.

If you are a Inkscape user and you are using it for press work, maybe you work with the great PDFCMYK extension, but if you use it with the Uniconvertor version that comes with Ubuntu (1.1.4) you probably have found that it doesn't works.

Here is a small guide to compile the last version (1.1.5) that includes a nice standalone gui, and that work with the PDFCMYK extension flawesly:

**1.** Uninstall any previous version of Uniconvertor from your system.

**2.** Install the required dependencies for the compilation. Open a terminal and type: ```
sudo apt-get install build-essential python-all-dev liblcms1-dev libjpeg62-dev libpaps-dev
```

**3.** Download the uniconvertor sources from [here]("http://sk1project.org/modules.php?name=Products&product=uniconvertor&op=download").

**4.** You must get 3 files:
uniconvertor-1.1.5.tar.gz (the program itself)
uniconvw-1.1.5.tar.gz (the gui)
sk1libs-0.9.1.tar.gz (the libs)

**5.** Extract the files with right click "extract here".

**6.** With a terminal, navigate to the folders. If you extracted them in your Downloads folder it must me something like: ```
cd Downloads/sk1libs-0.9.1
```

**7.** Type: ```
python setup.py bdist_deb
```

**8.** Repeat 6 and 8 for the other folders (uniconvertor-1.1.5, uniconvw-1.1.5)

**9.** If all goes well, you must have a new folder called "Dist", and inside a precious .DEB that you can install with Gdebi (```
sudo apt get install gdebi
```)

**10.** Install the 3 debs, first sk1libs, then uniconvertor, and finally uniconvw.

**11.** Enjoy!

---

### Post by jagajugue on 2011-10-27
Dude, you're the best. I got it working now, but still got a problem. When I try to convert a .cdr file to .svg with uniconw, it shows the following message:

*An error occurred: Parsing error: unrecognized file type*

And when i use uniconvertor it shows:

```
$ uniconvertor input.cdr out.svg
Traceback (most recent call last):
  File "/usr/bin/uniconvertor", line 13, in <module>
    uniconv_run()
  File "/usr/lib/python2.7/dist-packages/uniconvertor/__init__.py", line 95, in uniconv_run
    doc = load.load_drawing(input_file)
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/io/load.py", line 377, in load_drawing
    return load_drawing_from_file(file, filename)
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/io/load.py", line 354, in load_drawing_from_file
    raise SketchLoadError(_("Parsing error: ")+ str(value))
app.events.skexceptions.SketchLoadError: Parsing error: unrecognised file type
```

:(

A friend of mine send me this image. Don't now if it's because he's using the newest Corel Draw and uniconvertor doesn't have support yet.

What do you think?

---

### Post by samigina on 2011-10-27
That looks like an unsupported corel version, Uniconvertor can handle corel files up to X4.

---

### Post by jagajugue on 2011-10-29
Yeah, that's what I was afraid. Anyway, great help you give! Thanks!
o/

---

### Post by jackrawn on 2011-11-01
thanks for sharing with me.

---

### Post by chandra on 2012-01-04
Thank you samigina. It worked perfectly :p

---

### Post by Kreaninw on 2012-05-19
I am using Ubuntu 12.04 LTS. I can install sk1libs-0.9.1 and uniconvertor-1.1.5 perfectly fine, but fail to install uniconvw-1.1.5.

I tried to install with GDebi and with Ubuntu Software Center, both fail to install uniconvw-1.1.5. When tried to install with GDebi, GDebi crashes every time. When tried to install with Ubuntu Software Center, it show Internal Error massage which describes my .deb could not be opened.

Is it importance to install uniconvw-1.1.5? And how can I successfully install uniconvw-1.1.5 on Ubuntu 12.04 LTS?

Thanks in advance. :)

---

