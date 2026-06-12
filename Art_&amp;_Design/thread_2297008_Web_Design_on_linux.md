---
title: "Web Design on linux"
date: 2015-09-30
forum: Art &amp; Design
---

### Post by Mariciano on 2015-09-30
Hi, I just made Lubuntu my main OS and I was wandering if I could do web design just on linux without the need of dual boot just to use PS and Illustrator.

---

### Post by TheFu on 2015-09-30
If you **know** web design, then any editor will do.  vim, emacs, etc.  

IMHO.

I use vim. It is perhaps the most powerful editor in the world. In the right hands it is the most efficient editor available. From what I've seen, many people never learn enough to get passed noob skill level and use it like notepad. What a waste. I suppose it depends on the complexity of the desired layout.  We avoid javascript and use CSS for everything possible.

---

### Post by coldraven on 2015-10-01
Gimp can replace Photoshop for most people. 
[http://www.gimp.org/](http://www.gimp.org/)

Inkscape can replace Illustrator, see this article for news on this. (Also the comments section has some good info)
[http://www.theregister.co.uk/2015/05/19/inkscape_review/](http://www.theregister.co.uk/2015/05/19/inkscape_review/)

Both of these programs can be installed directly from the Software Centre. (or whatever it is called in Lubuntu)

---

### Post by marcus_s on 2015-10-19
Linux is capable of web-design and -development just like the other big players on the market. As I am doing web-design and development myself, I have a few recommendations regarding the tools you might want to use.

**Image editing and creation: GIMP**
As mentioned in the previous post, GIMP is quite powerful and offers an almost comparable toolset to its unrelated bigger brother, Photoshop. If you're used to Photoshop and switch over to GIMP, the usability is different - but you will get used to it. Available in the Ubuntu repos. Install with [FONT=courier new]sudo apt-get install gimp[/FONT]

Development tool: **various options**
Which tool you ultimately choose to write the code for your websites, is up to you. The choice of that depends on how comfortable you want to be. Here's my list of tools usable for that.

**Sublime Text** - Without any shadow of a doubt, this editor is among the most powerful on the market. It offers a large array of plugins that most definitely will suit any kind of web development, be it Javascript, PHP... you name it. Sporting a light footprint, it provides a suitable light IDE option for web development. Get it from [http://www.sublimetext.com](http://www.sublimetext.com)

**gEdit** - "Built-in" text editor in most Ubuntu flavors. This text editor has a plug-in system which also adds auto-complete, and offers syntax highlighting for a great number of languages, including PHP, CGI, and others. Install with [FONT=courier new]sudo apt-get install gedit[/FONT] if not present on system.

**(g)Vim** - You already mentioned to use VIM, I'm sure I don't need to explain to you what exactly it is and what it can (or rather what it cannot do). Also among the list of all-time favorites for development.

**NetBeans** - A more heavyweight contender for web-development, but allows the management of complete web-based solutions. Also free, but needs to be downloaded from [http://www.netbeans.org](http://www.netbeans.org) .

**Eclipse** - Originally tailored at Java development, this heavyweight contender has grown into an environment that suits web-development as well. Its usability takes some getting used to, but most definitely among the tools being used by developers. Get it from [http://www.eclipse.org/ide](http://www.eclipse.org/ide) .

I hope this provides you with some information to get started :)

---

### Post by Wadim_Korneev on 2015-10-26
Nearest to Dreamweaver in Linux is Quanta that comes with KDE's web development package.

There are zillions of text-based editors from generic ones to language specifc, just do a yum search for 'editor' and you'll find a bunch to get started with.
The 'best' is very subjective word, imho the 'best' is Vim, but I doubt you'd agree so you need to try and decide the 'best' all by yourself.

---

### Post by TheFu on 2015-10-26
> **Wadim_Korneev said:**
> just do a yum search 

"yum" isn't used on Ubuntu.  Replace that with **synaptic** or whatever interface you prefer to the package management system for Ubuntu. If you choose apt-get or aptitude, don't forget that tab completions can help find packages for the repos you have configured.  However, for a generic tool search like this, I'd probably use synaptic's search with a few different keywords.

I don't find much (any) use for Software Center. It doesn't show all the available packages, but when you want something really popular or don't want to see 30k+ packages, it does trim the list.

---

### Post by Mike_Sinclair on 2015-11-02
Hello, happy to have found this place. I have recently switched from over 10 years of Windows and Mac use to Ubuntu, and what a ride it's been. First and foremost i really do think all systems have their advantages and disadvantages - when it come's to working with graphics, 3d modelling and CSS design, i have come to learn that all the tools and programs thats out there for Ubuntu work out as good as on Win or Mac. GIMP can replace PS in many ways - but it's a little learning curve(some really good guides out there), hopefully we will get some creative cloud love to our end soon. Actually just started a new project, and it's all done on my new Ubuntu machine, and i'm pretty darn happy with it.  - Also, i have read the code of conduct, and this is my first post - but i want to make sure all newbies to Ubuntu understand that you can make beautiful designs and as good graphics on Ubuntu with Gimp, as with PS on the other systems. 

I'm really happy i made the switch, and i have come to love this very functional and good operating system!

---

### Post by Skaperen on 2015-11-05
i am reading *this thread* to see what web site development software i can run under ubuntu, natively.  i have written in HTML and Javascript before but i want to use GUI based site development this time.  it should either store the site files locally or upload them (hopefully with ssh, scp, or rsync over ssh).  i am running Apache on a virtual server with plans to move to AWS.

it looks like post #4 by marcus_s will be very useful.

---

### Post by maclenin on 2015-11-05
My web design stable...

1. leafpad
```
$ sudo aptitude install leafpad
```
2. gimp
```
$ sudo aptitude install gimp
```
3. inkscape
```
$ sudo aptitude install inkscape
```
...and away you go!

---

### Post by Portaro on 2015-11-27
Hey I am a hobbyst web designer or multimedia maker and I only use GNU/Linux .
A list of programs ?
 Do you need?:D

Here we go -
Natron (is similar to Nuke)
Krita 2.9 alpha is become with animation tools.
Pencil for 2D animation
toonloop
GIMP (image)
Darktable (image)
Inkscape (vector , logos)
Blender (well the better program for a designer , animation, logo, scenes, games forget the past thinking on the future this is Blender)
F4L (to Flash 2D animation - you need to find the github fork here - [https://github.com/ozkanpakdil/f4l](https://github.com/ozkanpakdil/f4l) tested on my 14.04)
Gnash to view flash animations 
Postearzor (poster software)
Scribus (flyers magazines)
Synfig studio (animation)
Tupi (animation)
winff (convert between formats)
convertgiftoavi (to make a avi of gif)
Discwrapper (to build cd covers)
Converseen (batch image convert)
Make human (model 3d of human can export to Blender)
Bluefish (CSS HTML)
Geany (all you need HTML, CSS...)
Filezilla (to up content to an host for example your site)
google web designer (a designer tool)
WDT (WEB developer tools for CSS HTML)
photivo (raw edit)
Raw therapee (raw)
Pyxeluvo (edit enhance  images photos)
Sunflow (photorealistic render)
SVGpage (put a page to an svg file)
potrace (to trace and convert between formats include .svg)
Sweet home 3d (interior home design)
TBO (to make comics)
Xara Extrem 
Xnview....

to video
Openshot
Avidemux
Lives
Pitivi
Cinelerra
Aegisub (subtitles)
gnome subtitles
DevedeNG
Imagination (custom slide DVD)
Mediainfo (info about media files)
Kdenlive
qstopmotion (to create stop & motion animations)
mkvinfo
ffmpeg
avconv
Ripperx
Qgifer (video based animator GIF)
GIMP Master video encoder (encode video of your image layers etc)
Xfburn
....



Music
LMMS
Audacious
Mixxx 
GNUEtertics (an distro to mount your own radio or to use in a Radio of your local)
Ocenaudio
....

I think I need to stop because there are an amazing amount of tools to Multimedia or Web design or content design or else in Ubuntu!

Oh I remember in sourceforge there are many tools also very good like tools to BD design , convert , PDF edit etc... ...

An example of a distro with big amount of tools to Designers is ArtistX -> [COLOR=#000000][FONT=Arial]http://artistx.org/            \ [/FONT][/COLOR]http://distrowatch.com/table.php?distribution=artistx but is discontinued if page is on air you can see many tools to all you need 3D, Animation, web dev, game dev, ....

The question is -  **search on google and in Ubuntu repositories**, and also ppa, sourceforge and github or others resources!

I hope this help, if anyone have a question comment please.

---

### Post by phatlocreal0 on 2016-03-04
Hi,

i'm ussually use wordpress for building my website and it still working good, i think for beginer should you it better.

Thanks,

---

### Post by aanyadsouza on 2016-04-21
> **Portaro said:**
> Hey I am a hobbyst web designer or multimedia maker and I only use GNU/Linux .
A list of programs ?
 Do you need?:D

Here we go -
Natron (is similar to Nuke)
Krita 2.9 alpha is become with animation tools.
Pencil for 2D animation
toonloop
GIMP (image)
Darktable (image)
Inkscape (vector , logos)
Blender (well the better program for a designer , animation, logo, scenes, games forget the past thinking on the future this is Blender)
F4L (to Flash 2D animation - you need to find the github fork here - [https://github.com/ozkanpakdil/f4l](https://github.com/ozkanpakdil/f4l) tested on my 14.04)
Gnash to view flash animations 
Postearzor (poster software)
Scribus (flyers magazines)
Synfig studio (animation)
Tupi (animation)
winff (convert between formats)
convertgiftoavi (to make a avi of gif)
Discwrapper (to build cd covers)
Converseen (batch image convert)
Make human (model 3d of human can export to Blender)
Bluefish (CSS HTML)
Geany (all you need HTML, CSS...)
Filezilla (to up content to an host for example your site)
google web designer (a designer tool)
WDT (WEB developer tools for CSS HTML)
photivo (raw edit)
Raw therapee (raw)
Pyxeluvo (edit enhance  images photos)
Sunflow (photorealistic render)
SVGpage (put a page to an svg file)
potrace (to trace and convert between formats include .svg)
Sweet home 3d (interior home design)
TBO (to make comics)
Xara Extrem 
Xnview....

to video
Openshot
Avidemux
Lives
Pitivi
Cinelerra
Aegisub (subtitles)
gnome subtitles
DevedeNG
Imagination (custom slide DVD)
Mediainfo (info about media files)
Kdenlive
qstopmotion (to create stop & motion animations)
mkvinfo
ffmpeg
avconv
Ripperx
Qgifer (video based animator GIF)
GIMP Master video encoder (encode video of your image layers etc)
Xfburn
....



Music
LMMS
Audacious
Mixxx 
GNUEtertics (an distro to mount your own radio or to use in a Radio of your local)
Ocenaudio
....

I think I need to stop because there are an amazing amount of tools to Multimedia or Web design or content design or else in Ubuntu!

Oh I remember in sourceforge there are many tools also very good like tools to BD design , convert , PDF edit etc... ...

An example of a distro with big amount of tools to Designers is ArtistX -> [COLOR=#000000][FONT=Arial]http://artistx.org/            \ [/FONT][/COLOR]http://distrowatch.com/table.php?distribution=artistx but is discontinued if page is on air you can see many tools to all you need 3D, Animation, web dev, game dev, ....

The question is -  **search on google and in Ubuntu repositories**, and also ppa, sourceforge and github or others resources!

I hope this help, if anyone have a question comment please.

Haha... But thank you for sharing such useful list ;)

---

### Post by ericoporto2008 on 2016-05-02
If you are too accustomed to Photoshop, you can try this: [http://www.rileybrandt.com/2014/03/09/photoshop-to-gimp/](http://www.rileybrandt.com/2014/03/09/photoshop-to-gimp/)  . These are essentially tips on making GIMP more Photoshop like. There is a single zip to do it but I haven't tested it : [http://www.webupd8.org/2014/02/gimp-get-photoshop-like-keyboard.html](http://www.webupd8.org/2014/02/gimp-get-photoshop-like-keyboard.html) .

Also I've read reports that Photoshop is working well under the [Wine]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32438") so if you are running and already paying it, it will cost nothing to try it also.

---

### Post by Dustino on 2016-05-05
> **coldraven said:**
> Gimp can replace Photoshop for most people. 
[http://www.gimp.org/](http://www.gimp.org/)

Inkscape can replace Illustrator, see this article for news on this. (Also the comments section has some good info)
[http://www.theregister.co.uk/2015/05/19/inkscape_review/](http://www.theregister.co.uk/2015/05/19/inkscape_review/)

Both of these programs can be installed directly from the Software Centre. (or whatever it is called in Lubuntu)

Thanks for the links the register page was something I needed to read.

GIMP works pretty well for what I have been using it for and I prior to was using CS6.

---

### Post by chien85 on 2016-05-31
Friends of mine use ubuntu and mac but Windows. I thought Mac is best for web programming.

---

### Post by xcdx100 on 2016-07-14
I find GIMP easier to handle than InkScape. I am unexperienced with web design related to art. My buddy is well exprncd in web design with GIMP.

---

### Post by Cyr4x on 2016-07-17
My tools of choice are Gimp and Gedit (replace with your favorite text editor). Believe me, you don't need anything more than that. Professional php devs mostly use NetBeans, but if you aren't focused on heavyweight apps, just mostly front-end/gfx, leave it.

---

