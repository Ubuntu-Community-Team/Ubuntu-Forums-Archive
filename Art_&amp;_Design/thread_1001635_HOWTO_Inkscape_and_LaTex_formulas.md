---
title: "HOWTO: Inkscape and LaTex formulas"
date: 2008-12-04
forum: Art &amp; Design
---

### Post by rlopez on 2008-12-04
Inkscape is a great program if you want to generate vector graphics. If you don't have it, please type

```
sudo apt-get install inkscape
```

Imagine now that you want to generate a figure for your scientific paper (or whatever). Actually, what you want is that this figure has some embedded LaTex formulas. 

To show how to do this with Inkscape and LaTex is the aim of this HOWTO.

Step 1
------
You will need to have LaTex in your system. Check this: [https://help.ubuntu.com/community/LaTeX]("https://help.ubuntu.com/community/LaTeX")

Step 2
------
We need an extension for Inkscape called textext. [Link to the official web page]("http://pav.iki.fi/software/textext/").

Download the last release from the previous web page. I installed this [textext-0.4.4.tar.gz]("http://pav.iki.fi/software/textext/textext-0.4.4.tar.gz") (it was the latest version when I did this tutorial ;) ).
```
 wget http://pav.iki.fi/software/textext/textext-0.4.4.tar.gz 
```
Untar the Textext package and copy its files to
Unpack of the Textext package and copy its files to ~/.config/inkscape/extensions/

```

tar xvfz textext-0.4.4.tar.gz
mv textext-0.4.4/* ~/.config/inkscape/extensions/

```


Step 3
------

Install the package pdf2svg. Since Ubuntu 8.10, the package is already in the repositories. 
```
sudo apt-get install pdf2svg
```

For older versions of Ubuntu you can download it from [here]("http://www.cityinthesky.co.uk/pdf2svg.html"). Unpack the file and make the executable
```

tar -zxf pdf2svg-0.2.1.tar.gz
cd pdf2svg-0.2.1
./configure --prefix=/usr/local
make
sudo make install

```


Step 4
------

Restart Inkscape. To create a new LaTeX object, choose Effects -> Tex Text, and type in your LaTeX code. 
The dialog has two additional fields:
-Preamble file: name of a LaTeX preamble file, where you can put common definitions.
-Scale factor: this affects how much a newly created LaTeX object is magnified. You can later change/reset this via Object -> Transform -> Matrix.

Afterwards, the object can be re-edited by selecting it and choosing Effects -> Tex Text again.


**Related Links & References **
- [http://pav.iki.fi/software/textext/](http://pav.iki.fi/software/textext/)


**Change Log:**
March, 8, 2011 - Instructions for Ubuntu 10.04
January, 26, 2009 - Instructions for Ubuntu 8.10.
First version December,4th,2008

---

### Post by aimonas on 2009-04-05
Thanks for the very useful post! I would like to contribute to the information about textext in inkscape by submitting what I did to assign a keyboard shortcut for textext, since the navigation with mouse might become tiresome when one wants to edit and write many things. For advanced users this should be trivial, but I think it will be helpful for users like me:

So, first enter the terminal

```
sudo gedit /usr/share/inkscape/keys/default.xml
```

Now I disabled the ctrl+shift+s associated to action "Save as" by commenting the corresponding lines:

[I]<!--bind key="s" modifiers="Ctrl,Shift" action="FileSaveAs" display="true"/>
  <bind key="S" modifiers="Ctrl,Shift" action="FileSaveAs" /-->[/I]

to assign it to textext at the end of the file (before </keys>)through

[I]<bind key="s" modifiers="Ctrl,Shift" action="org.ekips.filter.textext" display="true"/>
<bind key="S" modifiers="Ctrl,Shift" action="org.ekips.filter.textext" />
[/I]

The tag in action is the id from the textext.inx file.

Restart Inkscape and it should be ready to launch textext with Ctrl+shift+s


greetings
aimonas

---

### Post by aimonas on 2009-11-02
Hello everyone, I 've just installed 9.10 and tried to configure the TexText extension to Inkscape, according to the guidelines posted above, which were working up to 9.04 (I don't remember the corresponding version of Inkscape). Unfortunately, I couldn't succeed with Inkscape 0.47 in 9.10.

Can anyone give me a feedback about the functionality of TexText in the latest version of Inkscape?

Cheers

[COLOR="Red"]SOLUTION:[/COLOR] For Inkscape 0.47 copy the textext.* in ~/.config/inkscape/extensions/ ([[COLOR="Blue"]updated installation instructions[/COLOR]]("http://www.elisanet.fi/ptvirtan/software/textext/index.html"))

---

### Post by Craigacp on 2010-03-22
Or you can just install pstoedit from the Ubuntu repositories, in addition to Inkscape and LaTeX, then restart Inkscape (if its already running). This enables the built in LaTeX plugin in Inkscape. You can't edit the LaTeX once its been generated but its much easier to install.

---

### Post by GermanGiant on 2010-03-23
I've been meaning to learn LaTeX for a while now and this inspired me to take it up one of these days when I have more time.

---

### Post by anjames on 2010-05-03
Had some trouble installing in 9.10, but figured it out eventually.

The above from aimonas regarding the new config directory (~/.config/inkscape/extensions/) in 9.10 may be useful, but I just put everything in the /usr/share/inkscape/extensions directory with the other extensions, so now textext is available to all users.

Also, for some reason when I extracted the files there they had insufficient permissions (ie not readable by a typical user) so inkscape reported errors at startup:

[INDENT]$ inkscape

** (inkscape:21130): CRITICAL **: Inkscape::Extension::Extension* Inkscape::Extension::build_from_reprdoc(Inkscape::XML::Document*, Inkscape::Extension::Implementation::Implementation*): assertion `doc != NULL' failed

** (inkscape:21130): WARNING **: Unable to create extension from definition file /usr/share/inkscape/extensions/textext.inx.
[/INDENT]
The fix for this was:

[INDENT]sudo chown root:root /usr/share/inkscape/extensions/textext*
sudo chmod a+rX /usr/share/inkscape/extensions/textext*
[/INDENT]
So now I have under a menu called 'Extensions' (not Effects as previously suggested) an entry called Tex Text, which works as expected.

After running the extension though, it reports the following annoying message in a popup window:

[INDENT]/usr/share/inkscape/extensions/textext.py:55: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, sys, tempfile, traceback, glob, re, md5, copy
[/INDENT]

Works otherwise now.

---

### Post by cortiver on 2010-05-22
To suppress the DeprecationWarning popup, you can add the bolded lines to textext.py (near line 54):

```

import sys, os, glob, traceback, platform
sys.path.append('/usr/share/inkscape/extensions')
sys.path.append(r'c:/Program Files/Inkscape/share/extensions')
sys.path.append(os.path.dirname(__file__)

**# Suppress the DeprecationWarning when importing md5**
**import warnings**
[B]warnings.simplefilter("ignore", DeprecationWarning)
[/B]
import inkex
import os, sys, tempfile, traceback, glob, re, copy, md5
from lxml import etree

```

---

### Post by chris billington on 2010-06-01
> **cortiver said:**
> To suppress the DeprecationWarning popup, you can add the bolded lines to textext.py (near line 54):

```

import sys, os, glob, traceback, platform
sys.path.append('/usr/share/inkscape/extensions')
sys.path.append(r'c:/Program Files/Inkscape/share/extensions')
sys.path.append(os.path.dirname(__file__)

**# Suppress the DeprecationWarning when importing md5**
**import warnings**
[B]warnings.simplefilter("ignore", DeprecationWarning)
[/B]
import inkex
import os, sys, tempfile, traceback, glob, re, copy, md5
from lxml import etree

```

A slightly more aesthetic fix is to apply this [[COLOR="Red"]patch[/COLOR]]("http://bitbucket.org/pv/textext/issue/1/module-md5-deprecated-in-python-26#comment-44998") to texttex.py, which replaces use of the deprecated md5 module with the hashlib module.

What a great extension!

---

### Post by gsedej on 2010-09-24
Hi

I get error in ubuntu 10.04 patch from previous post and still same error.
tex text works if there is no "\", but when I say \begin or \fract or whaterver "\..." it says

```

Traceback (most recent call last):
  File "textext.py", line 211, in cb_ok
    self.callback(self.text, self.preamble_file, self.scale_factor)
  File "textext.py", line 370, in <lambda>
    converter_cls, old_node))
  File "textext.py", line 388, in do_convert
    new_node = converter.convert(text, preamble_file, scale_factor)
  File "textext.py", line 879, in convert
    return PdfConverterBase.convert(self, *a, **kw)
  File "textext.py", line 751, in convert
    self.tex_to_pdf(latex_text, preamble_file)
  File "textext.py", line 728, in tex_to_pdf
    exec_command(['pdflatex', self.tmp('tex')] + latexOpts)
  File "textext.py", line 597, in exec_command
    % (' '.join(cmd), p.returncode, out + err))
RuntimeError: Command pdflatex /tmp/tmpKkAra2/tmp.tex -interaction=nonstopmode -halt-on-error failed (code 1): This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(/tmp/tmpKkAra2/tmp.tex
LaTeX2e <2009/09/24>
Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo))

LaTeX Warning: Unused global option(s):
    [a0].

No file tmp.aux.

! LaTeX Error: Can be used only in preamble.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.7         \begin{document}
                            
? 
! Emergency stop.
 ...                                              
                                                  
l.7         \begin{document}
                            
!  ==> Fatal error occurred, no output PDF file produced!
Transcript written on tmp.log.

```

Any idea?

---

### Post by drorata on 2010-10-05
I'm using 10.04 and inkscape 0.47.
When ever I try to generate some TeX I get the following error:

> Traceback (most recent call last):
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 214, in cb_ok
    self.callback(self.text, self.preamble_file, self.scale_factor)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 373, in <lambda>
    converter_cls, old_node))
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 391, in do_convert
    new_node = converter.convert(text, preamble_file, scale_factor)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 755, in convert
    self.pdf_to_svg()
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 853, in pdf_to_svg
    + pstoeditOpts)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 600, in exec_command
    % (' '.join(cmd), p.returncode, out + err))
RuntimeError: Command pstoedit -f plot-svg /tmp/tmpj_9D0N/tmp.pdf /tmp/tmpj_9D0N/tmp.svg -dt -ssp -psarg -r9600x9600 failed (code -11): pstoedit: version 3.50 / DLL interface 108 (build Jan 25 2010 - release build - g++ 4.4.3) : Copyright (C) 1993 - 2009 Wolfgang Glunz


This happens also after making the changes suggested in the patch mentioned above...

Any advice?

---

### Post by abid_naqvi83 on 2010-10-10
@*drorata*:

I had the same problem. The solution (if you can call it one) is remarkably simple although it did take me a whole day and a considerable head-ache to realize it. Basically all mathematical expressions in TexText need to be enclosed in a pair of $ (dollar signs). So for instance to write Newton's Second Law use:

```
$\vec{F}=m \vec{a}$
```

and you should be set.


I also changed the owner:group of all the textext* files in the directory to root and made them executable by all as follows (first navigate to the folder containing these files):

```
sudo chown root:root textext*
sudo chmod a+rX /textext*
```

but I don't think that was strictly necessary to solve this particular problem.

---

### Post by drorata on 2010-10-11
I knew the '$' issue - somehow I still have a problem.

For example, if the input is: $\sqrt{-1}=i$, then as an error I get:

> Traceback (most recent call last):
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 214, in cb_ok
    self.callback(self.text, self.preamble_file, self.scale_factor)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 373, in <lambda>
    converter_cls, old_node))
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 391, in do_convert
    new_node = converter.convert(text, preamble_file, scale_factor)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 755, in convert
    self.pdf_to_svg()
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 853, in pdf_to_svg
    + pstoeditOpts)
  File "/home/drorata/.config/inkscape/extensions/textext.py", line 600, in exec_command
    % (' '.join(cmd), p.returncode, out + err))
RuntimeError: Command pstoedit -f plot-svg /tmp/tmpC5fz1h/tmp.pdf /tmp/tmpC5fz1h/tmp.svg -dt -ssp -psarg -r9600x9600 failed (code -11): pstoedit: version 3.50 / DLL interface 108 (build Jan 25 2010 - release build - g++ 4.4.3) : Copyright (C) 1993 - 2009 Wolfgang Glunz

I don't know... In the meanwhile, I use the LaTeX Formula tool, and it works. Up to the following error: "Segmentation fault". But It produces the desired result. So I'm more or less satisfied.

---

### Post by rtaker on 2010-10-23
hello everyone ... thank you very much for the helpful suggestions above ... however, even though i have done as instructed i still receive an error when i open the "Tex Text"-extension in inkscape ... frankly i am pretty lost here, so i would really appreciate any suggestions... btw, i am using ubuntu 9.10 and inkscape 0.47 .. thanks a lot in advance :)


>  Traceback (most recent call last):
  File "/usr/share/inkscape/extensions/textext.py", line 937, in <module>
    e.affect()
  File "/usr/share/inkscape/extensions/inkex.py", line 207, in affect
    self.effect()
  File "/usr/share/inkscape/extensions/textext.py", line 349, in effect
    % ';\n'.join(converter_errors))
RuntimeError: No Latex -> SVG converter available:
Pdf2Svg: Command pdf2svg failed: [Errno 2] No such file or directory;
PstoeditPlotSvg: Command pstoedit -help failed: [Errno 2] No such file or directory;
SkConvert: Command pstoedit failed: [Errno 2] No such file or directory
    

---

