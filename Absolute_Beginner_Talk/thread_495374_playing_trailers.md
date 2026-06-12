---
title: "playing trailers"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by kolhoznik on 2007-07-07
I am having trouble playing movie trailers, clips etc.  Does anyone have any idea what I could do to enable this?

---

### Post by Vajra Vrtti on 2007-07-07
What problems?
Playing what?

---

### Post by bodhi.zazen on 2007-07-07
could you be more descriptive of the problem exactly. Otherwise see :

Restricted formats

	[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

	[http://www.ubuntuforums.org/showthread.php?&t=182902](http://www.ubuntuforums.org/showthread.php?&t=182902)

---

### Post by kolhoznik on 2007-07-08
Playing standard quality trailers off Yahoo Movies but it will not play any of the HD Trailers.

---

### Post by Vajra Vrtti on 2007-07-08
The links recommended by bodhi.zazen probably will solve your problem.

---

### Post by trak87 on 2007-07-08
You need to give more information about what's not working, what player you are attempting to use and what sites you are trying to view.

---

### Post by kolhoznik on 2007-07-08
I am trying to use Totem Movie player for the HD clip and after the download I get this message:

The playback of this movie requires a text/html decoder plugin which is not installed.

I am just not sure which one I need.

---

### Post by neoguy2012 on 2007-07-08
It seems that these are qtl files.  Hmmm...  I can give you a quick and dirty method of playing them, but it's not a very nice method.  I hope someone else can figure out a better way of doing this...  Basically qtl files are xml files that store the information about playing the actual file.  I would recommend downloading the qtl file to your desktop.  For example, let's say I wanted to watch the Shrek 2 movie clip on 480p.  I would load up firefox (or your favorite browser) and go to the HD trailer site on yahoo:

[http://movies.yahoo.com/feature/hdtrailers.html](http://movies.yahoo.com/feature/hdtrailers.html)

Next, I would find Shrek 2, click on it, then click on 480p.  When it asks what to do with the file, choose to save it to disk.  Go to your desktop and open up the file in your favorite text editor (it automatically allows me to open it up in Kate on KDE... but it may be different for you).  It will look something like this:

```
<?xml version="1.0"?><?quicktime type="application/x-quicktime-media-link"?><embed src="http://playlist.yahoo.com/makeplaylist.dll?sid=37084129&embedded=yes&t=mov&br=2700&s=950752080&start=0&end=&afr=0&nodeid=2737152&d=75&tz=&pg=ODUyNDM4NDE0NDY5MDYyMm&authid=&sl=75&so=%252FYahoo%252FMovies%252FTrailers%252FShrek%2B2%252Ftrailer2%2528HD%2529&tcode=&sdm=web&pt=rd" autoplay="false" type="video/quicktime" controller="true" quitwhendone="false" cache="false" loop="false" name="test file"></embed>
```

the part that's most important is the link next to the src attribute.  Copy the URL inside the quotes:

```
http://playlist.yahoo.com/makeplaylist.dll?sid=37084129&embedded=yes&t=mov&br=2700&s=950752080&start=0&end=&afr=0&nodeid=2737152&d=75&tz=&pg=ODUyNDM4NDE0NDY5MDYyMm&authid=&sl=75&so=%252FYahoo%252FMovies%252FTrailers%252FShrek%2B2%252Ftrailer2%2528HD%2529&tcode=&sdm=web&pt=rd
```

Paste this link in firefox and it'll let you download the file in .mov format.  I believe you need to download some of the proprietary multimedia codecs.  Here's a link to how you can do this in a couple lines:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

I hope that helps!  Good luck!

---

### Post by Palmyra on 2008-05-03
neoguy, when I pasted the URL into Firefox bar, it tried to play the video instead of asking me to download it.  The video never played.

---

### Post by damis648 on 2008-06-10
You must press File>Save As and save it somewhere.

---

