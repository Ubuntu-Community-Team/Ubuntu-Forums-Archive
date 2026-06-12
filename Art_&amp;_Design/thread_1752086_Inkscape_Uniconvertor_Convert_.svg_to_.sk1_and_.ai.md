---
title: "Inkscape Uniconvertor Convert .svg to .sk1 and .ai"
date: 2011-05-07
forum: Art &amp; Design
---

### Post by coljohnhannibalsmith on 2011-05-07
Hello,

I own a T-Shirt shop on ***[www.spreadshirt.com]("http://www.spreadshirt.com")*** and ***[www.spreadshirt.co.uk]("http://www.spreadshirt.co.uk")***, and these sites often reject *pixel-art* for a variety of reasons, in favor of *vector-graphics.*

For example, a number of my recent ***.jpg*** files have been rejected for poor image quality.  These are images that I edited in GIMP to resolve these problems.

Spreadshirt perfers images in ***.ai ***format, which is the ***adobe-illustrator*** format.  I've read online that ***Inkscape,*** which I have installed, uses ***Uniconvertor,*** which uses ***potrace,*** to convert images to this format.  (*This explanation is begining to feel like the Russian Nesting Dolls thread.*)   First I tried this in Inkscape which only offers the ***.sk1*** format; so I tried it hoping I would be *closer* to getting my desired *.ai.*  This attempt resulted in the following output message: (and a 0 byte file).

[I][B]UniConvertor failed:

Cannot list directory /home/sophie/.uniconvertor:[Errno 2] No such file or directory: '/home/sophie/.uniconvertor'
ignoring it in font_path
Cannot list directory /home/sophie/.uniconvertor:[Errno 2] No such file or directory: '/home/sophie/.uniconvertor'
ignoring it in font_path
No plugin-type information in /usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/__init__.py
No plugin-type information in /usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/__init__.py
Cannot load plugin module sk1saver
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/plugins.py", line 73, in load_module
    desc)
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/sk1saver.py", line 249, in <module>
    from app.Graphics.image import CMYK_IMAGE
ImportError: cannot import name CMYK_IMAGE
When importing plugin sk1saver
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/plugins.py", line 190, in __call__
    module = self.load_module()
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/plugins.py", line 73, in load_module
    desc)
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/sk1saver.py", line 249, in <module>
    from app.Graphics.image import CMYK_IMAGE
ImportError: cannot import name CMYK_IMAGE
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/uniconvertor/__init__.py", line 88, in uniconv
    saver(doc, output_file)
  File "/usr/lib/pymodules/python2.7/uniconvertor/app/plugins/plugins.py", line 194, in __call__
    % {'name':self.module_name})
app.events.skexceptions.SketchError: Cannot load filter sk1saver
[/B]
[/I]Having failed at the previous attempt, I tried using *Uniconvertor* directly, which produced the following output message: ( and an ***.ai*** which could 'not' be opened as a ***.pdf***).

[B][I]sophie@sophie-laptop:~$ uniconvertor '/home/sophie/Desktop/Metro_Badges/Metro_Police5a_uk.svg'  '/home/sophie/Desktop/Metro_Badges/Metro_Police5a_uk.ai' 
Cannot list directory /home/sophie/.uniconvertor:[Errno 2] No such file or directory: '/home/sophie/.uniconvertor'
ignoring it in font_path
Cannot list directory /home/sophie/.uniconvertor:[Errno 2] No such file or directory: '/home/sophie/.uniconvertor'
ignoring it in font_path
No plugin-type information in /usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/__init__.py
No plugin-type information in /usr/lib/pymodules/python2.7/uniconvertor/app/plugins/Filters/__init__.py
sophie@sophie-laptop:~$ 

[/I][/B]This seems to share much with the previous example, only with truncated output.

***This certainly appears to be a bug or a corruption of some kind.***

Since I recently upgraded to Natty, there may also be some compatibility issues.

Whatever the case, I'm happy to receive some better educated opinions.

[B][I]*Also, as an aside, It would be helpful, if .ai's could be rendered by Linux/Ubuntu in the thumbnail view; so that I could tell at-a-glance if the file was created successfully.

[IMG]http://cdn1.iconfinder.com/data/icons/Fold_CS5/512/Illustrator.png[/IMG]
[/I][/B]

---

### Post by prokoudine on 2011-05-09
> **coljohnhannibalsmith said:**
> 
Spreadshirt perfers images in ***.ai ***format, which is the ***adobe-illustrator*** format.  I've read online that ***Inkscape,*** which I have installed, uses ***Uniconvertor,*** which uses ***potrace,*** to convert images to this format.

I'm afraid you were misinformed. Inkscape uses UniConverter for opening and saving various vector images. AI is not among those that can be saved from Inkscape.

Potrace has nothing to do with UniConverter whatsoever. It is used by Inkscape internally for tracing bitmap images to vector graphics.

Likewise .sk1 file format has nothing to do with .ai. It's a file format by sK1 vector graphics editor.

In general, saving to PDF from Inkscape should suffice. If the print shop can open .ai, it will be able to open .pdf just as well. All versions of Adobe Illustrator since v9 released in early 2000s use PDF in .ai files for compatibility.

However, if you have UniConvertor installed, please use its simple UI for conversion. Then you could convert tour SVG file created with Inkscape to AI file. Please note, however, the AI file is likely to be in older file format. In former Ubuntu the user interface for UC used to be in Applications > Graphics menu. How to start it in Unity, I really have no clue, because I haven't upgraded to 11.04 yet. 

> **coljohnhannibalsmith said:**
> Also, as an aside, It would be helpful, if .ai's could be rendered by Linux/Ubuntu in the thumbnail view; so that I could tell at-a-glance if the file was created successfully.

I'm not entirely sure, but they should be rendered, if you have Ghostscript installed.

---

### Post by coljohnhannibalsmith on 2011-05-15
> **prokoudine said:**
> I'm not entirely sure, but they should be rendered, if you have Ghostscript installed.

***[COLOR=Blue]I checked; and it's not...[/COLOR]***

Also, I'd still like to know what the errors mean and how to correct them...

BTW,  Spreadshirt responded to my email and stated that they 'can' use SVGs; but suggested I use the .eps format instead.  Definately good-news; but I wish they had stated this in their tutorial, or ***anywhere*** on their site...





[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

