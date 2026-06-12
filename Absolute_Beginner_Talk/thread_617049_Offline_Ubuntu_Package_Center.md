---
title: "Offline Ubuntu Package Center"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by cadcrazy on 2007-11-18
Hello Friends
After seeing many guys without internet access @ home asking for offline packages for ubuntu, i decided to create this thread where we can share offline packages.

You can also request for packages not listed here.

>  [COLOR="Sienna"]**_How To Install_**[/COLOR] : Copy all your downloaded packages to a folder say "software" on desktop or anywhere you find it suitable. Now launch terminal ( Applications -> Accessories -> Terminal) and type

[B]cd /home/cadcrazy/Desktop/software
sudo dpkg -i *.deb[/B]

[COLOR="Sienna"]Note: Replace cadcrazy with your username[/COLOR] :p 

This method will install all the deb packages whether or not all the dependencies are satisfied . So as a result you may get some broken packages chances of which are rare . If you get some error message while installing, to fix the problem type

**sudo apt-get install -f**

This command will remove the broken packge(s) if any and show you the name of removed package. To know the missing dependency double click on .deb and the packge manager will show the name of missing dependency.

[COLOR="Sienna"]PS: Report here in case of errors/missing dependencies[/COLOR]

Here is the List :

**[SIZE="2"][COLOR="Magenta"]Audio/Video[/COLOR]:[/SIZE]**
> [COLOR="Sienna"]_**Gstreamer**_[/COLOR] : Many applications in Ubuntu use the GStreamer open source multimedia framework including Totem and Rhythmbox to play proprietary audio/video files

Homepage: [http://gstreamer.freedesktop.org/documentation/plugins.html](http://gstreamer.freedesktop.org/documentation/plugins.html)

**32 bit download links** : [Gstreamer.zip]("http://jtzpwq.bay.livefilestore.com/y1pVpmzOri6j-K0nLRAVK07ZSJYBDctzr2CDkxPa6Cz0oFLYbfwSTVUL0nU3w3DbNLhcxwPt9TvQElaYrd97_GL6Q/Gstreamer.zip?download")
**64 bit download links** : NA 

>  [COLOR="Sienna"]_**VLC**_[/COLOR] : VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4, DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia streams from various network sources. VLC can also be used as a streaming server that duplicates the stream it reads and multicasts them through the network to other clients, or serves them through HTTP. VLC has support for on-the-fly transcoding of audio and video formats, either for broadcasting purposes or for movie format transformations. Support for most output methods is provided by this package, but features can be added by installing additional audio plugins (vlc-plugin-esd, vlc-plugin-sdl, vlc-plugin-arts) or video plugins (vlc-plugin-sdl, vlc-plugin-ggi, vlc-plugin-glide, vlc-plugin-svgalib). There is also a web browser plugin in the mozilla-plugin-vlc package.

Homepage: [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
[B]
32 bit download links[/B] : [vlc.zip]("http://jtzpwq.bay.livefilestore.com/y1pVpmzOri6j-Lkbe1LmFpY7dYoLypHNlFTJej1YuCjz2n9GVL32TSATfKue75jGfzOmIbgBLLM4KNPKmRn-sPmNA/vlc.zip?download")
**64 bit download links** : NA 

>  _[COLOR="Sienna"]**Exaile**[/COLOR]_ : Exaile is a media player aiming to be similar to KDE's Amarok, but for GTK+. It incorporates many of the cool things from Amarok (and other media players) like automatic fetching of album art, handling of large libraries, lyrics fetching, artist/album information via the wikipedia, last.fm support, optional iPod support (assuming you have python-gpod installed).

Homepage: [http://www.exaile.org/](http://www.exaile.org/)

**32 bit download links** : [exaile]("http://mirrors.kernel.org/ubuntu/pool/universe/e/exaile/exaile_0.2.10+debian-1.1ubuntu2_i386.deb"), [python-elementtree]("http://mirrors.kernel.org/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-11ubuntu1_all.deb"),[ python-mutagen]("http://mirrors.kernel.org/ubuntu/pool/main/m/mutagen/python-mutagen_1.11-1_all.deb"), [python-pyogg]("http://mirrors.kernel.org/ubuntu/pool/main/p/pyogg/python-pyogg_1.3-1.1ubuntu4_i386.deb"), [python-pysqlite2]("http://mirrors.kernel.org/ubuntu/pool/main/p/python-pysqlite2/python-pysqlite2_2.3.4-2_i386.deb"), [python-pyvorbis]("http://mirrors.kernel.org/ubuntu/pool/main/p/pyvorbis/python-pyvorbis_1.3-1.2ubuntu2_i386.deb")
**64 bit download links** : [exaile]("http://mirrors.kernel.org/ubuntu/pool/universe/e/exaile/exaile_0.2.10+debian-1.1ubuntu2_amd64.deb"), [python-elementtree]("http://mirrors.kernel.org/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-11ubuntu1_all.deb"), [python-mutagen]("http://mirrors.kernel.org/ubuntu/pool/main/m/mutagen/python-mutagen_1.11-1_all.deb"), [python-pyogg]("http://mirrors.kernel.org/ubuntu/pool/main/p/pyogg/python-pyogg_1.3-1.1ubuntu4_amd64.deb"), [python-pysqlite2]("http://mirrors.kernel.org/ubuntu/pool/main/p/python-pysqlite2/python-pysqlite2_2.3.4-2_amd64.deb"), [python-pyvorbis]("http://mirrors.kernel.org/ubuntu/pool/main/p/pyvorbis/python-pyvorbis_1.3-1.2ubuntu2_amd64.deb")


[Mplayer]("http://cid-382ddf3833ef404c.skydrive.live.com/self.aspx/Public/Ubuntu%20APT-ON-CD/Mplayer.iso") (32 bit)
[Gxine+libxine1-ffmpeg]("http://cid-382ddf3833ef404c.skydrive.live.com/self.aspx/Public/Ubuntu%20APT-ON-CD/Gxine+libxine1-ffmpeg%20.iso") (32 bit)
[Amarok]("http://cid-382ddf3833ef404c.skydrive.live.com/self.aspx/Public/Ubuntu%20APT-ON-CD/Amarok.iso") (32 bit)

**[SIZE="2"][COLOR="Magenta"]Audio/Video[/COLOR]:[/SIZE]**
> [COLOR="Sienna"]**_GnomeBaker_**[/COLOR] : Gnomebaker is an easy to use CD/DVD burner. Its current features includes Data and audio CD burning, Multisession CDs, DVD formating, DVD data disk burning, On-the-fly data CD burning, Cue bin data CD writing[SIZE=3][COLOR=Red][COLOR=Black][SIZE=2][COLOR=black]

Homepage : [http://sourceforge.net/projects/gnomebaker]("http://sourceforge.net/projects/gnomebaker")

32 bit download links[/B] : [gnomebaker]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomebaker/gnomebaker_0.6.2-2_i386.deb"), [icedax]("http://mirrors.kernel.org/ubuntu/pool/universe/c/cdrkit/icedax_1.1.6-1ubuntu3_i386.deb")[/COLOR]
** 64 bit download links** : [/SIZE][/COLOR][/COLOR][/SIZE][SIZE=3][COLOR=Red][COLOR=Black][SIZE=2][COLOR=black][gnomebaker]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gnomebaker/gnomebaker_0.6.2-2_amd64.deb"), [icedax]("http://mirrors.kernel.org/ubuntu/pool/universe/c/cdrkit/icedax_1.1.6-1ubuntu3_amd64.deb")[/COLOR][/SIZE][/COLOR][/COLOR][/SIZE]
**[SIZE="2"][COLOR="Magenta"]Cad/Design [/COLOR]:[/SIZE]**
> 
[COLOR="Sienna"]_**Blender**_[/COLOR] : Blender needs no introduction.Blender is an integrated 3d suite for modelling, animation, rendering,post-production, interactive creation and playback (games). Blender has its own particular user interface, which is implemented entirely in OpenGL and designed with speed in mind. Python bindings are available for scripting; import/export features for popular file formats like 3D Studio and Wavefront Obj are implemented as scripts by the community. Stills, animations, models for games or other third party engines and interactive content in the form of a standalone binary and/or a web plug-in are common products of Blender use.

Homepage: [http://blender.org/](http://blender.org/)

**32 bit download links** : [Blender]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fblender%2Fblender_2.44-2ubuntu2_i386.deb&md5sum=efb930ac771b501aa7e9d785057506ff&arch=i386&type=main"), [Gettext]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgettext%2Fgettext_0.16.1-2ubuntu3_i386.deb&md5sum=3bdc1318b7502465132989854754b410&arch=i386&type=main"), [libopenexr2c2a]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fo%2Fopenexr%2Flibopenexr2c2a_1.2.2-4.3ubuntu2_i386.deb&md5sum=bb3342c35d44b0422ad2e95eb615c3af&arch=i386&type=main")
**64 bit download links** : [Blender]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fb%2Fblender%2Fblender_2.44-2ubuntu2_amd64.deb&md5sum=6521b3517db1cabe602d516e705b7a0e&arch=amd64&type=main"), [Gettext]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fg%2Fgettext%2Fgettext_0.16.1-2ubuntu3_amd64.deb&md5sum=3570ddb6a80227df15ff20e70b504161&arch=amd64&type=main"), [libopenexr2c2a]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fo%2Fopenexr%2Flibopenexr2c2a_1.2.2-4.3ubuntu2_amd64.deb&md5sum=67131ec79c252b91efcf632d8f53d52d&arch=amd64&type=main")



Will Keep on adding ----------------

---

### Post by vasiliymeshko on 2007-11-19
On-disk.com offers complete Ubuntu repositories on DVD's for about $30 ( Check[ http://on-disk.com/product_info.php/cPath/28_135_178/products_id/360]("http://on-disk.com/product_info.php/cPath/28_135_178/products_id/360") ). Same story here with Ubuntu on PC's with no internet access, and these DVD's were godsend to me.

---

### Post by cadcrazy on 2007-11-19
But these are not updated ones and here you can find the latest packages that too free not for 30 $. And these are not available to all countries as i hope.

---

### Post by cadcrazy on 2007-11-24
**[COLOR="Magenta"]Addded Blender[/COLOR]**

---

### Post by cadcrazy on 2007-11-30
**[COLOR="Magenta"]Amarok added[/COLOR]**

---

### Post by cadcrazy on 2007-12-16
[COLOR="Magenta"]**Added Exaile and GnomeBaker**[/COLOR]

---

