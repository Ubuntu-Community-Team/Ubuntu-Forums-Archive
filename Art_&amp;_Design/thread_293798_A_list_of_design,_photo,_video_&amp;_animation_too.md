---
title: "A list of design, photo, video &amp; animation tools"
date: 2006-11-05
forum: Art &amp; Design
---

### Post by uuwatti on 2006-11-05
I am trying to make a list of all design, photo & video tools that work/don't work on Ubuntu.
I am doing this for fun and to see if anyone else knows any good/bad tools
Please add your programs/experiences too.
Also check out [Getdeb.net]("http://www.getdeb.net/category.php?id=4") for few porgrams not listed here.
[SIZE="6"][COLOR="Red"]List now in WIKI form in Here:[/COLOR][/SIZE]
[SIZE="8"][COLOR="Red"][http://artlinux.wetpaint.com/]("http://artlinux.wetpaint.com/")[/COLOR][/SIZE]
[SIZE="4"][COLOR="Blue"]Please feel free to update the Wiki as I am very busy atm. and can't find time to do it.[/COLOR][/SIZE]
[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Photo Managers[/COLOR][/SIZE]


[SIZE="3"][COLOR="Red"]Picasa[/COLOR][/SIZE]
[Click on ubuntu package.]("http://picasa.google.com/linux/download.html") Googles photo
 managing software.

[SIZE="3"][COLOR="Red"]F-Spot[/COLOR][/SIZE] 
```
sudo aptitude install f-spot
``` 
F-Spot comes pre-installed on Edgy. For Dapper and others check the forums.

[SIZE="3"][COLOR="Red"]DigiKam[/COLOR][/SIZE] 
```
sudo aptitude install digikam
``` 
KDE photo manager. For KDE people.

[SIZE="3"][COLOR="Red"]Kitty Hooch[/COLOR][/SIZE]
[Info & Download]("http://www.kde-apps.org/content/show.php?content=45622")
Another KDE photo manager.

[SIZE="3"][COLOR="Red"]jBrout[/COLOR][/SIZE]
```
sudo gedit /etc/apt/sources.lst
```
add this: ```
deb http://jbrout.free.fr/download/debian binary/
```
and then: ```
sudo apt-get update
sudo aptitude install jbrout
```
Python-based photo manager [More info.]("http://jbrout.python-hosting.com/")

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Raster Graphics/Photography/RAW Tools[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]The Gimp[/COLOR][/SIZE] OSS
```
sudo aptitude install gimp
```
No need for description. Default in Gnome.
[SIZE="3"][COLOR="Red"]
PhotoPaint 8/Canvas 7[/COLOR][/SIZE] PROPRIETARY/FREE
[Download PhotoPaint]("http://linux.softpedia.com/progDownload/Corel-Photo-Paint-Download-3947.html")
[Download Canvas]("http://public.www.planetmirror.com/pub/canvas/linux/?fl=c")
Both too old. They won't work on newer systems. Canvas 7 depends on an older version kernel. I don't know what the problem with PhotoPaint is.

[SIZE="3"][COLOR="Red"]LightZone[/COLOR][/SIZE] PROPRIETARY/FREE
Tool for editing photographs. Good interface, quite fast.[Read more.]("http://www.macworld.com/2006/02/reviews/lightzone1/") 
[Download.]("http://www-old.lightcrafts.com/linux/download.php/")

[SIZE="3"][COLOR="Red"]Pixel[/COLOR][/SIZE] PROPRIETARY
[Demo version]("http://www.kanzelsberger.com/pixel/?page_id=12")
Check the big debate [here.]("http://www.ubuntuforums.org/showthread.php?t=89690")

[COLOR="Red"][SIZE="3"]Krita[/SIZE][/COLOR] OSS
```
sudo aptitude install krita
``` Never tried it.
Default in KDE. Has CMYK support. Developing fast. Old version in repos. More info and source [here.]("http://www.koffice.org/krita/")

[COLOR="Red"][SIZE="3"]Gogh[/SIZE][/COLOR] OSS
Gogh is a GNU/Linux bitmap graphics editor. It is designed to work with pressure-sensitive input devices, like a Wacom tablet. [Info & Download source]("http://www.goghproject.com/index.html")

[COLOR="Red"][SIZE="3"]Gimpshop[/SIZE][/COLOR] OSS
[Get .deb]("http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb")
Fork of The Gimp, shortcuts and menus like in photoshop, but otherwise it's the same old Gimp. [More info]("http://plasticbugs.com/")

[COLOR="Red"][SIZE="3"]blueMarine[/SIZE][/COLOR] OSS
[Get .deb]("https://bluemarine.dev.java.net/files/documents/5150/57352/blueMarine_0.9.EA9.1770_all.deb")
More info[/URL]
Windows/OSX equivalent: Adobe Lightroom, Apple Aperture

[COLOR="Red"][SIZE="3"]VIPS[/SIZE][/COLOR] OSS
[Info & source]("http://www.vips.ecs.soton.ac.uk/index.php?title=VIPS")
VIPS is a free image processing system. It aims to be about half-way between Photoshop and Excel. It is very bad at retouching photographs, but very handy for the many other imaging tasks that programs like Photoshop get used for. It is good with large images (images larger than the amount of RAM you have available), for working with colour and for research & development.

[COLOR="Red"][SIZE="3"]dcraw[/SIZE][/COLOR] OSS
```
sudo aptitude install dcraw
```
"program that decodes any raw image from any digital camera"

[COLOR="Red"][SIZE="3"]Video Related Picture Editor[/SIZE][/COLOR] OSS
[Info &source]("http://vrpe.sytes.net/")
VRPE want's to be a full-featured video-editor and maybe is sometime. Until in beta-state it can be seen as ImageMagick cluster-frontend...

[COLOR="Red"][SIZE="3"]DALiM LiTHO[/SIZE][/COLOR] PROPRIETARY
[Info]("http://www.dalim.com/en/products/litho/") (no download available :(
High-performance combination of well-known prepress applications for page layout, illustration and image retouching, making it the ultimate tool for anyone working in lithographics.

[COLOR="Red"][SIZE="3"]Metapixel[/SIZE][/COLOR] OSS
```
sudo aptitude install metapixel
```
[Info]("http://www.complang.tuwien.ac.at/schani/metapixel/")
Metapixel is a program for generating photomosaics. It can generate classical photomosaics, in which the source image is viewed as a matrix of equally sized rectangles for each of which a matching image is substitued, as well as collage-style photomosaics, in which rectangular parts of the source image at arbitrary positions (i.e. not aligned to a matrix) are substituted by matching images.

[COLOR="Red"][SIZE="3"]Hugin[/SIZE][/COLOR] OSS
```
sudo aptitude install hugin
```
Program for creating panorama pictures. Front-end for panorama tools. The GUI is a bit confusing, but the program works ok. Very complex. [Info here.]("http://hugin.sourceforge.net/") "sudo aptitude install enblend" to install enblend plugin for better compositing result.

[COLOR="Red"][SIZE="3"]Bibble Pro/Lite[/SIZE][/COLOR] PROPRIETARY
[Info + download demo.]("http://www.bibblelabs.com/") Professional Workflow and RAW Conversion software is designed to quickly and easily let you maximize the results from most major cameras and RAW formats.

[COLOR="Red"][SIZE="3"]PhotoGenics HDR[/SIZE][/COLOR] PROPRIETARY
[Info.]("http://www.idruna.com/products.html") Commercial program, $699. Website does not give information, but if I got it right this is a competitor for Photoshop. The website also has a demo version, but it doesn't work. .. Oh yeah, Its suitable for HDR editing as well

[COLOR="Red"][SIZE="3"]Rawstudio[/SIZE][/COLOR] OSS
```
sudo aptitude install rawstudio
```
[Info & source]("http://rawstudio.org/")
Rawstudio is an open source raw-image converter written in GTK+.

[COLOR="Red"][SIZE="3"]UFRaw[/SIZE][/COLOR] OSS
[Get .deb]("http://www.getdeb.net/download.php?release=421&fpos=0") Rumor has it that even photoshop has part of UFRaw code (or was it rawstudio..).


[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Vector Graphics[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]Inkscape[/COLOR][/SIZE] OSS
```
sudo aptitude install inkscape
``` I don't have experience with this one.

[COLOR="Red"][SIZE="3"]Xara Xtreme[/SIZE][/COLOR] OSS
```
sudo aptitude install xaralx
``` A winner. It really is a good substitute for Illustrator. Learn more [here.]("http://www.xaraxone.com/")

[COLOR="Red"][SIZE="3"]Sodipodi[/SIZE][/COLOR] OSS
```
sudo aptitude install sodipodi
``` I used it ages ago. I think Inkscape & Xara are now much more advanced(not sure). **DISCONTINUED**

[COLOR="Red"][SIZE="3"]Gestalter[/SIZE][/COLOR] OSS
[It's here.]("http://www.linotux.ch/gestalter/") I don't know much about this yet.

[COLOR="Red"][SIZE="3"]Dia[/SIZE][/COLOR] OSS
[CODE}sudo aptitude install dia[/CODE]
[Here here.]("http://www.gnome.org/projects/dia/") Dia is inspired by the commercial Windows program 'Visio', though more geared towards informal diagrams for casual use. It can be used to draw many different kinds of diagrams.

[COLOR="Red"][SIZE="3"]ivtools[/SIZE][/COLOR] OSS
[Follow this link.]("http://www.ivtools.org/ivtools/index.html")
ivtools (pronounced eye-vee-tools) is a suite of free X Windows drawing editors for PostScript, TeX, and web graphics production, as well as an embeddable and extendable vector graphic shell

[COLOR="Red"][SIZE="3"]Sketsa[/SIZE][/COLOR] PROPRIETARY
[Info here.]("http://www.kiyut.com/products/sketsa/index.html") Similar to Xara and Inkscape, but worse. And it's proprietary/non-free. Don't bother with it.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]3D software[/COLOR][/SIZE]


[COLOR="Red"][SIZE="3"]Art Of Illusion[/SIZE][/COLOR] OSS
```
wget http://prdownloads.sourceforge.net/aoi/ArtOfIllusion24-Linux.zip
unzip ArtOfIllusion24-Linux.zip -d aoi
cd aoi
./aoisetup.sh
```
stable and powerful enough to be used for serious, high end animation work. Many of its capabilities rival those found in commercial programs. Some of the highlights include subdivision surface based modelling tools, skeleton based animation, and a graphical language for designing procedural textures and materials.

[COLOR="Red"][SIZE="3"]SharpConstruct[/SIZE][/COLOR] OSS
[Download.]("http://sourceforge.net/project/showfiles.php?group_id=112386&package_id=121637&release_id=417142")
Open-source project similar to ZBrush. [Read more.]("http://blenderartists.org/forum/showthread.php?t=66369") An Ubuntu [package]("http://skulboxx.com/Ubuntu/sbx/") also exists, but it didn't work for me.
[SIZE="3"][COLOR="Red"]
Blender[/COLOR][/SIZE] OSS
```
sudo aptitude install blender
```
3D program with editing and compositing capabilities. Everyone should know this by now.[Info.]("http://www.blender3d.org")

[COLOR="Red"][SIZE="3"]Maya[/SIZE][/COLOR] PROPRIETARY/FREE VERSION EXISTS
Industry-standard 3D program. [PLE Edition]("http://usa.autodesk.com/adsk/servlet/index?siteID=123112&id=7639525") is free of charge. Otherwise.. expect to pay a lot, but also to get a lot. Most users will probably cope with Blender.
[SIZE="3"][COLOR="Red"]
K-3D[/COLOR][/SIZE] OSS
```
sudo aptitude install k3d
```K-3D features a robust plugin architecture and visualization pipeline, designed to scale to the needs of professional artists. K-3D has been written from the ground up to generate motion picture quality animation using RenderMan render engines. 
[More info here.]("http://www.k-3d.org/wiki/Main_Page") 

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Video Editing[/COLOR][/SIZE]
[SIZE="3"][COLOR="Red"]
Kino[/COLOR][/SIZE] OSS
```
sudo aptitude install kino
``` No experience yet. [Info.]("http://www.kinodv.org/")

[SIZE="3"][COLOR="Red"]LiVES[/COLOR][/SIZE] OSS
[Download .deb]("http://www.getdeb.net/download.php?release=558&fpos=0") Slow. Its good for working with smaller clips, but unusable for bigger ones. [More info.]("http://lives.sourceforge.net/")

[SIZE="3"][COLOR="Red"]Cinelerra[/COLOR][/SIZE] OSS
[Use this]("http://www.kiberpipa.org/%7Egandalf/ubuntu/README") or [this guide]("http://www.ubuntuforums.org/showthread.php?t=270037&highlight=cinelerra") to install. Crashes often. Is ugly. But it is a step in the right direction. A very comprehensive tool with lots of features.
 
[SIZE="3"][COLOR="Red"]Diva[/COLOR][/SIZE] OSS
[Download source.]("http://www.diva-project.org/wiki/Releases") This project looks pretty dead. The demo videos look good though. Hope someone resurrects this project. **Update: NOT DEAD **
[SIZE="3"][COLOR="Red"]
PiTiVi[/COLOR][/SIZE] OSS
```
sudo aptitude install pitivi
``` Starts with ```
pitivi --sync
```, but it doesn't do anything. Seems to be very simple to use.

[SIZE="3"][COLOR="Red"]MainActor[/COLOR][/SIZE] PROPRIETARY
[Demo version.]("http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.36Ubuntu6+mainactor-5.5-36.i386.ubuntu-6.06.deb") It's actually very usable. Fast. Not cheap. Good interface. Expensive. if you have used Premiere, you feel comfortable with this. Doesn't support very many codecs though. [Info.]("http://www.mainconcept.com/site/index.php?id=395")

[SIZE="3"][COLOR="Red"]ShotCut[/COLOR][/SIZE] OSS
Difficult to install. First you need mlt libraries. Get those from Jahshakas repository. 
Make sure you have all the dependencies explained here--> [Info.]("http://users.pandora.be/acp/shotcut/")
```
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
cvs -z3 -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/shotcut co shotcut
```
bootstrap, configure, make and make install. Tried this a few months back, can't remember if it worked properly or not.
But it definitely wasn't worth the trouble.

[COLOR="Red"][SIZE="3"]SciLab Aurora[/SIZE][/COLOR] OSS
```
sudo aptitude install scilab
wget http://kent.dl.sourceforge.net/sourceforge/scilab-aurora/aurora_linux.zip
unzip aurora_linux.zip
cd aurora
./aurora.sh
```
[Info.]("http://scilab-aurora.sourceforge.net/") Simple video editor that works quite well for a first version. It doesn't have any proper functionality yet, like editing, but you can play around with transitions. What I did find good about it is that it actually seems to be quite fast. Hope they carry on the development.(first release was end of september)

[COLOR="Red"][SIZE="3"]KDEnlive[/SIZE][/COLOR] OSS
[@Sourceforge]("http://kdenlive.sourceforge.net/index.php")
[Klik Install]("http://kdenlive.klik.atekon.de/")
KDE video editor using the MLT framework. The best choice after Blender for open source video editing.
use Treviño's repositories for installing via apt.
```
sudo gedit /etc/apt/sources.list 
```
add this:```
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
```
then:
```
sudo apt-get update
gpg --keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9 
gpg --export --armor 2D6CFB44DD800CD9 | sudo apt-key add -
sudo apt-get install kdenlive
```

[COLOR="Red"][SIZE="3"]Jumpcut[/SIZE][/COLOR] PROPRIETARY/FREE/ONLINE
[Use it!]("http://www.jumpcut.com") Yahoo-sponsored on-line video editor. Simple to use. Only Flashplayer required! Good tool for editing video straight to internet.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Video Compositing/Effects[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]D2 Nuke[/COLOR][/SIZE] PROPRIETARY
[Info.]("http://www.d2software.com/")
Another heavy-duty film compositor like Shake. Big, but justified price-tag.

[SIZE="3"][COLOR="Red"]SNICE[/COLOR][/SIZE] OSS
[@Sourceforge.]("http://sourceforge.net/projects/snice/")Need to compile from CVS. However there is no config file. So I don't know... However users say it's pretty good and stable for 0.1. But... there is no active development at all. **DISCONTINUED**
[SIZE="3"][COLOR="Red"]
Shake[/COLOR][/SIZE] PROPRIETARY
1-800-MY-APPLE Shake for Linux is available through Apple Pro Resellers for $4999. Heavy-duty compositing tool at a heavy-duty price. I've Never used it.
[SIZE="3"][COLOR="Red"]
ZS4[/COLOR][/SIZE] PROPRIETARY/FREE
[Download.]("http://devel.zs4.org/t@b_zweistein_linux_ubuntu32_0703161351.tar.gz")[/URL]  
Impressive features, but r-e-a-l-l-y  s-l-o-w. Still definitely the most interesting free video tool. New version and Ubuntu-specific build. I will try it later. 
[SIZE="3"][COLOR="Red"]
Jahshaka[/COLOR][/SIZE] OSS
[Instructions for installing]("http://www.jahshaka.org/index.php?option=com_mamblog&Itemid=55&task=show&action=view&id=112&Itemid=55") Very buggy, but it's alpha. Development slow. Very promising though.
[SIZE="3"][COLOR="Red"]
Cinepaint/Glasgow[/COLOR][/SIZE] OSS
```
sudo aptitude install cinepaint
```
Gimp-fork. Works now. HDR-Capable. Glasgow(next version) is here, but only for Windows!!!.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Vector Animation[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]Synfig[/COLOR][/SIZE] OSS
```
sudo aptitude install synfigstudio
```
For some reason this doesn't work on my Intel machine, but on my AMD machine it runs perfectly.
Looks promising. [More info.]("http://www.synfig.com/")

[SIZE="3"][COLOR="Red"]F4L[/COLOR][/SIZE] OSS
[Info.]("http://f4l.sourceforge.net/")Name says it all.. Flash 4 Linux. Haven't tried it. Apparently **DISCONTINUED**. Use UIRA Instead.[Install instructions.]("http://www.ubuntuforums.org/showthread.php?t=69156&highlight=f4l")

[SIZE="3"][COLOR="Red"]UIRA[/COLOR][/SIZE] OSS
[UIRA.org]("http://www.uira.org/")
Early development. qflash and f4l merged to form this project. I have problems getting it to work.
Someone with more experience with compiling qt apps might wanna give this a try.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]CAD[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]Archimedes[/COLOR][/SIZE] OSS
[Download.]("http://archimedes.incubadora.fapesp.br/portal") Link also includes installtion instructions and more information. Java-based CAD-tool.

[SIZE="3"][COLOR="Red"]gCAD3D[/COLOR][/SIZE] OSS
[Info & Download]("http://www.cadcam.co.at/freiter/gCAD3D_en.htm")
All the necessary info is on their website.

[SIZE="3"][COLOR="Red"]Cycas[/COLOR][/SIZE] PROPRIETARY/FREE FOR NON-COMMERCIAL USE
[Info & Download]("http://www.cycas.de/")
 CYCAS is a piece of architectural software for drafting and design in 2 + 3 dimensions. This seems really good.

[SIZE="3"][COLOR="Red"]GraphiteOne[/COLOR][/SIZE] PROPRIETARY/FREE FOR NON-COMMERCIAL USE
[Get it here. + Info.]("http://www.graphiteone-cad.com/en/index.htm")
GraphiteOne is a feature rich modular 3D CAD system designed for but not limited to mechanical construction.
This also seems really good.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Trad. Animation[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]Ktoon[/COLOR][/SIZE] OSS
[Download source.]("https://developer.berlios.de/project/showfiles.php?group_id=2960") There is .deb on these forums somewhere, but that didn't work for me.(no icons). Will try compiling this later. [Info.]("http://ktoon.toonka.com/")
[SIZE="3"][COLOR="Red"]
Plastic Animation Paper[/COLOR][/SIZE] PROPRIETARY/FREE VERSION EXISTS
[Download.]("http://www.plasticanimationpaper.dk/files/linux/pap4_0.tar.bz2")
Free version and payware version included. Its like animating on paper, but with a computer. [More info.]("http://www.plasticanimationpaper.dk/")

[SIZE="3"][COLOR="Red"]Anime Studio (Pro)[/COLOR][/SIZE] PROPRIETARY
[Info.]("http://www.e-frontier.com/article/articleview/1913/1/793?sbss=793") The program that used to be called MoHo. Linux version will be out soon.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Desktop Publishing[/COLOR][/SIZE]
[SIZE="3"][COLOR="Red"]
Scribus[/COLOR][/SIZE] OSS
```
sudo aptitude install scribus
```
Also available on Automatix.
Desktop publishing. Open-source equivalent of In-design or Quark. [Info.]("http://www.scribus.net/")

[SIZE="3"][COLOR="Red"]Laidout[/COLOR][/SIZE] OSS
[Download .deb]("http://downloads.sourceforge.net/laidout/laidout_0.06_i386.deb?modtime=1177566400&big_mirror=0")
Simple layout program. More info @ [laidout.org]("http://www.laidout.org/")

[SIZE="3"][COLOR="Red"]Scribus-ng[/COLOR][/SIZE] OSS
```
sudo aptitude install scribus-ng
```
Some kind of special/development version of scribus.

[SIZE="3"][COLOR="Red"]PageStream[/COLOR][/SIZE] PROPRIETARY
[Info + Download demo]("http://www.pagestream.org/") PageStream is a quality full featured desktop publishing/page layout program that gives you the tools you need to create the designs you desire. Everything from church newsletters to company perspectives, multi-volume product documentation to invitations for your family events can be created in PageStream. Full color brochures are almost as easy to create as a simple business card. 
[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Web Design[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]Nvu[/COLOR][/SIZE] OSS
```
sudo aptitude install nvu
```
Web authoring tool. **DISCONTINUED LOOK BELOW FOR KOMPOZER**. [Info.]("http://www.nvu.com/index.php")

[SIZE="3"][COLOR="Red"]Kompozer[/COLOR][/SIZE] OSS
[Download]("http://kompozer.net/") binaries & source.
Mozilla is continuing the Nvu Project now apparently.

[SIZE="3"][COLOR="Red"]Quanta Plus[/COLOR][/SIZE] OSS
```
sudo aptitude install quanta
```KDE web-development tool. [Info.]("http://quanta.kdewebdev.org/")


[SIZE="3"][COLOR="Red"]Aptana[/COLOR][/SIZE] OSS
[Info & Download]("http://aptana.com/")
[Installation instructions from binaries.]("http://ubuntuforums.org/showthread.php?t=315444&highlight=aptana")
[Installation via apt.]("http://www.aptana.com/forums/viewtopic.php?p=5092#5092")The Aptana IDE is a free, open-source, cross-platform, JavaScript-focused development environment for building Ajax applications. It features code assist on JavaScript, HTML, and CSS languages, FTP/SFTP support and a JavaScript debugger to troubleshoot your code.

[SIZE="3"][COLOR="Red"]qooxdoo[/COLOR][/SIZE] OSS
[http://qooxdoo.org/]("http://qooxdoo.org/")
GUI tool for creating AJAX-stuff.

[SIZE="3"][COLOR="Red"]OpenLaszlo[/COLOR][/SIZE] OSS
[Info]("http://www.openlaszlo.org/")
Something to do with web design not sure what.. yet

[SIZE="3"][COLOR="Red"]Bluefish[/COLOR][/SIZE] OSS
```
sudo aptitude install bluefish
```
Advanced HTML-editor.

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Font tools[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]FontForge[/COLOR][/SIZE] OSS
```
sudo aptitude install fontforge
```
Seems to be good substitute for Macromedia Fontographer and such. [Info]("http://fontforge.sourceforge.net/")

[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
[SIZE="5"][COLOR="Blue"]Other[/COLOR][/SIZE]

[SIZE="3"][COLOR="Red"]QDVDAuthor[/COLOR][/SIZE] OSS
```
sudo aptitude install qdvdauthor
``` DVD authoring. Crashes a lot, but has a good set of tools. [Info.]("http://qdvdauthor.sourceforge.net/")

[SIZE="3"][COLOR="Red"]Vexi[/COLOR][/SIZE] OSS
Vexi is a platform for creating and publishing Graphical User Interfaces that can be used over the Internet or an intranet. [More info & Download]("http://vexi.sourceforge.net/")

[SIZE="3"][COLOR="Red"]Knitting Pattern Creator[/COLOR][/SIZE] OSS
[Download]("http://linux.softpedia.com/get/Multimedia/Graphics/Knitting-Pattern-Generator-7558.shtml")
Knitting Pattern Generator is a Python script to convert image files (PNG, GIF, BMP, etc.) into knitting patterns.

[SIZE="3"][COLOR="Red"]Context Free Art[/COLOR][/SIZE] OSS
[Info & Download]("http://www.contextfreeart.org/mediawiki/index.php/Main_Page")
It's a program for creating pretty random (but beautiful) images.

[SIZE="3"][COLOR="Red"]Processing[/COLOR][/SIZE] OSS
[Info & Download]("http://processing.org/")
Processing is an open source programming language and environment for people who want to program images, animation, and sound. 
I've seen pretty incredible looking things created with this.

[SIZE="3"][COLOR="Red"]kuler[/COLOR][/SIZE] PROPRIETARY/FREE/ONLINE
[Use it!]("http://kuler.adobe.com") Adobe relased something for free! Kuler is a tool to help the designer in creating color-palettes. NOTE: Current version of Linux-Flash does not support Express Install, so we have to wait for this. Btw. It worked earlier...

[SIZE="3"][COLOR="Red"]LignumCAD[/COLOR][/SIZE] OSS
lignumCAD is a tool for designing furniture. [Download .rpm or source.]("http://lignumcad.sourceforge.net/doc/en/HTML/index.html") Link includes more info.

[SIZE="3"][COLOR="Red"]Stopmotion[/COLOR][/SIZE] OSS
```
sudo aptitude install stopmotion
```
Stopmotion is a free application for creating stop-motion animation movies. The users will be able to create stop-motions from pictures imported from a camera or from the harddrive, add sound effects and export the animation to different video formats such as mpeg or avi. 

[SIZE="3"][COLOR="Red"]ColorExplorer[/COLOR][/SIZE] OSS
[Download.]("http://billposer.org/Software/ColorExplorer.html#downloads")
ColorExplorer is a tool for exploring the color space and finding out how colors, color names, and numerical color specifications are related. 

[SIZE="3"][COLOR="Red"]Voodoo Camera Tracker[/COLOR][/SIZE] PROPRIETARY/FREE FOR NON-COMMERCIAL USE
[Download + info.]("http://www.digilab.uni-hannover.de/docs/manual.html")
"The voodoo camera tracker estimates camera parameters and reconstructs a 3D scene from image sequences. The estimation algorithm offers a full automatic and robust solution to estimate camera parameters for long video sequences. The results are useful for many applications like film production, 3D reconstruction or video coding." Works well with Blender also.

[SIZE="3"][COLOR="Red"]ColorWrite[/COLOR][/SIZE] PROPRIETARY/FREE
[Info + download.]("http://www.adaptiveview.com/cw/index.html") ColorWrite is a color chooser with an integrated CSS/HTML code generator. It allows you to define colors using RGB, HSV, CMY and CMYK, makes using web safe colors easy and now, with Version 1.1, ColorWrite  takes the guess work out of combining colors.

[SIZE="3"][COLOR="Red"]LProf[/COLOR][/SIZE] OSS
```
sudo aptitude install lprof
```
LPROF is the only open source ICC profiler with a graphical user interface. It can be used to create ICC version 2 compliant profiles for cameras, scanners and monitors. As such it fills a necessary niche in the emerging open source color management effort.

[SIZE="3"][COLOR="Red"]Monica[/COLOR][/SIZE] OSS
[Download binary]("http://www.pcbypaul.com/software/dl/monica-3.4_gcc-3.3.5.tar.bz2"). "Monica is a Monitor Calibration Tool. An easy way to get respectable color rendetion on your screen" [Info.]("http://www.pcbypaul.com/software/monica.html")

[SIZE="3"][COLOR="Red"]Coriander[/COLOR][/SIZE] OSS
```
sudo aptitude install coriander
```
Coriander is the Linux graphical user interface for controlling a Digital Camera through the IEEE1394 bus
[more info.]("http://damien.douxchamps.net/ieee1394/coriander/index.php")

[SIZE="3"][COLOR="Red"]MetaCam[/COLOR][/SIZE] OSS
```
sudo aptitude install metacam
```
A tool for editing picture meta-data.. right? correct me if i'm wrong.
[More Info.]("http://www.cheeseplant.org/~daniel/pages/metacam.html")

[SIZE="3"][COLOR="Red"]ExifTool[/COLOR][/SIZE] OSS
Does the same thing as MetaCam, I guess.. [DL + Info]("http://owl.phy.queensu.ca/~phil/exiftool/")
[B]----------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------[/B]
I added a bunch programs that I haven't tried yet, but are still in (early) development or look interesting. If you have any experience with these, add your comments
[COLOR="Red"]
Frameworks[/COLOR]
Stop-motion capture program. [Info & Download]("http://frameworks.polycrystal.org/")

[COLOR="Red"]Gephex[/COLOR]
Video effects generator. [Info & Download source]("http://www.gephex.org/") Seems like a tool for veejays.
[COLOR="Red"]
EffecTV[/COLOR]
Similar to Gephex, I think. [Info & Download source]("http://effectv.sourceforge.net/")

[COLOR="Red"]ARToolKit[/COLOR]
[Info & Download source]("http://www.hitl.washington.edu/artoolkit/")
> ARToolKit is a software library for building Augmented Reality (AR) applications. These are applications that involve the overlay of virtual imagery on the real world.  High-tech stuff.

[COLOR="Red"]Veejay[/COLOR]
Name says it all. [Info & Download source]("http://veejay.dyne.org/")

[COLOR="Red"]FreeJ[/COLOR]
```
sudo aptitude install freej
``` Veejay tool with streaming capabilities.

[COLOR="Red"]Celtx[/COLOR]
> Celtx is Pre-Production software for film, video, theatre, and animation. Look like planner/organizer for film pre/production work. [Info & Download]("http://celtx.com/")

[COLOR="Red"]
Moonlight 3D[/COLOR]
[Info & Download]("http://www.moonlight3d.eu/cms/") 3D modeling & Animation app.

[COLOR="Red"]gSculpt[/COLOR]
[Info & Install Instructions]("http://gsculpt.sourceforge.net/index.html") Subdiv modeling prog.

[COLOR="Red"]SIPToolbox[/COLOR]
[Info & Download]("http://siptoolbox.sourceforge.net/") Not sure what this is yet.

[COLOR="Red"]Moldeo[/COLOR]
Real-time effects and animation tool.. in other more veejay stuff... I think
[Download source & More Info.]("http://moldeo.computaciongrafica.com/principal/home/e-home.php?PHPSESSID=183e717032e03493844217442d613fcf")

[COLOR="Red"]Delta Compositor[/COLOR]
[Info & Download source]("http://deltacompositor.sourceforge.net/") Very early in development. But it looks really promising node-based compositor.

[COLOR="Red"]Vivia[/COLOR]
[@Sourceforge]("http://vivia.sourceforge.net/") Video editor. 0.1 just released.

[COLOR="Red"]JAnimationShop[/COLOR]
[@Sourceforge]("http://sourceforge.net/projects/janimationshop") Animation program written in java. There is something in the CVS. Not sure if this project is discontinued.
[COLOR="Red"]
Open Movie Editor[/COLOR]
[@Sourceforge]("http://openmovieeditor.sourceforge.net/HomePage") 0.02 released. Looks Similar to Diva, PiTiVi and Vivia.
[COLOR="Red"]
ISOBLOX[/COLOR] 
an isometric pixel art tool. [@Sourceforge]("http://sourceforge.net/projects/isoblox")

---

### Post by hikaricore on 2006-11-06
Very good list you'd made here :)

Just to let you know I've never been able to get Synfig to work either, tried compiling it on 3 systems now with all dependancies met and everything and it bombs out.  I'll have to try the apt method tho to see if I have any luck.

One thing you might want to add to Scribus is Scribus-NG, it's mostly a development build with more features, but may be more unstable than Scribus.

Otherwise good work :)  You found alot of stuff that I've not come across yet.  I'm working an a ubuntu desktop publishing system at work so some of this will come in handy.

---

### Post by dckirba on 2006-11-06
Nice list. very useful.

Blender is a great tool. Xara is up there with the best.

I really wish there was gimp with CMYK support. Then we'd have it all :)

Cheers,
David K

---

### Post by carla on 2006-11-06
Thank you for starting this list!

Does anyone know of any knitting-related programs for Linux--design, organization, etc.?

---

### Post by HanZo on 2006-11-06
I did get Ktoon to work once on edgy, with the icons, it'a all a matter of specifying the right install dir when the app starts for the first time. unfortunately I can't remember the exact location... but it's somethin in /usr i think...

---

### Post by ADroop on 2006-11-06
Great list.. 
have to try out that blender.

---

### Post by viper on 2006-11-07
GR8 job on the list very useful.........thx

---

### Post by carla on 2006-11-07
> **carla said:**
> Thank you for starting this list!

Does anyone know of any knitting-related programs for Linux--design, organization, etc.?

Should have noted that I only know of one: [Knitting Pattern Generator]("http://linux.softpedia.com/get/Multimedia/Graphics/Knitting-Pattern-Generator-7558.shtml") (found at Softpedia). Am going to test it on my system, shall report back. :)

---

### Post by roderikk on 2006-11-10
Very good list! I really like the LightZone software to do a quick touch up for my photos.

Maybe you could also put in a section for 'photo managing' such as f-spot and picassa?

And shouldn't imagemagic also be somewhere?

BTW maybe it is better if you promote the use of aptitude vs. apt-get ( [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) ). Especially for people who just quickly want to try things out aptitude is really good because it allows for very easy removal.

---

### Post by uuwatti on 2006-11-13
> **roderikk said:**
> Very good list! I really like the LightZone software to do a quick touch up for my photos.

Maybe you could also put in a section for 'photo managing' such as f-spot and picassa?

And shouldn't imagemagic also be somewhere?

BTW maybe it is better if you promote the use of aptitude vs. apt-get ( [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) ). Especially for people who just quickly want to try things out aptitude is really good because it allows for very easy removal.


Done and done. Except for Imagemagick, if I start listing every possible image program based on Imagemagick, this is list is going to be endless.
Stick with The Gimp... for now.

---

### Post by roderikk on 2006-11-13
Great! Here are also some tutorials for lightzone from its creator:

[http://web.mac.com/fabio.riccardi/iWeb/Site/Blog/Blog.html](http://web.mac.com/fabio.riccardi/iWeb/Site/Blog/Blog.html)

Not sure if you also want to mention those ;-), for than you would have to mention tutorials for more programs...

---

### Post by P_Badger on 2006-11-14
Awesome list, thanks muchly, eh. I'll be kept busy for a bit going through this.

Just want to add that Mainactor isn't THAT expensive, compared to other digital editing software, 200 U.S. isn't too bad. And last I checked, Shake is going for 3000 bux U.S. for the linux version, but 500 bux for the osx version, (Sweethearts, I know).

Hope Glasgow comes out some time withing the next decade. If you go to the cinepaint site, theere's a post on the front page about it being released "October 1st, 2006", but that date has come and gone. Much like Gimp, they have an annoying tendency to keep promising a "major" release then pushing it off for another 5 years.

EDIT: Oh sh*t, just checked, and you're right, OP, Shake is 5000 bux. : ( I could have sworn I saw 3000 when I was there a few weeks ago.

---

### Post by P_Badger on 2006-11-14
Me again, figured I'd add something to the thread.

After spending a bit of time looking through google, I've found a program that made me drop a turd in happiness, as it nearly makes my conversion to linux complete.

[COLOR="DarkOrange"][SIZE="4"]GOGH[/SIZE][/COLOR]

A *raster*-based "sketch" program. If you're familiar with Alias' Sketchbook Pro, and liked it, I recommend giving Gogh a go. Very friendly, dead simple, and immediately worked with my wacom tablet. 

[Gogh Project]("http://www.goghproject.com/index.html")

---

### Post by uuwatti on 2006-11-14
Good find P! I'll add it later to the main list as well.

---

### Post by Gargamella on 2006-11-15
thank u for the list, i used to search on the web for these informations

---

### Post by uuwatti on 2006-11-15
If there are any KDE folks out there reading this, there is a video editing app called kdenlive... actually if some KDE user(s) would give their opinions on KDE specific stuff on this list, I would greatly appreciate it.
Oh yeah.. back to [COLOR="Red"][SIZE="3"]kdenlive[/SIZE][/COLOR].. [@Sourceforge]("http://kdenlive.sourceforge.net/index.php")
easy install [@klik]("http://kdenlive.klik.atekon.de/")
kdenlive uses the same MLT framework as ShotCut and Jahshaka.. but this looks way better... [SIZE="1"]at least from the screenshots[/SIZE]..

---

### Post by stengah on 2006-11-16
Great idea and great list, thanks a bunch! Just been told today that F4L (Flash for Linux) has been discontinued, and adopted by the [UIRA]("http://www.uira.org/") project though. Might want to update that.

---

### Post by uuwatti on 2006-11-16
ah.. i completely forgot about uira. will update later and also check the status of the project as well. there also something called agar, which is a massive project, with all sorts of tools. I haven't added it because it seems to be discontinued as well.

---

### Post by uuwatti on 2006-11-16
EDIT: added a whole bunch of stuff.

---

### Post by roderikk on 2006-11-17
A change list would be useful :-)

Keep up the good work!

---

### Post by smartalecks on 2006-11-18
Somebody needs to sticky this.

Clarification about Diva (video editor)-

I emailed the developer not too long ago. Development is stalled at the moment because he has taken up a new job and relocated to Finland recently. Gstreamer has also been going very slowly, and Diva uses Gstreamer heavily. The developer has no intention of letting Diva die, he's just very busy at the moment. Email him some encouragement, maybe :)

---

### Post by bhuot on 2006-11-18
> **carla said:**
> Thank you for starting this list!

Does anyone know of any knitting-related programs for Linux--design, organization, etc.?

If you count cross-stitch, this is one [http://kxstitch.sourceforge.net/](http://kxstitch.sourceforge.net/)

---

### Post by bhuot on 2006-11-18
Bluefish - html editing much easier to use than Quanta Plus
cssed - cascading stylesheet editor
kbarcode label editor - all sorts of layout templates including postcards and greeting cards
[http://en.wikipedia.org/wiki/Djvu](http://en.wikipedia.org/wiki/Djvu) open format similar PDF but can give much better compression to bitmaps
I converted a 16 MB PDF to a 2 MB DJVU format file and it download incrementally as you view it so it downloads fast even over slow connections
[http://any2djvu.djvuzone.org/](http://any2djvu.djvuzone.org/) converts file to the open DJVU format
[http://javadjvu.foxtrottechnologies.com/](http://javadjvu.foxtrottechnologies.com/) java viewer for embedding into web page to view djvu files without viewer
evince (comes with Gnome) can view pdfs and djvu, etc
kghostview (usually comes with KDE) best open source pdf viewer for KDE

---

### Post by stalefries on 2006-11-18
Just pointing out that when the new version of Gimp based on GEGL comes out, it should have CMYK support. (And yes, GEGL is coming along.)

---

### Post by uuwatti on 2006-11-19
EDIT: added all.

---

### Post by savohead on 2006-11-20
GREAT LIST, i saw it once but i wasn't with my ubuntu, now i'm going to try all stuff and chose one.
That's quite the idea i had [here]("http://www.ubuntuforums.org/showthread.php?t=299376"), but with all type of softwares.
anyway, didn't want to show off, just to thank you!!
bye

---

### Post by Oki on 2006-11-20
Hi

I am very new to Linux; and the first thing I looked for was programs to view/convert/edit/++ (RAW)photos - since that is my hobby, and I needed replacement for my Windows programs(those damn camera m. only makes applications for Windows:-( ). My list is long - I saved them in a OOo writer  page, if you want me to I could post or mail my list?

Btw; why should KDE people test programs for us GNOME users - We can also use KDE applications in GNOME?

---

### Post by uuwatti on 2006-11-20
> **Oki said:**
> Hi

I am very new to Linux; and the first thing I looked for was programs to view/convert/edit/++ (RAW)photos - since that is my hobby, and I needed replacement for my Windows programs(those damn camera m. only makes applications for Windows:-( ). My list is long - I saved them in a OOo writer  page, if you want me to I could post or mail my list?

Btw; why should KDE people test programs for us GNOME users - We can also use KDE applications in GNOME?
Thanks, man !First I'm still in the middle of putting this list together, so I haven't added(or removed all the stuff i want, but here's  one I know of[UFRaw]("http://ufraw.sourceforge.net/") Just post the list here and I'll sort it out or something,
You'll probably find some kind of instructions on how to use it by searching these forums or gimptalk.com or something.
And yeah by all means if you have all the necessary stuff to run KDE apps on gnome, you can do so. I just like my installation to be lean and fast.

---

### Post by Oki on 2006-11-20
Hi again

I guess my poor English messed up the meaning of my post here; I was trying to say that I already know about a lot of software for Linux regarding digital photo(UFRaw is one of them) – since I have searched a lot of threads in photo forums and by using Google. If you want me to, I can send a PM with the list I have so you can add them to yours when you have time.

I think your list is great and needed; even in new threads in photo forums they are saying that there are so few programs for Linux when it comes to photo, witch I disagree with. And its better that you add them and not me with my English:-)

---

### Post by uuwatti on 2006-11-20
> **Oki said:**
> Hi again

I guess my poor English messed up the meaning of my post here; I was trying to say that I already know about a lot of software for Linux regarding digital photo(UFRaw is one of them) – since I have searched a lot of threads in photo forums and by using Google. 
Nothing wrong with your english, the fault is in _my_ brain.. sorry about that. Just post the list here or as an attachment and I'll put it in the main post.

---

### Post by Oki on 2006-11-21
Here is the list of the programs that I have found. 

It would be great if you could, when you got the time, update your list. Not seldom you can read post that says “there are so few programs for photo in Linux” in photo forums(as in [www.dpreview.com)](www.dpreview.com)). If you updated your list I could just post a link to it when I see people complaining about lack of programs under Linux :-)



Edit; the file is to big? What to do?

---

### Post by uuwatti on 2006-11-21
[rapidshare]("http://rapidshare.de/") it! Hopefully it's smaller than 100MB

---

### Post by Oki on 2006-11-21
Perhaps this is ok(?), if not let me know so I can delete it: 

[PHP]First note; my language is not English, and I also have dyslexia... And the comments are just what I think – don’t listen to me.
Some of the comments are just copy/paste from other sites. 

As I said, I have been looking for programs that could replace my Windows programs regarding photo. My needs were;1.View RAW files (fast), 2.Convert RAW files, 3.Edit photo, 4. Tag and view jpg, 5. ++ That was critical for me since it’s my hobby. It started bad; no camera manufactures makes programs for Linux, only MS(and perhaps Mac). Most of the “over views” was outdated – so I got a bad first impression. 

This is what I have found; 

Gimp:
http://www.gimp.org/
Gimp help file can be found in Synaptic.
Plug-in for Gimp: http://sourceforge.net/projects/lasmz
Tutorials and books about GIMP: 
http://gimp.org/tutorials/
http://gug.sunsite.dk/
http://world.std.com/~mmcirvin/gimp_tutorial/
http://www.gimpguru.org/
http://www.gimptalk.com/forum/board.php
http://gimp-savvy.com/BOOK/
http://www.gimpshop.net/
Makes Gimp look like PS: http://www.gimpshop.net/
Plug-in for Gimp so it can handle RAW files: http://ufraw.sourceforge.net/
Gimp 2.2. include RawPhoto for opening many (most?) RAW formats.

GIMP is great software, but is often compared to PS – witch I think is a bit unfair. People often complain that Gimp can’t work in 16 bits, don’t have actions, don’t support colour management and   are not user friendly. I have red that this will be fixed in later updates (http://en.wikipedia.org/wiki/GEGL). 

Krita:
http://www.koffice.org/krita/
It dos not have all the options as Gimp, but this software looks good! Krita can now work in 16 bits mode (sometimes 32 bit images), support for layers, user friendly interface, manipulate curves in lab colorspace, support for colour management (ICC Profiles) via LittleCMS. After upgrading from 8 to 16bits mode people are telling that they are getting a much better result with it. 

Digikam:
Can import pictures from your camera. Good for browsing and tagging pictures, and can convert RAW files (with Meta data) -but slow when it comes to view RAW files. Can now edit in 16 bits, and the same for all the plug-ins. Colour management is now also supported.
Help file can be downloaded from Synaptic (comes with KDE). 
Plug-ins for Digikam: http://extragear.kde.org/apps/digikamimageplugins/

Cinepaint: (The CinePaint Project)
http://www.cinepaint.org
CinePaint supports layers, offers colour management, and the application is fully colorspace aware. 16-bit support and decent sharpening filters. The ICC profiles for Linux from Adobe come in an rpm package. To install it I had to first install KPackage from synaptic and then install the rpm with Kpackage.

dcraw:
http://www.cybercom.net/~dcoffin/dcraw/
A RAW converter tool from Dave Coffin (if you want to read an amazing story you should Google his name). You can read an interview with Dave here; http://www.dpreview.com/news/0504/05042701davecoffininterview.asp  As I understand it every RAW converter for Linux is based upon dcraw (perhaps not the commercial once).
This one can’t read camera curves, and makes the pictures look “washed out", the tool Little CMS can fix that; http://www.littlecms.com/, It also removes the EXIF data (you can use a tool called neftags2jpg to replace them again; http://www.exiv2.org/ ). 
http://www.aim-dtp.net/aim/digicam/dcraw/vng-ahd-comparison.htm
http://www.cybercom.net/~dcoffin/dcraw/

Commander scripted GUI that executes both DCRAW and ImageMagick's convert utility to generate both a full sized JPEG and a web-sized JPEG.
http://www.kde-look.org/content/show.php?content=45530

Ufraw: 
http://sourceforge.net/projects/ufraw
A standalone RAW converter tool based upon dcraw, or it can be used as a plug-in for Gimp. This can edit and convert the pictures to 16 bit.  Ufraw can save the EXIF data to JPEG output for a few supported formats. You can interpolate the pictures, can read camera curves and colour, live mode when editing. Very nice! I think it is consensus that Ufraw has taken over as a standalone tool regarding dcraw. 
Guide: http://serge.mankovski.com/photoblog/?page_id=3
Guide: http://ufraw.sourceforge.net/Guide.html
You can also download and add curves to your pictures, witch can be found here: 
http://fotogenetic.dearingfilm.com/downloads.html

Rawstudio: 
http://rawstudio.org/
A RAW converter tool. As all Linux RAW converts it is based upon dcraw. Works in 16 bits, 
http://packages.ubuntu.com/edgy/graphics/rawstudio
Deb package here; http://www.getdeb.net/category.php?id=15 

ImageMagick:
http://sourceforge.net/projects/imagemagick/
http://www.imagemagick.org/script/index.php
Command based tool. Working with 16-bit linear images, including the ability to assign ICC profiles suited to the colour model of choice, and output to widely readable formats like 16-bit TIFF.

F-Spot: 
http://f-spot.org/Main_Page
For GNOME. Can import pictures, tag pictures, sort the pictures based upon the EXIF dates, can upload to Flicker and Picasa, supports RAW files, can show all pictures on a timeline, has a fun future that it will add a new screensaver for you where your “keepers” will be shown. The tags are saved in the picture file (metadata) in the last version of the program. 
It will, much as Picasa, scan a whole part ion for pictures (I don’t like that...). It has some editing tools. 

RawView -through-the-lens:
http://www.through-the-lens.net/cms/

Xara LX:
http://www.xaraxtreme.org/  

Bibble/Pro:
www.bibblelabs.com 
Cost, but is very good! I have not tried this one myself(the Linux version that is), but people are saying it is fast with handling RAW files, have a lot of good tools, and basic Noise Ninja is included(the pro version can be used if you have it). http://ubuntuforums.org/showthread.php?t=219756&highlight=raw

Lightzone:
Commercial, but free for Linux. I have read that one of the workers with LightZone is doing the porting work on his own, cus he is a Linux fan (!). I have tried this one a lot, and it is a very good program. Some of the tools (but not all) are very good imo. 
http://www.lightcrafts.com/index.php http://sonic.net/~rat/lightcrafts/index.html 
Tutorial: http://web.mac.com/fabio.riccardi/iWeb/Site/Blog/Blog.html
Test: http://www.outbackphoto.com/artofraw/raw_26/essay.html
Blog: http://fricc.blogspot.com/
Manual: http://www.lightcrafts.com/products/lightzone2/Discovering_LightZone_eBook_v9.pdf

Pixel:
http://www.kanzelsberger.com/pixel/?page_id=12
Cost. Pixel supports CMYK witch Gimp don’t. I have read that the work with this software is going slow, but I don’t know if that is a fact. 

Picasa:
http://picasa.google.com/linux/ 
Looks very good, supports and can convert RAW files (based upon dcraw), fast for showing pictures – also RAW files. Can tag files, but only in a database(I think). Have some editing tools. So, if you like Goggle...

Software to make panorama pictures:
Panorama Tools: http://www.path.unimelb.edu.au/~dersch/
Panoramaprogram/gui for Panoramatools: http://hugin.sourceforge.net/
Plugins: http://enblend.sourceforge.net/

Making panorama with gimp:
http://www.linuxjournal.com/comment/reply/7295
http://linuxappfinder.com/package/pandora
Autostitch: http://www.cs.ubc.ca/~mbrown/autostitch/autostitch.html

Programs to view pictures: 
General overview; 
http://en.wikipedia.org/wiki/Comparison_of_image_viewers
http://www.linux.com/article.pl?sid=05/10/27/166215

KphotoAlbum(was called KimDaBa):
http://kphotoalbum.org/ 
Dos not support RAW files, I don’t like the user interface. Some are saying this one is very good to organize your pictures... You can share your tags with others. 

Gthumb;
http://gthumb.sourceforge.net/
Nice interface, has some editing tools, can sort pictures. You can get it from Synaptic. Dos not support RAW files. 

Eye of Gnome(eog)/Image viewer:
Ubuntu/GNOME default image viewer. Dos not support RAW files.  

Gwenview:
http://gwenview.sourceforge.net/home?from=50
http://gwenview.sourceforge.net/
Simple but fast. Dos not support RAW files. 

ShowImg; 
http://www.jalix.org/projects/showimg/
Nice interface, can not read RAW files, a bit slow. 

Gqview: 
http://gqview.sourceforge.net/
Can not show RAW files in full size. Nice interface, fast when it comes to jpg. Can read Exif data. 

Pornview:
http://pornview.klik.atekon.de/
“Let’s make the most stupid name so no one can use it...”

FEH:
http://www.linuxbrit.co.uk/feh/ 
http://freshmeat.net/projects/feh/
http://www.linux.com/article.pl?sid=06/07/14/184218
Command based?

Goby: 
Missing info. 

GNOME Photo Collector:
http://www.linux.org/apps/AppId_7224.html

Cumulus:
http://www.canto.com/
http://www.imaging-resource.com/SOFT/CM/CM.HTM
	
Albumshaper.:
In Synaptic. 

RawView
http://www.through-the-lens.net/cms/

The Photomaniac Media Library
http://sourceforge.net/projects/pm-medialibrary/

Photo Organizer
http://freshmeat.net/projects/photoorganizer/ 

Photo Directory 
http://freshmeat.net/projects/photodirectory/

KuickShow:
http://kuickshow.sourceforge.net/
 
Ksquirrel:
http://ksquirrel.sourceforge.net/

Xnview;
http://perso.orange.fr/pierre.g/xnview/enxnview.html

FastStone Image Viewer:
This on is for Windows – a good free program known to be fast and with lots of futures, but people manage to run it also under Linux(I guess with Wine). 
“You just need to make sure you install MS Truetype Fonts for max readability (since some fonts used in Windows applications don't translate correctly otherwise). That's simple, too (you can copy fonts from windows/fonts your Windows NTFS partition, or you can use the built in package manager to install them from popular repositories with a mouse click”. 


About tags:
http://idea.zanestate.edu/archives/2005/11/photo-organizing-in-linux/
Many programs lat you tag your pictures, and save the info to a database. You should avoid those; cus if you later send the pictures to a friend or you change the program all the info is lost. It is much better to save the info (tags) inside the picture itself. The pictures has 3 “blocks” with extra info, EXIF where the camera stores info, the two others, IPTC and XMP, is where you can save “keywords”(XMP is the new version). 

Programs for Linux that stores the tags inside the IPTC:

F-Spot is using XMP. 

jBrout:
http://jbrout.python-hosting.com/
I have tried this one, and I find it to be very good. The search function is very good, and I have opened the pictures later in Windows to check if it really saves the info as IPTC keywords – witch it did. 

imgSeek:
http://www.imgseek.net/
 
Mapivi:
http://mapivi.sourceforge.net/mapivi.shtml

Perhaps Picasa2 and digikam. 

Monitor calibration:
Not supported with Linux yet (damn!!). If you are dual booting you can create a profile in Windows and later load the same profile in Linux. 
More info:
http://applications.linux.com/article.pl?sid=05/02/07/2244242
http://en.wikipedia.org/wiki/Linux_color_management
http://software.newsforge.com/article.pl?sid=05/03/08/1712218
http://docs.scribus.net/index.php?lang=en&page=cms
http://lists.xcf.berkeley.edu/lists/gimp-user/2006-September/008614.html
http://sourceforge.net/project/screenshots.php?group_id=146038
http://www.linuxjournal.com/article/6635
http://www.photo.net/bboard/q-and-a-fetch-msg?msg_id=00HMf8&tag=200607240407
http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/

You can also use Linux to make your own ICC profiles: http://www.argyllcms.com/doc/ArgyllDoc.html

Little CMS:
http://www.littlecms.com/
“ is a "free colour management engine in 100K. This is handy if you have programs, like dcraw or ImageMagick, which don't support colour profiles.”

Monica:
http://www.pcbypaul.com/software/monica.html
Monica is a free monitor calibration tool.

xicc:
http://packages.debian.org/unstable/x11/xicc

Colour profiles (.icc) from Adobe are available here: http://www.adobe.com/support/downloads/iccprofiles/iccprofiles_linux.html

Other programs:
Transfer pictures from camera to pc:
http://gphoto.sourceforge.net

gphoto2:
http://www.gphoto.org/
Support for different cameras (digikam are using this). 

ExifTool:
http://owl.phy.queensu.ca/~phil/exiftool/
To read Exif data.

Another Exif reader:
http://www.cheeseplant.org/~daniel/pages/metacam.html

jUploadr 1.1.1:
For uploading to flickr and Zoommr
http://www.flickr.com/explore/. 

Coriander:
http://damien.douxchamps.net/ieee1394/coriander/index.php
To control the camera from a pc.

To use a folder with pictures as a screensaver in Ubunut – Howto:
http://ubuntuforums.org/showthread.php?t=230576

Gallery:
http://gallery.menalto.com/
The open source web based photo album organizer. Gallery gives you an intuitive way to blend photo management seamlessly into your own website

HDR capable software in Linux:
http://graphics.stanford.edu/~mhouston/school/digital-photo/

Linux Movie:
1.http://www.linuxmovies.org/software.html 
http://ubuntuforums.org/showthread.php?t=293798



[/PHP]

---

### Post by uuwatti on 2006-11-21
Excellent list, man! Just leave as it is.

---

### Post by uuwatti on 2006-11-21
> *Originally posted by Oki I just fixed the URLs Thanks to Oki for his most excellent post* -uuwatti

First note; my language is not English, and I also have dyslexia... And the comments are just what I think &#8211; don&#8217;t listen to me.
Some of the comments are just copy/paste from other sites. 

As I said, I have been looking for programs that could replace my Windows programs regarding photo. My needs were;1.View RAW files (fast), 2.Convert RAW files, 3.Edit photo, 4. Tag and view jpg, 5. ++ That was critical for me since it&#8217;s my hobby. It started bad; no camera manufactures makes programs for Linux, only MS(and perhaps Mac). Most of the &#8220;over views&#8221; was outdated &#8211; so I got a bad first impression. 

This is what I have found; 

[SIZE="3"][COLOR="Red"]Gimp:[/COLOR][/SIZE]
[http://www.gimp.org/]("http://www.gimp.org/")
Gimp help file can be found in Synaptic.
[SIZE="3"][COLOR="Red"]Plug-in for Gimp: [/COLOR][/SIZE][http://sourceforge.net/projects/lasmz]("http://sourceforge.net/projects/lasmz")
Tutorials and books about GIMP: 
[http://gimp.org/tutorials/]("http://gimp.org/tutorials/")
[http://gug.sunsite.dk/]("http://gug.sunsite.dk/")
[http://world.std.com/~mmcirvin/gimp_tutorial/]("http://world.std.com/~mmcirvin/gimp_tutorial/")
[http://www.gimpguru.org/]("http://www.gimpguru.org/")
[http://www.gimptalk.com/forum/board.php]("http://www.gimptalk.com/forum/board.php")
[http://gimp-savvy.com/BOOK/]("http://gimp-savvy.com/BOOK/")
[http://www.gimpshop.net/]("http://www.gimpshop.net/")
Makes Gimp look like PS: [http://www.gimpshop.net/]("http://www.gimpshop.net/")
Plug-in for Gimp so it can handle RAW files: [http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/)
Gimp 2.2. include RawPhoto for opening many (most?) RAW formats.

GIMP is great software, but is often compared to PS &#8211; witch I think is a bit unfair. People often complain that Gimp can&#8217;t work in 16 bits, don&#8217;t have actions, don&#8217;t support colour management and   are not user friendly. I have red that this will be fixed in later updates ([http://en.wikipedia.org/wiki/GEGL]("http://en.wikipedia.org/wiki/GEGL")). 

[SIZE="3"][COLOR="Red"]Krita:[/COLOR][/SIZE]
[http://www.koffice.org/krita/]("http://www.koffice.org/krita/")
It dos not have all the options as Gimp, but this software looks good! Krita can now work in 16 bits mode (sometimes 32 bit images), support for layers, user friendly interface, manipulate curves in lab colorspace, support for colour management (ICC Profiles) via LittleCMS. After upgrading from 8 to 16bits mode people are telling that they are getting a much better result with it. 

[SIZE="3"][COLOR="Red"]Digikam:[/COLOR][/SIZE]
Can import pictures from your camera. Good for browsing and tagging pictures, and can convert RAW files (with Meta data) -but slow when it comes to view RAW files. Can now edit in 16 bits, and the same for all the plug-ins. Colour management is now also supported.
Help file can be downloaded from Synaptic (comes with KDE). 
[SIZE="3"][COLOR="Red"]Plug-ins for Digikam: [/COLOR][/SIZE][http://extragear.kde.org/apps/digikamimageplugins/]("http://extragear.kde.org/apps/digikamimageplugins/")

[SIZE="3"][COLOR="Red"]Cinepaint:[/COLOR][/SIZE] (The CinePaint Project)
[http://www.cinepaint.org]("http://www.cinepaint.org")
CinePaint supports layers, offers colour management, and the application is fully colorspace aware. 16-bit support and decent sharpening filters. The ICC profiles for Linux from Adobe come in an rpm package. To install it I had to first install KPackage from synaptic and then install the rpm with Kpackage.

[SIZE="3"][COLOR="Red"]dcraw:[/COLOR][/SIZE]
[http://www.cybercom.net/~dcoffin/dcraw/]("http://www.cybercom.net/~dcoffin/dcraw/")
A RAW converter tool from Dave Coffin (if you want to read an amazing story you should Google his name). You can read an interview with Dave here; [http://www.dpreview.com/news/0504/05042701davecoffininterview.asp]("http://www.dpreview.com/news/0504/05042701davecoffininterview.asp") As I understand it every RAW converter for Linux is based upon dcraw (perhaps not the commercial once).
This one can&#8217;t read camera curves, and makes the pictures look &#8220;washed out", the tool Little CMS can fix that; [http://www.littlecms.com/]("http://www.littlecms.com/"), It also removes the EXIF data (you can use a tool called neftags2jpg to replace them again; [http://www.exiv2.org/]("http://www.exiv2.org/") ). 
[http://www.aim-dtp.net/aim/digicam/dcraw/vng-ahd-comparison.htm]("http://www.aim-dtp.net/aim/digicam/dcraw/vng-ahd-comparison.htm")
[http://www.cybercom.net/~dcoffin/dcraw/]("http://www.cybercom.net/~dcoffin/dcraw/")

Commander scripted GUI that executes both DCRAW and ImageMagick's convert utility to generate both a full sized JPEG and a web-sized JPEG.
[http://www.kde-look.org/content/show.php?content=45530]("http://www.kde-look.org/content/show.php?content=45530")

[SIZE="3"][COLOR="Red"]Ufraw: [/COLOR][/SIZE]
[http://sourceforge.net/projects/ufraw]("http://sourceforge.net/projects/ufraw")
A standalone RAW converter tool based upon dcraw, or it can be used as a plug-in for Gimp. This can edit and convert the pictures to 16 bit.  Ufraw can save the EXIF data to JPEG output for a few supported formats. You can interpolate the pictures, can read camera curves and colour, live mode when editing. Very nice! I think it is consensus that Ufraw has taken over as a standalone tool regarding dcraw. 
Guide: [http://serge.mankovski.com/photoblog/?page_id=3]("http://serge.mankovski.com/photoblog/?page_id=3")
Guide: [http://ufraw.sourceforge.net/Guide.html]("http://ufraw.sourceforge.net/Guide.html")
You can also download and add curves to your pictures, witch can be found here: 
[http://fotogenetic.dearingfilm.com/downloads.html]("http://fotogenetic.dearingfilm.com/downloads.html")

[SIZE="3"][COLOR="Red"]Rawstudio: [/COLOR][/SIZE]
[http://rawstudio.org/]("http://rawstudio.org/")
A RAW converter tool. As all Linux RAW converts it is based upon dcraw. Works in 16 bits, 
[http://packages.ubuntu.com/edgy/graphics/rawstudio]("http://packages.ubuntu.com/edgy/graphics/rawstudio")
Deb package here; [http://www.getdeb.net/category.php?id=15]("http://www.getdeb.net/category.php?id=15") 
[COLOR="Red"][SIZE="3"]
ImageMagick:[/SIZE][/COLOR]
[http://sourceforge.net/projects/imagemagick/]("http://sourceforge.net/projects/imagemagick/")
[http://www.imagemagick.org/script/index.php]("http://www.imagemagick.org/script/index.php")
Command based tool. Working with 16-bit linear images, including the ability to assign ICC profiles suited to the colour model of choice, and output to widely readable formats like 16-bit TIFF.
[COLOR="Red"][SIZE="3"]
F-Spot: [/SIZE][/COLOR]
[http://f-spot.org/Main_Page]("http://f-spot.org/Main_Page")
For GNOME. Can import pictures, tag pictures, sort the pictures based upon the EXIF dates, can upload to Flicker and Picasa, supports RAW files, can show all pictures on a timeline, has a fun future that it will add a new screensaver for you where your &#8220;keepers&#8221; will be shown. The tags are saved in the picture file (metadata) in the last version of the program. 
It will, much as Picasa, scan a whole part ion for pictures (I don&#8217;t like that...). It has some editing tools. 
[COLOR="Red"][SIZE="3"]
RawView -through-the-lens[/SIZE][/COLOR]:
[http://www.through-the-lens.net/cms/]("http://www.through-the-lens.net/cms/")

[COLOR="Red"][SIZE="3"]Xara LX:[/SIZE][/COLOR]
[http://www.xaraxtreme.org/ ]("http://www.xaraxtreme.org/") 

[SIZE="3"][COLOR="Red"]Bibble/Pro:[/COLOR][/SIZE]
[www.bibblelabs.com]("http://www.bibblelabs.com") 
Cost, but is very good! I have not tried this one myself(the Linux version that is), but people are saying it is fast with handling RAW files, have a lot of good tools, and basic Noise Ninja is included(the pro version can be used if you have it). [http://ubuntuforums.org/showthread.php?t=219756&highlight=raw]("http://ubuntuforums.org/showthread.php?t=219756&highlight=raw")

[SIZE="3"][COLOR="Red"]Lightzone:[/COLOR][/SIZE]
Commercial, but free for Linux. I have read that one of the workers with LightZone is doing the porting work on his own, cus he is a Linux fan (!). I have tried this one a lot, and it is a very good program. Some of the tools (but not all) are very good imo. 
[http://www.lightcrafts.com/index.php ]("http://www.lightcrafts.com/index.php")[http://sonic.net/~rat/lightcrafts/index.html ]("http://sonic.net/~rat/lightcrafts/index.html")
Tutorial: [http://web.mac.com/fabio.riccardi/iWeb/Site/Blog/Blog.html]("http://web.mac.com/fabio.riccardi/iWeb/Site/Blog/Blog.html")
Test: [http://www.outbackphoto.com/artofraw/raw_26/essay.html]("http://www.outbackphoto.com/artofraw/raw_26/essay.html")
Blog: [http://fricc.blogspot.com/]("http://fricc.blogspot.com/")
Manual: [http://www.lightcrafts.com/products/lightzone2/Discovering_LightZone_eBook_v9.pdf]("http://www.lightcrafts.com/products/lightzone2/Discovering_LightZone_eBook_v9.pdf")

[SIZE="3"][COLOR="Red"]Pixel:[/COLOR][/SIZE]
[http://www.kanzelsberger.com/pixel/?page_id=12]("http://www.kanzelsberger.com/pixel/?page_id=12")
Cost. Pixel supports CMYK witch Gimp don&#8217;t. I have read that the work with this software is going slow, but I don&#8217;t know if that is a fact. 

[SIZE="3"][COLOR="Red"]Picasa:[/COLOR][/SIZE]
[http://picasa.google.com/linux/ ]("http://picasa.google.com/linux/")
Looks very good, supports and can convert RAW files (based upon dcraw), fast for showing pictures &#8211; also RAW files. Can tag files, but only in a database(I think). Have some editing tools. So, if you like Goggle...

Software to make panorama pictures:
[SIZE="3"][COLOR="Red"]Panorama Tools:[/COLOR][/SIZE] [http://www.path.unimelb.edu.au/~dersch/]("http://www.path.unimelb.edu.au/~dersch/")
Panoramaprogram/gui for Panoramatools: [http://hugin.sourceforge.net/]("http://hugin.sourceforge.net/")
Plugins: [http://enblend.sourceforge.net/]("http://enblend.sourceforge.net/")

[SIZE="3"][COLOR="Red"]Making panorama with gimp:[/COLOR][/SIZE]
[http://www.linuxjournal.com/comment/reply/7295]("http://www.linuxjournal.com/comment/reply/7295")
[http://linuxappfinder.com/package/pandora]("http://linuxappfinder.com/package/pandora")
Autostitch: [http://www.cs.ubc.ca/~mbrown/autostitch/autostitch.html]("http://www.cs.ubc.ca/~mbrown/autostitch/autostitch.html")

Programs to view pictures: 
General overview; 
[http://en.wikipedia.org/wiki/Comparison_of_image_viewers]("http://en.wikipedia.org/wiki/Comparison_of_image_viewers")
[http://www.linux.com/article.pl?sid=05/10/27/166215]("http://www.linux.com/article.pl?sid=05/10/27/166215")

[COLOR="Red"][SIZE="3"]KphotoAlbum[/SIZE][/COLOR](was called KimDaBa):
[http://kphotoalbum.org/ ]("http://kphotoalbum.org/")
Dos not support RAW files, I don&#8217;t like the user interface. Some are saying this one is very good to organize your pictures... You can share your tags with others. 

[SIZE="3"][COLOR="Red"]Gthumb;[/COLOR][/SIZE]
[http://gthumb.sourceforge.net/]("http://gthumb.sourceforge.net/")
Nice interface, has some editing tools, can sort pictures. You can get it from Synaptic. Dos not support RAW files. 
[SIZE="3"][COLOR="Red"]
Eye of Gnome[/COLOR][/SIZE](eog)/Image viewer:
Ubuntu/GNOME default image viewer. Dos not support RAW files.  

[SIZE="3"][COLOR="Red"]Gwenview:[/COLOR][/SIZE]
[http://gwenview.sourceforge.net/home?from=50]("http://gwenview.sourceforge.net/home?from=50")
[http://gwenview.sourceforge.net/]("http://gwenview.sourceforge.net/")
Simple but fast. Dos not support RAW files. 

[SIZE="3"][COLOR="Red"]ShowImg;[/COLOR][/SIZE] 
[http://www.jalix.org/projects/showimg/]("http://www.jalix.org/projects/showimg/")
Nice interface, can not read RAW files, a bit slow. 

[SIZE="3"][COLOR="Red"]Gqview: [/COLOR][/SIZE]
[http://gqview.sourceforge.net/]("http://gqview.sourceforge.net/")
Can not show RAW files in full size. Nice interface, fast when it comes to jpg. Can read Exif data. 

[SIZE="3"][COLOR="Red"]Pornview:[/COLOR][/SIZE]
[http://pornview.klik.atekon.de/]("http://pornview.klik.atekon.de/")
&#8220;Let&#8217;s make the most stupid name so no one can use it...&#8221;
[SIZE="3"][COLOR="Red"]
FEH:[/COLOR][/SIZE]
[http://www.linuxbrit.co.uk/feh/ ]("http://www.linuxbrit.co.uk/feh/")
[http://freshmeat.net/projects/feh/]("http://freshmeat.net/projects/feh/")
[http://www.linux.com/article.pl?sid=06/07/14/184218]("http://www.linux.com/article.pl?sid=06/07/14/184218")
Command based?

[SIZE="3"][COLOR="Red"]Goby:[/COLOR][/SIZE] 
Missing info. 

[SIZE="3"][COLOR="Red"]GNOME Photo Collector:[/COLOR][/SIZE]
[http://www.linux.org/apps/AppId_7224.html]("http://www.linux.org/apps/AppId_7224.html")
[SIZE="3"][COLOR="Red"]
Cumulus:[/COLOR][/SIZE]
[http://www.canto.com/]("http://www.canto.com/")
[http://www.imaging-resource.com/SOFT/CM/CM.HTM]("http://www.imaging-resource.com/SOFT/CM/CM.HTM")
[SIZE="3"][COLOR="Red"]    
Albumshaper.:[/COLOR][/SIZE]
In Synaptic. 

[SIZE="3"][COLOR="Red"]RawView[/COLOR][/SIZE]
[http://www.through-the-lens.net/cms/]("http://www.through-the-lens.net/cms/")

[SIZE="3"][COLOR="Red"]The Photomaniac Media Library[/COLOR][/SIZE]
[http://sourceforge.net/projects/pm-medialibrary/]("http://sourceforge.net/projects/pm-medialibrary/")

[SIZE="3"][COLOR="Red"]Photo Organizer[/COLOR][/SIZE]
[http://freshmeat.net/projects/photoorganizer/ ]("http://freshmeat.net/projects/photoorganizer/")

[SIZE="3"][COLOR="Red"]Photo Directory [/COLOR][/SIZE]
[http://freshmeat.net/projects/photodirectory/]("http://freshmeat.net/projects/photodirectory/")

[SIZE="3"][COLOR="Red"]KuickShow:[/COLOR][/SIZE]
[http://kuickshow.sourceforge.net/]("http://kuickshow.sourceforge.net/")
 
[SIZE="3"][COLOR="Red"]Ksquirrel:[/COLOR][/SIZE]
[http://ksquirrel.sourceforge.net/]("http://ksquirrel.sourceforge.net/")

[SIZE="3"][COLOR="Red"]Xnview;[/COLOR][/SIZE]
[http://perso.orange.fr/pierre.g/xnview/enxnview.html]("http://perso.orange.fr/pierre.g/xnview/enxnview.html")

[SIZE="3"][COLOR="Red"]FastStone Image Viewer:[/COLOR][/SIZE]
This on is for Windows &#8211; a good free program known to be fast and with lots of futures, but people manage to run it also under Linux(I guess with Wine). 
&#8220;You just need to make sure you install MS Truetype Fonts for max readability (since some fonts used in Windows applications don't translate correctly otherwise). That's simple, too (you can copy fonts from windows/fonts your Windows NTFS partition, or you can use the built in package manager to install them from popular repositories with a mouse click&#8221;. 


[SIZE="3"][COLOR="Red"]About tags:[/COLOR][/SIZE]
[http://idea.zanestate.edu/archives/2005/11/photo-organizing-in-linux/]("http://idea.zanestate.edu/archives/2005/11/photo-organizing-in-linux/")
Many programs lat you tag your pictures, and save the info to a database. You should avoid those; cus if you later send the pictures to a friend or you change the program all the info is lost. It is much better to save the info (tags) inside the picture itself. The pictures has 3 &#8220;blocks&#8221; with extra info, EXIF where the camera stores info, the two others, IPTC and XMP, is where you can save &#8220;keywords&#8221;(XMP is the new version). 

Programs for Linux that stores the tags inside the IPTC:

F-Spot is using XMP. 

[SIZE="3"][COLOR="Red"]jBrout:[/COLOR][/SIZE]
[http://jbrout.python-hosting.com/]("http://jbrout.python-hosting.com/")
I have tried this one, and I find it to be very good. The search function is very good, and I have opened the pictures later in Windows to check if it really saves the info as IPTC keywords &#8211; witch it did. 

[SIZE="3"][COLOR="Red"]imgSeek:[/COLOR][/SIZE]
[http://www.imgseek.net/]("http://www.imgseek.net/")
 
[SIZE="3"][COLOR="Red"]Mapivi:[/COLOR][/SIZE]
[http://mapivi.sourceforge.net/mapivi.shtml]("http://mapivi.sourceforge.net/mapivi.shtml")

Perhaps Picasa2 and digikam. 

[SIZE="3"][COLOR="Red"]Monitor calibration:[/COLOR][/SIZE]
Not supported with Linux yet (damn!!). If you are dual booting you can create a profile in Windows and later load the same profile in Linux. 
More info:
[http://applications.linux.com/article.pl?sid=05/02/07/2244242]("http://applications.linux.com/article.pl?sid=05/02/07/2244242")
[http://en.wikipedia.org/wiki/Linux_color_management]("http://en.wikipedia.org/wiki/Linux_color_management")
[http://software.newsforge.com/article.pl?sid=05/03/08/1712218]("http://software.newsforge.com/article.pl?sid=05/03/08/1712218")
[http://docs.scribus.net/index.php?lang=en&page=cms]("http://docs.scribus.net/index.php?lang=en&page=cms")
[http://lists.xcf.berkeley.edu/lists/gimp-user/2006-September/008614.html]("http://lists.xcf.berkeley.edu/lists/gimp-user/2006-September/008614.html")
[http://sourceforge.net/project/screenshots.php?group_id=146038]("http://sourceforge.net/project/screenshots.php?group_id=146038")
[http://www.linuxjournal.com/article/6635]("http://www.linuxjournal.com/article/6635")
[http://www.photo.net/bboard/q-and-a-fetch-msg?msg_id=00HMf8&tag=200607240407]("http://www.photo.net/bboard/q-and-a-fetch-msg?msg_id=00HMf8&tag=200607240407")
[http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/")

You can also use Linux to make your own ICC profiles: [http://www.argyllcms.com/doc/ArgyllDoc.html]("http://www.argyllcms.com/doc/ArgyllDoc.html")

[SIZE="3"][COLOR="Red"]Little CMS:[/COLOR][/SIZE]
[http://www.littlecms.com/]("http://www.littlecms.com/")
&#8220; is a "free colour management engine in 100K. This is handy if you have programs, like dcraw or ImageMagick, which don't support colour profiles.&#8221;

[SIZE="3"][COLOR="Red"]Monica:[/COLOR][/SIZE]
[http://www.pcbypaul.com/software/monica.html]("http://www.pcbypaul.com/software/monica.html")
Monica is a free monitor calibration tool.

[SIZE="3"][COLOR="Red"]xicc:[/COLOR][/SIZE]
[http://packages.debian.org/unstable/x11/xicc]("http://packages.debian.org/unstable/x11/xicc")

[SIZE="2"][COLOR="Red"]Colour profiles (.icc) from Adobe are available here:[/COLOR][/SIZE] [URL="http://www.adobe.com/support/downloads/iccprofiles/iccprofiles_linux.html"]http://www.adobe.com/support/downloads/iccprofiles/iccprofiles_linux.html
[/URL]
Other programs:
Transfer pictures from camera to pc:
[http://gphoto.sourceforge.net]("http://gphoto.sourceforge.net")
[SIZE="3"][COLOR="Red"]
gphoto2:[/COLOR][/SIZE]
[http://www.gphoto.org/]("http://www.gphoto.org/")
Support for different cameras (digikam are using this). 
[SIZE="3"][COLOR="Red"]
ExifTool:[/COLOR][/SIZE]
[http://owl.phy.queensu.ca/~phil/exiftool/]("http://owl.phy.queensu.ca/~phil/exiftool/")
To read Exif data.

[SIZE="3"][COLOR="Red"]Another Exif reader:[/COLOR][/SIZE]
[http://www.cheeseplant.org/~daniel/pages/metacam.html]("http://www.cheeseplant.org/~daniel/pages/metacam.html")
[SIZE="3"][COLOR="Red"]
jUploadr 1.1.1:[/COLOR][/SIZE]
For uploading to flickr and Zoommr
[http://www.flickr.com/explore/]("http://www.flickr.com/explore/"). 
[SIZE="3"][COLOR="Red"]
Coriander:[/COLOR][/SIZE]
[http://damien.douxchamps.net/ieee1394/coriander/index.php]("http://damien.douxchamps.net/ieee1394/coriander/index.php")
To control the camera from a pc.

To use a folder with pictures as a screensaver in Ubunut &#8211; Howto:
[http://ubuntuforums.org/showthread.php?t=230576]("http://ubuntuforums.org/showthread.php?t=230576")
[SIZE="3"][COLOR="Red"]
Gallery:[/COLOR][/SIZE]
[http://gallery.menalto.com/]("http://gallery.menalto.com/")
The open source web based photo album organizer. Gallery gives you an intuitive way to blend photo management seamlessly into your own website

[SIZE="3"][COLOR="Red"]HDR capable software in Linux:[/COLOR][/SIZE]
[http://graphics.stanford.edu/~mhouston/school/digital-photo/]("http://graphics.stanford.edu/~mhouston/school/digital-photo/")

[SIZE="3"][COLOR="Red"]Linux Movie:[/COLOR][/SIZE]
1.[http://www.linuxmovies.org/software.html ]("http://www.linuxmovies.org/software.html")
[http://ubuntuforums.org/showthread.php?t=293798  ]("http://ubuntuforums.org/showthread.php?t=293798")

---

### Post by Oki on 2006-11-24
Nice work with the list uuwatti:-D

I think you and me have big troubles to understand each other he he 

I hope you get som time to make one list a the first page where we can have all the suggested programs listed(and not with my text or name in it pl). That would be great to have when seeing whining of lack of photo/movie programs under Linux - just give the link. 

Only thing I miss now is Google Sketchup, lets hope they can port it to Linux, not only to MS and Mac... 

Have a nice day – Oki

---

### Post by Oki on 2006-11-24
Add this?

tkpaint
[http://mars.netanya.ac.il/~samy/tkpaint.html](http://mars.netanya.ac.il/~samy/tkpaint.html)

---

### Post by uuwatti on 2006-11-25
yeah i will put all the stuff to the first post when i have more time.

---

### Post by Oki on 2006-11-26
A new program:
[http://www.rawtherapee.com/](http://www.rawtherapee.com/)

"Raw Therapee is a free RAW photo converter application developed single-handedly by Gábor Horváth. It has been available on Windows for some time, but on October 11, Horváth released the first build for Linux. If you are familiar with other graphical RAW converters, such as UFRaw, you will feel quite at home using Raw Therapee."

---

### Post by Animortis on 2006-11-27
Is there any PDF editing software getting closer to Adobe Acrobat? Exporting PDFs are something else entirely, I need to modify already-created PDFs, sign them and sometimes encrypt them.

---

### Post by leech on 2006-11-27
Don't forget for Desktop Publishing, Pagestream.

I used to use it on the Atari ST, haven't tried it on Linux yet (except the demo for a short time)

It's Proprietary / Commercial, but does support PDF, etc.

[http://www.grasshopperllc.com/](http://www.grasshopperllc.com/)

Leech

---

### Post by hikaricore on 2006-11-28
*bump* to keep the list up there

---

### Post by uuwatti on 2006-11-29
> **Animortis said:**
> Is there any PDF editing software getting closer to Adobe Acrobat? Exporting PDFs are something else entirely, I need to modify already-created PDFs, sign them and sometimes encrypt them.

Lets see...
[http://www.ecademix.com/JohannesHofmann/]("http://www.ecademix.com/JohannesHofmann/")
[http://alan.aspuru.com/archives/2005/12/26/how-to-edit-a-pdf-file-in-linux/]("http://alan.aspuru.com/archives/2005/12/26/how-to-edit-a-pdf-file-in-linux/")
[http://pdfedit.petricek.net/pdfedit.download_e]("http://pdfedit.petricek.net/pdfedit.download_e")

Middle link is unfortunately the best solution atm. ..until the program in the last link is finished. Still.. I would give it a try

---

### Post by Oki on 2006-11-30
You could take a look at this link, and look under "Creating PDF" [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by uuwatti on 2006-12-01
Found more (proprietary)stuff: 
[XSI (3D)]("http://www.softimage.com/products/xsi/default.aspx")
[Some really high-tech editing system ála Smoke (look below)/]("http://www.digitalvision.se/")
[Smoke (video editing)]("http://usa.autodesk.com/adsk/servlet/index?id=5561833&siteID=123112")
[Flint (Video Compositing]("http://usa.autodesk.com/adsk/servlet/index?id=5562744&siteID=123112")
[RealFlow (3D --fluid simulation)]("http://www.nextlimit.com/realflow/")

---

### Post by Portable_Jim on 2006-12-01
(referring to original message - I feel it is too long to quote)

Thanks , I didn't know there was Open Source Apps to do all those purposes.

---

### Post by Portable_Jim on 2006-12-01
Also, I forgot to mention...
[quote=[uuwatti]("http://ubuntuforums.org/member.php?u=140705")]
[SIZE=3][COLOR=Red]Gimp:[/COLOR][/SIZE]
[http://www.gimp.org/](http://www.gimp.org/)
Gimp help file can be found in Synaptic.[/quote]
The GIMP is VERY Good (in my view comparable to Photoshop)

[quote=[uuwatti]("http://ubuntuforums.org/member.php?u=140705")][SIZE=3][COLOR=Red] Blender[/COLOR][/SIZE] OSS
     Code:
     [LEFT]sudo aptitude install blender[/LEFT]
 
3D program with editing and compositing capabilities. Everyone should know this by now
[/quote]
Also, V. Good

P.S 
[quote=hikaricore]*bump* to keep the list up there[/quote]
What is a "bump"??

---

### Post by Rodneyck on 2006-12-01
A bump is a way to revive an old thread, to bring it to user's attention by raising its order on the forum to the top, just by posting.

---

### Post by Oki on 2006-12-01
Two more for you:

LPROF:
[http://lprof.sourceforge.net/](http://lprof.sourceforge.net/)
"open source ICC profiler with a graphical user interface"
Loks good!

LPhoto:
[http://www.lphoto.com/?page=downloads](http://www.lphoto.com/?page=downloads)
Dont think this one is so good, comapred to digikam, f-spot and so on...

---

### Post by Portable_Jim on 2006-12-02
> **Rodneyck said:**
> A bump is a way to revive an old thread, to bring it to user's attention by raising its order on the forum to the top, just by posting.

Thanks

---

### Post by rioghal on 2006-12-02
I, for one, feel that this thread needs to be made "sticky". This list is a "must-read" and I feel it would benefit all users in one way or another. How can we get this thread made sticky?

---

### Post by Oki on 2006-12-02
As soon as the first post here is updated I will post a thread over at dpreview.com; guess they will be surprised to see all the free and good photoprograms that can be used under Linux! Perhaps some will think twice; photo related applications are not cheap. And the majority thinks these programs are missing under Linux.

---

### Post by Portable_Jim on 2006-12-02
Using windows, I could only dream about owning a Vector animation, CAD, Desktop Publishing, and (good) video editing software.

I had (and still have) the GIMP, Blender and Nvu. A few months ago my Dad got to use Macromedia Flash 8 (work licence), so I got Studio MX. This list basically lets me do everything I am able to do in Window$, with Linux. Again, Thanks for the list!!!

---

### Post by Rodneyck on 2006-12-02
Well, as far as Gimp is concerned, it has a ways to go before it rivals the likes of Photoshop for professional use, CMYK support for one.  I would also like to see it handle some vector graphics, like PS can. I think someone said you can only get 600 dpi output, which is bad for some professional mock ups. 

With that said, I think many of these issues are being addressed, from what I have read, in future updates, at least I hope so.

---

### Post by uuwatti on 2006-12-03
I'm starting to feel like putting up a website with all this stuff and links to tutorials and so on. ). Also my SLR is from 1971 so my knowledge of any RAW-related stuff isn't exactly up-to-date. At least a website would be easier to update.
Anyways, I will update the first post now and see if can learn some kind of web-app to make a website..

EDIT: yeah i'm gonna do a website for all this stuff. That main post is getting pretty irritating to edit. Also the navigation is starting to suffer, as list keeps growing and growing.

EDIT2: First Edition ready. Just opied most of the content here to that page. Will add links to tutorials and information pages, and some sort of way to navigate easily 
like: I want to create a pamphlet <-- click and it goes to program and/or tutorial. 
I want something like photoshop <-- click and it goes to the gimp and krita etc.
[http://www.freewebs.com/artlinux/]("http://www.freewebs.com/artlinux/")

---

### Post by Oki on 2006-12-05
Hi again uuwatti

I think you have done a great job with that site. It was hard to scroll at first, but I can se you have fixed it. I hope you can add a link to the homepage for each project for more info, and it looks like you already have started. It&#8217;s a great site to link to for others, so they can easy and fast get an overview &#8211; big thanks for your work!

One of the bad thing with these sort of pages, are that they often are forgotten/outdated; hope you can keep an eye on it. 

Perhaps you can add a link to it in the first post in this thread?

Best regards

Oki

---

### Post by uuwatti on 2006-12-05
I'll work on the site tomorrow or the day after. The slowness (it's really slow for me as well sometimes) you are experiencing is due to the fact that it's freewebs.com and there is very little I can do about it. I'll try though.

---

### Post by uuwatti on 2006-12-06
I have to switch the host freewebs isn't good enough this kind of site. It's probably gonna take a while.

---

### Post by -Phi- on 2006-12-06
Do you need space? I can donate a subdomain with (or without) some wiki software.

- Phi

---

### Post by Deviltongue on 2006-12-08
I need some help compiling KToon, I'm new to Ubuntu so I'm still getting acquainted

---

### Post by hikaricore on 2006-12-11
someone should pin this thread :P  *hint nudge*

---

### Post by uuwatti on 2006-12-11
Sorry for the delay on the update, I'm really busy atm. @-Phi- ..thanks for the offer, but think I already found a suitable host. I'll keep your offer in mind, if it doesn't work out though.

---

### Post by MoonBlossom on 2006-12-13
Thank you for the list is very useful!!

I couldn't get knitting pattern generator to work but I found KXStitch. 

[http://kxstitch.sourceforge.net](http://kxstitch.sourceforge.net)

---

### Post by 23meg on 2006-12-13
Under Aptana you may want to link to [this guide]("http://www.ubuntuforums.org/showthread.php?t=315444") for installing it under Edgy.

---

### Post by pgatrick on 2006-12-15
Don't forget [K-3D](k-3d.org), it's an OSS 3D app which is developing quite nicely. It outputs to RIB, for which the OSS renderman renderers [Aqsis](aqsis.org) and [Pixie](pixie.sf.net) are quite nice. :)
Also there's [3Delight](3delight.com) a proprietary renderman renderer wich is free for noncommercial use, and [RenderDotC](http://www.dotcsw.com/), another proprietary renderman renderer but with a free (resolution crippled) version. :) I'll add more if I can think of them. :)

---

### Post by uuwatti on 2006-12-16
I made it into a wiki. so, please people start editing and adding to content to it as soon as I publish it (later today or tomorrow) I don't have that much time to create the content so Wiki is the best option. you can also leave comments and such. I don't have any experience with webdesign or raw photography. so people with knowledge and links are more than welcome to come and share their information.

---

### Post by Oki on 2006-12-16
Do you have a link pl?

And this is relevant [http://www.linux.com/article.pl?sid=06/12/06/158220](http://www.linux.com/article.pl?sid=06/12/06/158220)

---

### Post by uuwatti on 2006-12-17
I' still putting all the stuff from these forums in there, so there isn't much content yet, But, if you want start adding stuff here is the link. they got some problems with opera and konqueror browsers, so use firefox when editing. (you can browse the site with other browsers, just not edit) 
[http://artlinux.wetpaint.com/]("http://artlinux.wetpaint.com/")

---

### Post by circ on 2006-12-17
you didnt mention avidemux under vid tools, which imo is the only video editor worth using on unix.

---

### Post by EyeBun2 on 2006-12-17
Thank you Uuwatti for creating this exellent thread.  You have provided a very impressive list and I look forward to future additions.   Great job!

---

### Post by YaseenKriel on 2006-12-18
what software would u  recommend to get video from video camera onto pc via usb cable? Got a sony video camera and wanna burn home movies onto DVD.

---

### Post by eragorn on 2006-12-20
Uuwatti, you rock man!  For those of you who are just watching the thread make sure you check out the Wiki it kicks *** and is only going to get better.

Nicely done!

---

### Post by uuwatti on 2006-12-20
thanks for the kind words, people! sorry for not updating the wiki properly yet (no time). I'll try to do it the day after xmas (not a promise ;) ).

---

### Post by uuwatti on 2006-12-20
...meanwhile here's something to keep you guys busy. kdenlive is The Best open-source video editor so far. I copypasted (and updated) these instructions from here -->[http://doc.ubuntu-fr.org/applications/kdenlive]("http://doc.ubuntu-fr.org/applications/kdenlive") I hope I managed to get all the dependencies right.
```
sudo aptitude install kdelibs4-dev libqt4-dev unsermake libsdl-image1.2 libsdl-image1.2-dev libsdl1.2-dev libsamplerate0 libsamplerate0-dev libogg0 libogg-dev libvorbis0a libvorbis-dev libdv4 libdv4-dev libjack0.100.0-0 libjack0.100.0-dev sox sox-dev libxml2 libxml2-dev ladspa-sdk-dev libquicktime0 libquicktime-dev libtheora0 libtheora-dev ladspa-sdk swh-plugins libavformat0d libavformat-dev kdesvn build-essential libgtk2-dev libmad0 libmad0-dev autoconf automake1.9 dvgrab

```
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-shared --enable-vorbis --enable-libogg --enable-pp
make
sudo make install
cd ..
```
```
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
```
Hit <enter> for password
```
cvs -z3 -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt
cd mlt
./configure --enable-gpl --enable-shared --enable-theora --enable-vorbis --enable-libogg --enable-pp --enable-shared-pp --enable-motion-est --avformat-svn --prefix=/usr
make
sudo make install
cd ..
```
```
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
```
Hit <enter> for password
```
cvs -z3 -d :pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt++
cd mlt++
./configure --prefix=/usr
make
sudo make install
cd ..
```
Then start kdesvn from the menu OR type to terminal: ```
kdesvn
```
Go to --> Subversion --> General --> Checkout a repository
and add```
https://svn.sourceforge.net/svnroot/kdenlive/trunk/kdenlive 
```
as URL and your home folder as target. Hit ok.
```
cd kdenlive
make -f Makefile.cvs
./configure --prefix=/usr
make
sudo make install
```

Enjoy!
Thanks to the guy wrote this tutorial in the french ubuntuforums.
PS. To answer your question YaseenKriel this program is the best to grab and edit your stuff. But if you don't want to bother with all the compiling, you could just use Kino which uses the same capture tools as KDEnlive. See first post on how to install Kino.

---

### Post by P_Badger on 2006-12-22
Hey heys!

Just stumbled across this program while looking through Digg, it's a high-end video compositing program called "Fusion 5.1" that just recently released a Linux version. I'm not sure what the price is, but I'm sure it can't be cheap. ; ) Proprietary software that needs a powerful machine to run it.

Here's the link:

[http://www.eyeonline.com/Web/EyeonWeb/Products/fusion5/fusion5_linux.aspx](http://www.eyeonline.com/Web/EyeonWeb/Products/fusion5/fusion5_linux.aspx)

---

### Post by YaseenKriel on 2006-12-22
Kino requires firewire, will the other program use USB?

---

### Post by uuwatti on 2006-12-22
both use dvgrab so the answer is no. they suggest in dvgrab forums to use v4l controlled capture program, but i seriously doubt it will work. Suggestion: buy a firewire-card. programs that can capture from usb are rare even on windows, as the standard is still quite new. however, if you can play it somehow you can grab the stream with LiVES (or with number of programs)
And to P_Badger: OK I will add fusion to the list, but it is really expensive 4495,00 &#8364;. Which is a shame, because the only reason for my dual-booting is (now that I found KDEnlive) After Effects (and Cinema 4d, but I guess I can try Blender), and fusion would have filled that gap nicely. Oh, well Jahshaka is starting from ground zero next week, I just hope they get it right this time and really give a good open-source alternative to AE.

EDIT: Cinepaint Glasgow looks really promising and the release date is soon. Check the features from here: [http://cinepaint.blogspot.com/]("http://cinepaint.blogspot.com/")

EDIT 2: It's pretty weird that we have all these heavy-duty effects and copositing programs (like Houdini, Shake, Fusion, XSI and discreets Higgh-end stuff, but no proper NLE, which works like it should (like capturing or not-crashing-all-the-time) It seems that The Big Boys in Hollywood use Linux for FX and Macs for editing. [http://linuxmovies.org/]("http://linuxmovies.org/") <-- that explains a lot

---

### Post by Unterseeboot_234 on 2006-12-31
I was happy to find fonty python to manage fonts. Works like Adobe ATM. Lets you create font folders outside of the Fonts:/// and then sym-link. The linked fonts then can be turned on or off to update the font menu in whatever graphics software you're using. The limitation is TrueType only.

[**fonty python**]("http://wiki.wxpython.org/index.cgi/FontyPython")

I wanted your list to have this.

---

### Post by muhkayoh on 2007-01-06
Stopmotion has [a new version]("http://stopmotion.bjoernen.com/") that (among other things) apparently fixes a bug with respect to Edgy.  It would be really nice to see that in the official repositories as soon as somebody can get to it.  Well, it'd be nice for me at least. :D



Matt

---

### Post by Oki on 2007-01-13
Thanks again for this thread(or call it a bump)

---

### Post by smartalecks on 2007-01-16
Heya, just finished adding content to all the webdesign pages. I will try to do more in the future, but other people please help as well. It only takes a few minutes :D.

Also, to uuwatii, could you seperate (in webdesign) the frameworks from the actual applications? (like make a new catagory for "Frameworks")
qooxdoo and ZK are frameworks, not applications.

---

### Post by uuwatti on 2007-01-17
Thanks a lot! Now I need someone to work with the photgraphy section, because along with webdesign, digital photgraphy is something I know nothing about. (I still use regular film.. I know.. old-fashioned..) 
By the way screenshots are a good idea. I'll add some as well. Also, I moved all the stuff the way you suggested, except Nvu, which seems to have some problems. I'll add installation instructions as well later.

---

### Post by uuwatti on 2007-02-13
Updates: 
LightZone v.2.1 [here]("http://sonic.net/~rat/lightcrafts/release-2-1.html") blueMarine v0.9 EA8 [here]("https://bluemarine.dev.java.net/servlets/ProjectDocumentList?folderID=6654&expandFolder=6654&folderID=6654")
Krita v.1.6.1 [here]("http://kubuntu.org/announcements/koffice-161.php"); 
Cinepaint Glasgow release this week; 
Gogh updated; 
Inkscape 0.45 [here]("http://inkscape.org/download/?lang=en") 
Blender 2.43 in few days; 
LiVES 0.9.8.2 [here]("http://www.getdeb.net/app.php?name=lives")
Cinelerra 2.1 on Edgy [here]("http://ubuntuforums.org/showthread.php?t=320701")

---

### Post by uuwatti on 2007-02-25
A few new ones:
[COLOR="Red"][SIZE="5"]Cenon[/SIZE][/COLOR]
[Homepage]("http://www.cenon.info/frame_gb.html")
```
sudo aptitude install cenon.app
```



[COLOR="Red"][SIZE="5"]gsumi[/SIZE][/COLOR]
[Homepage]("http://www.gtk.org/~otaylor/gsumi/")
```
sudo aptitude install gsumi
```

---

### Post by misfitpierce on 2007-02-25
Awesome thanks for the post. Great help

---

### Post by vnt87 on 2007-03-04
Just wanted to add that for the CAD section, there's also VariCAD ([http://www.varicad.com](http://www.varicad.com) - proprietary)
And for the 3D section there is SideFX Houdini ([http://www.sidefx.com](http://www.sidefx.com) - proprietary). There is an Apprentice version that is available free of charge, it's pretty much like the Personal Learning Edition of Maya.

---

### Post by FyreBrand on 2007-03-04
> **Mountain Fog Studio said:**
> Never seen this or heard of this ```
aptitude
``` command.
Usually I use 
```
sudo apt-get install
```

Great List!Aptitude is another front end for apt, like apt-get.  Apt provides apt-get and it has Super Cow Powers.  Aptitude is a separate application is also Y2K-compliant, non-fattening, naturally cleansing, and housebroken and doesn't have Super Cow Powers.

You can use either, but I think it's generally best to stick with one and consistently use it.  Aptitude and apt-get handle recommends and suggests a little differently by default.  Apt-get tends only to install the absolute necessary packages while aptitude generally installs recommends (and maybe suggests) by default.  Aptitude also has an ncurses interface.  It use to be that aptitude handled package clean-up a little better but apt-get has an -autoremove switch will help remove unused dependencies.

Either way aptitude will still install packages just fine.

---

### Post by hikaricore on 2007-04-08
someone should really sticky this thread :P

---

### Post by eragorn on 2007-04-14
Has anyone come across any apps for fooling around with or creating hdr images??  So far I have to use my mac for this.  I use photomatix.

---

### Post by roketa on 2007-04-16
Qtpfsgui is a nice HDR program.

---

### Post by cookieofdoom on 2007-04-18
Great post! Thanks a lot!

> **hikaricore said:**
> someone should really sticky this thread :P

Agreed!

---

### Post by efflux on 2007-05-10
Thanks very much for the list. Very useful. In fact after discovering Lightzone I am transferring all my photo editing from my Mac to Linux on my PC. Forget Aperture or any competing program, Lightzone is where to go. You'll still need Gimp for more complex 2D editing but Lightzone for simple photo editing is fantastic.

One point worth changing on the list is that Anime Studio Pro Linux is now out. This is not a free program but worth the cost. It doesn't output any video formats with the Linux version and from my initial tests the swf ouput may have some problems. It does output image sequences which you could stitch into a movie on another app. However I expect this program to improve. It's a really fantastic animation app.

---

### Post by tcabeen on 2007-05-23
Keeping an awesome thread alive ...

I thought of this thread today when I found out about [http://www.osalt.com/](http://www.osalt.com/) through lifehacker.

They present open source alternatives on all platforms, so this isn't just good for us, finding software for Ubuntu.  It's also good to recommend to friends and family we just can't get to give up windows yet.  :D

---

### Post by uuwatti on 2007-05-24
updated the list for the first time in 3 months. sorry been busy. Lightzone for linux seems to be gone or the site is under construction. too bad, since this program is really, really good. hope they come back (i checked the forums and version 2.4 was released only 2 weeks ago for linux)

---

### Post by hikaricore on 2007-05-24
> **uuwatti said:**
> updated the list for the first time in 3 months. sorry been busy. Lightzone for linux seems to be gone or the site is under construction. too bad, since this program is really, really good. hope they come back (i checked the forums and version 2.4 was released only 2 weeks ago for linux)

[http://www.nabble.com/Re%3A-LightZone-Digest%2C-Vol-10%2C-Issue-11-tf3806093.html#a10790422](http://www.nabble.com/Re%3A-LightZone-Digest%2C-Vol-10%2C-Issue-11-tf3806093.html#a10790422)

Looks like it's just a mixup... hopefully not a coverup.

> **broken web: lightcrafts.com/linux**
[U]
by Anton Kast May 24, 2007; 02:58pm[/U]


[I]We certainly do have a serious web site problem here at Light Crafts.

When we revised [www.lightcrafts.com](www.lightcrafts.com) on Monday, we evidently broke many
things, including "lightcrafts.com", and including the entire Linux part
of the site.

Our new web server was not set up by experts.  The problem seems to be
some screwy virtual hosting configuration on there.  For me,
lightcrafts.com/linux gets the old content, but apparently not for all
web clients.

If you've been trying to get through, please stand by, and I'll let you
know when things make sense again.

Anton[/I]
_______________________________________________
LightZone mailing list
LightZone@...
[http://kast-dev.com/mailman/listinfo/lightzone](http://kast-dev.com/mailman/listinfo/lightzone) 

---

### Post by P_Badger on 2007-05-31
What I find curious is that the Lightzone people don't seem to have done anything to try and fix the screwed up Linux download section of their site. It's the ONLY thing that doesn't seem to be working, actually.

(Puts on tinfoil hat.)

---

### Post by Dragonbite on 2007-05-31
Has anybody mentioned that maybe a Wiki page should be made to keep a list of these programs, but people can update them as new features and versions come out?  It would be easier to reference than trying to look through all of these posts.

Just a thought.

[EDIT:]
Whoops! I didn't realize there already was one here : [[COLOR="Blue"]http://artlinux.wetpaint.com/?t=anon[/COLOR]]("http://artlinux.wetpaint.com/?t=anon")

---

### Post by hikaricore on 2007-06-05
> **P_Badger said:**
> What I find curious is that the Lightzone people don't seem to have done anything to try and fix the screwed up Linux download section of their site. It's the ONLY thing that doesn't seem to be working, actually.

(Puts on tinfoil hat.)

I've emailed them several times, still waiting for a response.

If anyone has the archived version of the linux build I will happily post it up somewhere for download. ^_^

la resistance!

---

### Post by P_Badger on 2007-06-05
> If anyone has the archived version of the linux build I will happily post it up somewhere for download. ^_^

Well, they do still have 2.4 for linux up on their site, at least. Had to do a wee bit of digging through the forums, here, in order to find the link.

[http://www-old.lightcrafts.com/linux/download.php](http://www-old.lightcrafts.com/linux/download.php)

---

### Post by kostkon on 2007-06-07
Great list!! Thanks!

---

### Post by JC_510 on 2007-06-07
My summers going to be very busy trying out all of these programs :p

Very useful thread, thanks. (Oh, and I agree it should be stickified!!):D

---

### Post by hikaricore on 2007-06-11
> **P_Badger said:**
> Well, they do still have 2.4 for linux up on their site, at least. Had to do a wee bit of digging through the forums, here, in order to find the link.

[http://www-old.lightcrafts.com/linux/download.php](http://www-old.lightcrafts.com/linux/download.php)

Thank you, I've emailed them many times on the subject and have been completely ignored.

Seems they're trying to cover up the existance of the linux version completely on their new site.

---

### Post by stani on 2007-06-11
For photo batch processing, I launch a new program: Phatch. You can use it for rotating, resizing, dropping shadows, ... (The list of plugins is still small, but will expand in the future.) It supports drag and drop from Nautilus, Konqueror, F-spot, Digikam, gThumb, ...

Phatch has a launchpad site:
[http://www.launchpad.net/phatch](http://www.launchpad.net/phatch)

The instructions are there how to install it, but to be sure:
```
sudo apt-get install bzr python-wxgtk2.8 python-imaging
bzr branch http://bazaar.launchpad.net/~stani/phatch/dev
```

For more info, read this thread:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

### Post by Merk42 on 2007-06-12
It should probably be noted that Maya PLE is not for Linux.

---

### Post by EyeBun2 on 2007-06-12
I have a fairly extensive list of Gimp tutorial links that I've collected over the year.  I will gladly share them. Again, this is specific to Gimp tutorials.

EyeBun2 Gimp Bookmarks

[http://del.icio.us/eyebun2](http://del.icio.us/eyebun2)

Not sure if this is an applicable post and apologies in advance if that's the case.

---

### Post by uuwatti on 2007-06-13
> **Merk42 said:**
> It should probably be noted that Maya PLE is not for Linux.

They used to have a ple for linux as well, but not anymore. Shame. 
BTW updated a few links to newer versions. I promise to check these once a month or so, so the list doesn't get dated.

---

### Post by goldfox_79 on 2007-10-07
Thanks a lot!

You post is very useful!

---

### Post by Dooglus on 2007-10-11
> **hikaricore said:**
> Very good list you'd made here :)

Just to let you know I've never been able to get Synfig to work either, tried compiling it on 3 systems now with all dependancies met and everything and it bombs out.

Did you report the bugs?  Somebody reported one today that was causing it to crash on startup, so I fixed it.  (svn r908).

Can you provide any more information other than 'it bombs out'?

Thanks.

The tracker URL is:
[http://sourceforge.net/tracker/?group_id=144022&atid=757416](http://sourceforge.net/tracker/?group_id=144022&atid=757416)

---

### Post by CAD-MAN on 2007-10-12
Wow, great list. Ive got some of those programs downloaded already, but it'll be great to try some of the others :D

---

### Post by ohmyiv on 2007-12-14
screem is pretty cool for web design

[http://www.screem.org/](http://www.screem.org/)

---

### Post by omega_user on 2007-12-16
nice list, many helpful links, semi-useful code snippets.  These types of forums that dish out all the possibilities for stuff people haven't explored yet are great. Good Work!

---

### Post by 99bluefoxx on 2007-12-20
what program do i use for editing the tags on OGG THEDORA video files?i riped a few dvds and they riped as" title on, title two" instead of the proper titles:(
is this the right thread for this question?

---

### Post by niceguy123 on 2008-01-14
What would be a good flash swf editor for linux?

---

### Post by Birk on 2008-01-21
I second the call for [COLOR="Red"]_Avidemux_[/COLOR].
It is still not in your list, but a nice relatively light weight and easy to use video editing software. It seems also pretty fast and easy to download/install in ubuntu.

---

### Post by wolfear on 2008-02-07
> **niceguy123 said:**
> What would be a good flash swf editor for linux?

I would even settle for one that wasn't good.
I only get asked about twice a year to design a flash logo, which desn't justify the cost of buying software (or reloading Windows for that matter).
f4l looks dead and the UIRA site doesn't have anything useful on it. It actually looks like it (the URIA site) hasn't been touched in a while, but that could just be me.
I would even settle for decent GIF animation in some cases. GIMP can do it, but not great.

---

### Post by stooshbunutu on 2008-02-19
Hiya,

Front end for metapixel

I've created a webpage that gerneates the script based on input fields to be copy-and-pasted into terminal to run the command.

It is the attached file, just save the .txt file as a .html file, open it in firefox, and enjoy.

Let me know what you think, I am currently working on converting it into a program front end

Hope you like it :)

---

### Post by carusoswi on 2008-03-01
Ok, I downloaded/installed Bluemarine.  I cannot find any evidence of it on my system, however.  If I open Synaptic Package manager, I can search and see that it is installed on my system, but, the program does not appear in any of my menus.

What did I do wrong?

Caruso

---

### Post by CaptainCabinet on 2008-03-01
A very useful list there. :)
This should be stickied.

---

### Post by Crafty Kisses on 2008-03-01
Thanks!

---

### Post by JCMe on 2009-09-01
This list is great.  I did note the missing program of Alice.  Not a true linux app, but it runs under wine.  Alice was the program by Randy Pausch (The Last Lecture) to teach programming by having a simple 3-D animation done by young children.  It is another effort to publish free software from Carnegie Mellon University. Download at [www.alice.org](www.alice.org).

---

### Post by rylleman on 2009-09-02
Good list!

I noticed **Pencil** is missing from trad. animation tools - [http://www.pencil-animation.org/]("http://www.pencil-animation.org/")
And there's a new video composite software called **Ramen** which looks very promising - [http://ramenhdr.sourceforge.net/screens.html]("http://ramenhdr.sourceforge.net/screens.html")

---

### Post by coldReactive on 2009-09-03
> UIRA OSS
UIRA.org
Early development. qflash and f4l merged to form this project. I have problems getting it to work.
Someone with more experience with compiling qt apps might wanna give this a try.

Seems URIA is gone, I can't seem to find it on the site provided.

---

### Post by uuwatti on 2009-09-04
I'm back to using Ubuntu, good news on the Ramen thing, that's what linux needs. I will update the list on the first page as soon as I have time.

---

### Post by coldReactive on 2009-09-04
Not to mention: [http://www.synfig.com/](http://www.synfig.com/)

Looks like a Joomla site, rather than a vector animation site o_O

it's too bad that Pencil's Ubuntu package is i386 only.

---

### Post by CFury on 2009-09-11
Don't know if this thread is being kept up however the GraphiteOne site appears to be down.  Sorry, didn't read through all the 13 pages here so not sure if it's been mentioned yet.

---

### Post by Darkaiser on 2009-09-13
good job:popcorn:

---

### Post by HappyHenry on 2009-09-13
Thank you very much, for such a great list.

---

### Post by SlonUA on 2010-03-29
nice list .. but:
[LIST][*]could u remove **PROPRIETARY** software or create another section in bottom of post[*]could u use official ubuntu wiki wiki.ubuntu.com (i'm not sure that smb. will create account on wetpaint with so many ads. or use **windows live id**)[*]also, it will be nice to remove all duplication, if u wanna point to Getdeb.net.[/LIST]

---

### Post by techunit on 2010-04-03
What would you recommend for raw conversion software? I am used to adobe camera raw. Obviously that is a windows program and I don't plan to continue to use windows apps in ubuntu so what do you recommend. I have used UFRAW and had great success with it.

---

### Post by Newfoundlander on 2010-05-13
> **walker935 said:**
> I really wish there was gimp with CMYK support. Then we'd have it all.

GIMP does have CMYK support.  There is a plug-in called [**Separate+**]("http://my.opera.com/area42/blog/gimp-cmyk").

---

### Post by iamgeniusrnti on 2011-03-11
I'm sorry for resurrecting a dead thread but there are so many options... is there an app that can import a video clip and allow me to paint lines and shapes over top of the video?

---

