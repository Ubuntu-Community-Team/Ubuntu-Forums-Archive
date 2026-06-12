---
title: "Fractals and fractal generators"
date: 2009-08-17
forum: Art &amp; Design
---

### Post by mystmaiden on 2009-08-17
:)  Any fractal folks about? 

Before I switched over to Linux I had fiddled a bit with Apophysis but didn't really learn the program before axing windows.  I loaded xaos and another fractal generator but they don't look the same as Apophysis did, nor do the fractals look as pretty or as refined as the ones I often see on renderosity. I know post work is done on them, but there is a big difference. Does that depend on what script you run to produce the fractal? I notice Apophysis is called a fractal flame generator, is there something more similiar to it for Ubuntu? I downloaded the .deb for gnofract but it doesn't install, install button is inactive. My google search didn't net much.

mystmaiden

---

### Post by heathenx on 2009-08-17
Fractal4D, which is an Adobe Air app, works great on Ubuntu. I use it from time to time. You can export the fractal to png when done. You can toss that into Inkscape or Gimp and add extra things. ;)

[http://mattkenefick.com/blog/2008/11/fractal4d-first-release/](http://mattkenefick.com/blog/2008/11/fractal4d-first-release/)

Also, I still use the old cross-platform Fyre app. It's getting on in age but still works pretty well. I made a short-lived wallpaper for my Ubuntu desktop a while ago. [http://is.gd/2l4AI](http://is.gd/2l4AI)

[http://fyre.navi.cx/](http://fyre.navi.cx/)

---

### Post by mystmaiden on 2009-08-20
Thank you so much, heathenx. I downloaded fyre and had lots of fun with it - had to make myself not just sit and watch it endlessly! Very nice flame on the wallpaper you made, too! 

mystmaiden

---

### Post by mcduck on 2009-08-20
One more cool app, although not exactly fractal-related, would be Evolvotron.

It creates pretty nice images in a cool way. It offers you a selection of images, then you click the one you like most and it will create a new set of images based on the features of the picture you selected. Keep on clicking the images you'll soon have pretty nice looking images. Then yu can render the ones you like in larger size.

[http://www.bottlenose.demon.co.uk/share/evolvotron/]("http://www.bottlenose.demon.co.uk/share/evolvotron/")
(it's available in Ubuntu's repositories)

---

### Post by mystmaiden on 2009-08-22
Thanks, mcduck, I'll check it out - sounds like fun

---

### Post by cascade9 on 2009-08-22
An exhaustive list of fractal software for linux here-

[http://freshmeat.net/articles/fractal-software](http://freshmeat.net/articles/fractal-software)

Theres also apophysis. Pity it needs to run under wine. 

[http://www.apophysis.org/](http://www.apophysis.org/)

---

### Post by ROY.G.BIV on 2009-08-22
Just wanted to say thanks for providing all this info. I'm a big fractal nut myself and will surely enjoy some of these immensely.  So far I've downed Fractal4d, Evolvotron and Fyre, though I will check out the list that cascade 9 posted.

---

### Post by atawapal on 2010-05-28
Hello,
When I try to install gnofract 4d, look what happens:

root@PC-theo:/home/theo/Bureau/gnofract4d# ./setup.py install
Traceback (most recent call last):
  File "./setup.py", line 29, in <module>
    from buildtools import my_bdist_rpm, my_build, my_build_ext, my_install_lib
ImportError: No module named buildtools

I just extracted the folder I had downloaded in another folder that I placed anywhere, because I don't know where it has to be located...
I have installed C++, ....many things...GTK+
Please, help..

---

### Post by barx on 2011-01-02
mystmaiden You must try Fyre, is like Apopysis.

Here's the link:

[COLOR="Red"]**[http://fyre.navi.cx/]("http://fyre.navi.cx/")**[/COLOR]

It's Amazing, I don't Understand why I didn't find before a Math Proyect.

Check it out the Flickr Gallery of this guy.


:KS[**[COLOR="YellowGreen"]David Trowbridge's Fyre Gallery[/COLOR]**]("http://www.flickr.com/photos/davidtrowbridge/sets/72157600306325564/with/528701646/")

[IMG]http://farm2.static.flickr.com/1157/528766132_043c95af8c_m_d.jpg[/IMG][IMG]http://farm2.static.flickr.com/1163/528784543_0165d19df8_m.jpg[/IMG][IMG]http://farm2.static.flickr.com/1028/528883485_dc056ffb55_m.jpg[/IMG]


He also create wooden music instruments, well, anyway his program is great xD.

[**[COLOR="Blue"]Deb package[/COLOR]**]("http://releases.navi.cx/fyre/fyre_1.0.0-1_i386.deb")

```
wget http://releases.navi.cx/fyre/fyre_1.0.0-1_i386.deb
```

I've installed on my Ubuntu AMD forcing the deb.

- Intel install
```
sudo dpkg -i fyre_1.0.0-1_i386.deb
```
- Amd Install
```
sudo dpkg -i --force-architecture fyre_1.0.0-1_i386.deb
```

If this really don't amaze you, then you didn't have childrenhood or something :lolflag:

The proyect is static since 2006, seems that a second version would be ready , but that link to the page does not exist.

---

### Post by cascade9 on 2011-01-02
I migth have to try give Frye a go, since I changed monitors I cant find any fractals I like in my native resolution (1920x1080) ;)

---

### Post by PayPaul on 2011-09-28
> **barx said:**
> mystmaiden You must try Fyre, is like Apopysis.

Here's the link:

[COLOR="Red"]**[http://fyre.navi.cx/]("http://fyre.navi.cx/")**[/COLOR]

It's Amazing, I don't Understand why I didn't find before a Math Proyect.

Check it out the Flickr Gallery of this guy.


:KS[**[COLOR="YellowGreen"]David Trowbridge's Fyre Gallery[/COLOR]**]("http://www.flickr.com/photos/davidtrowbridge/sets/72157600306325564/with/528701646/")

[IMG]http://farm2.static.flickr.com/1157/528766132_043c95af8c_m_d.jpg[/IMG][IMG]http://farm2.static.flickr.com/1163/528784543_0165d19df8_m.jpg[/IMG][IMG]http://farm2.static.flickr.com/1028/528883485_dc056ffb55_m.jpg[/IMG]


He also create wooden music instruments, well, anyway his program is great xD.

[**[COLOR="Blue"]Deb package[/COLOR]**]("http://releases.navi.cx/fyre/fyre_1.0.0-1_i386.deb")

```
wget http://releases.navi.cx/fyre/fyre_1.0.0-1_i386.deb
```

I've installed on my Ubuntu AMD forcing the deb.

- Intel install
```
sudo dpkg -i fyre_1.0.0-1_i386.deb
```
- Amd Install
```
sudo dpkg -i --force-architecture fyre_1.0.0-1_i386.deb
```

If this really don't amaze you, then you didn't have childrenhood or something :lolflag:

The proyect is static since 2006, seems that a second version would be ready , but that link to the page does not exist.
Fyre is in the repositories but the install takes infinitely longer than any other install from the Software center I've ever seen. How do I halt it and try from the deb or from Synaptic?

---

### Post by Dry Lips on 2011-10-02
> **PayPaul said:**
> Fyre is in the repositories but the install takes infinitely longer than any other install from the Software center I've ever seen. How do I halt it and try from the deb or from Synaptic?

I get these error messages when I try to install Fyre from the 
Ubuntu Software Centre:

> **Requires installation of untrusted packages**
[I]The action would require the installation of packages 
from unauthenticated sources.[/I]> **Failed to download package files**
*Check your Internet connection.*

---

### Post by PayPaul on 2011-10-02
Somehow it finally installed. Been playing around with it a bit. Shows promise yet it's not apophysis.

---

### Post by Dry Lips on 2011-10-02
I'm still not allowed to install it from the Software Centre... 
However ```
sudo apt-get install fyre
``` works.

---

### Post by PayPaul on 2011-10-02
> **Dry Lips said:**
> I'm still not allowed to install it from the Software Centre... 
However ```
sudo apt-get install fyre
``` works.
Will that command work for any program that's linux based? I'm thinking it must be something in the repository or even a program you've compiled from source.

---

### Post by Dry Lips on 2011-10-02
> **PayPaul said:**
> Will that command work for any program that's linux based? I'm thinking it must be something in the repository or even a program you've compiled from source.

It must be in the repos. For packages that's not in the repos, 
you normally download the package and use dpkg instead of apt-get...
(And some programs that you download comes with installation scripts.)

---

### Post by PayPaul on 2011-10-02
Download the package and then use dpkg in the terminal? Would that be a deb package only? "dpkg" means download package?

---

### Post by Dry Lips on 2011-10-02
> **PayPaul said:**
> Download the package and then use dpkg in the terminal? Would that be a deb package only? "dpkg" means download package?

  	 	 	 	 	 	  1. Yes, that is one way of doing it. I think if you download deb's you can also 

just click on them, and it'll open in the Software Centre if I remember correctly.
 For information about the usage of dpkg, type ```
man dpkg
```in the
terminal. (To exit type :q)

2. Yes, dpkg would be for .deb's only.  
 3. Dpkg= package manager for Debian.

---

### Post by rojaasensei on 2011-10-02
I'm glad I spotted this old thread revived.  Fyre downloaded and installed easily on xubuntu 11.04 from the ubuntu software centre.

Fascinating app.

Thanks, everyone.

---

### Post by PayPaul on 2011-11-24
I found another one which is pretty cool except for the way it handles window sizing. It's called Mandelbulb.

[http://sites.google.com/site/mandelbulber/home](http://sites.google.com/site/mandelbulber/home)

Perhaps it's unrelated but could someone help me with my windows sizing problem. It does relate to this program in that it's a real nuisance trying to view both the commands window and any settings windows. See the attached screenshot for what I must put up with. My resolution currently is 1024 X 768 4:3 ratio.

---

### Post by debd on 2011-11-26
WOW!
fyre simply is great.
it installed for me without any pain by apt.

I made some :) 
here's one: [http://debdj.deviantart.com/art/seismic-diamond-270989078](http://debdj.deviantart.com/art/seismic-diamond-270989078)[]("http://dl.dropbox.com/u/21195653/my_geometric_wps.zip")

---

### Post by Dry Lips on 2011-11-27
A list of the fractal generators that I've got installed:

**-** **XaoS** **- Fractal zoomer.**
[B]
- Fraqtive[/B]

**-** **Fyre**

- And finally "Unix-based fractal generator" which in reality is a port 
of the MS-DOS classic **Fractint** (called **xfractint** in the repos). 
[https://secure.wikimedia.org/wikipedia/en/wiki/Fractint](https://secure.wikimedia.org/wikipedia/en/wiki/Fractint)
[http://fractint.org/](http://fractint.org/)

---

