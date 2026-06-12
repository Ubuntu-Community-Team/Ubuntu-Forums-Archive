---
title: "Howto install sK1, a powerful alternative for Illustrator and CorelDraw"
date: 2008-02-06
forum: Art &amp; Design
---

### Post by stani on 2008-02-06
This post is deprecated as sk1 now has an official ubuntu installer:
[http://sk1project.org/modules.php?name=Products&product=sk1](http://sk1project.org/modules.php?name=Products&product=sk1)

So this is for archival purposes only:
> Igor, the icon king of [Phatch]("http://photobatch.stani.be"), asked me if I could get sk1 to work on Ubuntu Gutsy. After playing around I found a way. Try this on your own risk.

I never heard about sk1 and looked it up on the website:
[http://sk1project.org/](http://sk1project.org/)

 Why sk1project?

    We think that sK1 is a powerful illustration program for the Linux platform that can substitute professional proprietary software like CorelDRAW or Adobe Illustrator and we hope the program and its derivatives will be helpful for you.

    About sK1 vector graphics editor

    sK1 is an open source vector graphics editor similar to CorelDRAW, Adobe Illustrator, or Freehand.
    First of all sK1 is oriented for PostScript processing.
    The major sK1 features:

    * CMYK colorspace support
    * CMYK support in Postscript
    * Cairo-based engine
    * Color managment
    * Universal CDR importer (7-X3 versions)
    * Modern Ttk based (former Tile widgets) user interface

It looks quite impressive and in five steps you can have it up and running on your Ubuntu Gutsy. It is a KDE application.

Read the instructions on my blog: [http://pythonide.blogspot.com/2008/02/howto-install-sk1-powerful-alternative.html](http://pythonide.blogspot.com/2008/02/howto-install-sk1-powerful-alternative.html)

This is a screenshot, turned into perspective with [Phatch]("http://photobatch.stani.be"):

[IMG]http://bp1.blogger.com/_KhIIKmJ4wWc/R6oAXFQJVNI/AAAAAAAAACU/gY2bNBohhU0/s1600/sk1_3d.png[/IMG]


---

### Post by digitalis_vulgaris on 2008-02-06
Hahahahah! I just planned to spread a word on forum. You were a step in from of me. :lolflag:

Author of application said sK1 can't be installed on Ubuntu. It's not true if you are Stani ! :)

---

### Post by digitalis_vulgaris on 2008-02-07
Author of sK1 just let me know that he set sK1 deb installer

[http://sk1project.org/downloads/sk1/sk1_0.9.0-rev326-1ubuntu10_i386.deb](http://sk1project.org/downloads/sk1/sk1_0.9.0-rev326-1ubuntu10_i386.deb)

---

### Post by ChameleonDave on 2008-02-08
I've installed it, and it doesn't work.

```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/sk1/__init__.py", line 44, in <module>
    import sys, app
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 11, in <module>
    from app.utils import output
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 62, in <module>
    from managers.colormanager import ColorManager
  File "/usr/lib/python2.5/site-packages/sk1/app/managers/colormanager.py", line 8, in <module>
    from lcms.lcms import cmsOpenProfileFromFile,cmsCreateTransform,cmsDoTransform, \
ImportError: No module named lcms.lcms

```

I won't be making a big effort to get it to work, as Inkscape and OpenOffice.org Draw (plus Adobe Illustrator on XP, very occasionally) already cover my needs

---

### Post by tbranham on 2008-02-08
Any reason to use this over Inkscape? I'm not a graphic designer, so forgive me if I'm missing something. I also like Xara, but it is very unstable on my machine. So what makes sK1 special?

---

### Post by stani on 2008-02-09
> **ChameleonDave said:**
> I've installed it, and it doesn't work.

```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/sk1/__init__.py", line 44, in <module>
    import sys, app
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 11, in <module>
    from app.utils import output
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 62, in <module>
    from managers.colormanager import ColorManager
  File "/usr/lib/python2.5/site-packages/sk1/app/managers/colormanager.py", line 8, in <module>
    from lcms.lcms import cmsOpenProfileFromFile,cmsCreateTransform,cmsDoTransform, \
ImportError: No module named lcms.lcms

```

I won't be making a big effort to get it to work, as Inkscape and OpenOffice.org Draw (plus Adobe Illustrator on XP, very occasionally) already cover my needs

How did you install it from my blog or the author site?

It looks like you didn't install:
sudo apt-get install liblcms-utils python-liblcms

Anyway as sk1 now provides official packages, this howto should not be followed anymore.

---

### Post by stani on 2008-02-09
> **tbranham said:**
> Any reason to use this over Inkscape? I'm not a graphic designer, so forgive me if I'm missing something. I also like Xara, but it is very unstable on my machine. So what makes sK1 special?

I have no idea. digitalis_vulgaris put me the challenge if I could install this on Ubuntu. Maybe he knows what is better about it than inkscape.

---

### Post by digitalis_vulgaris on 2008-02-09
This application is effort in right direction and it should bring on Ubuntu quality prepress tool in the future. The most common files from commercial software (ai, eps, crd) should be opened and edited with this application. Inkscape is made to be a tool for SVG files, but sK1 is made to be alternative for Illustrator, inDesign, Corel and Freehand.
Still need work on it but we all hopping the best... 
:)

---

### Post by Half-Left on 2008-02-09
Tried it in Hardy and it's unstable(possibility because it's built for Gusty), I'd like to see how it's performance is for blur or a complex image with blur.

Illustrator is just not easy to use, personally I find Inkscapes UI top notch and very easy to use.

---

### Post by ChameleonDave on 2008-02-10
> **stani said:**
> How did you install it from my blog or the author site?

It looks like you didn't install:
sudo apt-get install liblcms-utils python-liblcms

Anyway as sk1 now provides official packages, this howto should not be followed anymore.

I installed it using the DEB at [http://sk1project.org/modules.php?name=Products&product=sk1](http://sk1project.org/modules.php?name=Products&product=sk1)

All dependencies were satisfied.  If it has more dependencies than those declared in the DEB, then the DEB was incorrectly packaged.

---

### Post by digitalis_vulgaris on 2008-02-10
Did someone menage to install sk1 on 64bit 7.10 ?

---

### Post by 1richard on 2008-03-15
Hey Stani, I read that you understand sK1, I am using 8.04, but it is 64 amd.  Most new computers are 64bit, can you help me get it to run on 64 bit??  Thanks

---

### Post by stani on 2008-03-15
> **1richard said:**
> Hey Stani, I read that you understand sK1, I am using 8.04, but it is 64 amd.  Most new computers are 64bit, can you help me get it to run on 64 bit??  Thanks

What is the problem with 64 bit systems? What procedure did you follow? What error messages do you get?

---

### Post by zabec on 2008-05-12
> **stani said:**
> What is the problem with 64 bit systems? What procedure did you follow? What error messages do you get?

I get this on amd64 core2duo Hoary:

```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/sk1/__init__.py", line 44, in <module>
    import sys, app
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 11, in <module>
    from app.utils import output 
  File "/usr/lib/python2.5/site-packages/sk1/app/__init__.py", line 56, in <module>
    from _sketch import Point, Polar, PointType
ImportError: /usr/lib/python2.5/site-packages/sk1/app/modules/_sketchmodule.so: wrong ELF class: ELFCLASS32
```

Is there anything I could try?

Thanks.

---

### Post by Rino_ap_Codkelden on 2008-10-04
Hi, **1richard!**
I have run sK1 tomorrow))
I used an SVN image.
Sorry for my worse English))

---

### Post by frumple on 2008-10-22
I've just installed sK1 from svn on my amd64 Ubuntu 8.04. It wasn't simple, since there is no documentation on how to do it and which dependencies need to be satisfied.

In my case I had to install the following dependencies (actually some of them were already installed):

sudo apt-get install liblcms-utils python-liblcms python-imaging-tk kdebase-bin subversion tcl8.5-dev tk8.5-dev python-cairo-dev python-imaging python-reportlab python2.5-devlibcairo2-dev

After solving this issue, I downloaded the sK1 from subversion:

sudo svn co [https://sk1.svn.sourceforge.net/...ot/sk1/trunk/sK1](https://sk1.svn.sourceforge.net/...ot/sk1/trunk/sK1)  sK1

Then it was just building and installing

cd sK1
python setup.py build
python setup.py bdist_rpm
alien --to-deb sK1-0.9.0-0.x86_64.rpm
sudo gdebi-gtk sk1_0.9.0-1_amd64.deb

Everything set, just need to type sk1 on a terminal to start the program.

As a bonus the above commands also produce a deb package, really usefull to install on several machines :D

Why do we always want the bleeding edge programs? :lolflag:

sK1 looks really promising, opens every file that I need ;) 

Eduardo

---

### Post by lonewolf72 on 2008-11-18
Has anyone gotten this to work on Ibex? I have tried the deb and tried building the snapshot and neither has worked... i get errors both ways :(

---

### Post by smartboyathome on 2008-11-19
> **lonewolf72 said:**
> Has anyone gotten this to work on Ibex? I have tried the deb and tried building the snapshot and neither has worked... i get errors both ways :(

Inkscapes a better alternative to this IMO. I remember trying it, and I didn't feel like I could do as much with it as with Inkscape, and it felt slow.

---

### Post by mircea.postolache on 2009-02-04
I followed frumple's steps and it worked. I have Ubuntu 8.04 (64). 
I think python2.5-devlibcairo2-dev is not needed in the apt-get install line because it will say it's not found. Instead it is requested by some other package from the list and apt-get will point you to the package that matches your installed system.

Thanks a lot.

---

### Post by stani on 2009-05-20
I've made packages for Jaunty and Intrepid in my PPA repository (including 64 bit):
[http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html](http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html)

---

### Post by burner69 on 2010-12-14
sK1 install on ubuntu10.04
Ubuntu Software Center
type in the search 'sK1'
install python-uniconvertor

[http://sk1project.org/modules.php?name=Products&product=sk1&op=download](http://sk1project.org/modules.php?name=Products&product=sk1&op=download)
download for OS you have
install the three packages: I installed in this order
python-sk1libs-0.9.2....deb
python-sk1sdk-0.9.1....deb
python-sk1-0.9.1....deb

Alt-F2
type sK1 and press run

---

### Post by kmrs75 on 2011-01-11
that is the same way we got it to install very easy - 

we use it alot for our work - alot of times we will get a CDR or AI file and we cant open it very easy or convert it - sk1 will open most of them. however there is a few that will not open correct. i think it was the ver. of the file it was originaly saved as. 


> **burner69 said:**
> sK1 install on ubuntu10.04
Ubuntu Software Center
type in the search 'sK1'
install python-uniconvertor

[http://sk1project.org/modules.php?name=Products&product=sk1&op=download](http://sk1project.org/modules.php?name=Products&product=sk1&op=download)
download for OS you have
install the three packages: I installed in this order
python-sk1libs-0.9.2....deb
python-sk1sdk-0.9.1....deb
python-sk1-0.9.1....deb

Alt-F2
type sK1 and press run

---

