---
title: "Flash development"
date: 2009-10-07
forum: Art &amp; Design
---

### Post by fhll on 2009-10-07
Does anyone know if there is an IDE that I can use in open source to create .swf files for web? Currently I use Adobe Flash on a windows box at work, and want to blow it completely away to run a superior Ubuntu Os. :)

Thanks
f

---

### Post by Dragonbite on 2009-10-07
> **fhll said:**
> Does anyone know if there is an IDE that I can use in open source to create .swf files for web? Currently I use Adobe Flash on a windows box at work, and want to blow it completely away to run a superior Ubuntu Os. :)

Thanks
f

I don't think so, but I hope I am wrong.

I think the closest thing I've found so far is [[COLOR="Blue"]Pencil[/COLOR]]("http://www.pencil-animation.org/") which is a 2D drawing program that can export to .swf if I remember right.  It may be a Windows-only feature, I'm not sure.

Otherwise, Adobe Flex is the next closest thing.

---

### Post by Bölvaður on 2009-10-07
[http://sourceforge.net/project/screenshots.php?group_id=87799]("http://sourceforge.net/project/screenshots.php?group_id=87799")

[F4L]("http://sourceforge.net/projects/f4l/")

---

### Post by lukeiamyourfather on 2009-10-07
There are some tools for creating animations but nothing that is fully featured. The best way to go for specialized programs native to Windows is to run a virtual machine with something like VirtualBox and install Windows and the application. Cheers!

---

### Post by fhll on 2009-10-07
> **Bölvaður said:**
> [http://sourceforge.net/project/screenshots.php?group_id=87799](http://sourceforge.net/project/screenshots.php?group_id=87799)

[F4L]("http://sourceforge.net/projects/f4l/")

F4L looks promising, Ill give it a go, Thanks!
:)

---

### Post by alex.rayu on 2009-10-08
If you work with Flash all the time, you can't help using Windows. F4L seems to be abandoned. It is impossible to seriously recreate Adobe Flash with OpenSource - too much work to be done. If you dont need the latest flash, you can run Flash 8 in Wine well. But if you want latest Flash, it's eather VBox or just Win.

---

### Post by Dragonbite on 2009-10-08
Slowly, Adobe seems to be bringing things to Linux so hopefully, some day Flash (development) will come too.  That is, once they have their business model in place.

---

### Post by alex.rayu on 2009-10-08
Yeah. Would love to see their whole suite on Linux.

---

### Post by Niva on 2009-10-08
I wouldn't hold my breath for it, not unless Linux manages to make more of an impact in the overall number of people who actually use it.  Until then we should just be happy that we get a buggy flash player for linux.

Flash is getting a bit bloated imo lately.  I guess from the business perspective it's what Adobe wants to do with the technology.  But from the www perspective it's definitely not working out as I thought it would at first when flash came out.

---

### Post by alex.rayu on 2009-10-09
"Flash gets bloated" +1

---

### Post by Sub101 on 2009-10-09
What I use at the moment for basic flash is GIMP with the [export flash plugin.]("http://registry.gimp.org/node/14983")

Another useful addition is the gimp gap plugin.

Flowing through a display of images can be created easily by Filters > Animation > Blend, then export that image as Flash.

For me its fine as all I want to do is cycle through images, it is very basic though.

---

### Post by Dragonbite on 2009-10-09
> **Niva said:**
> I wouldn't hold my breath for it, not unless Linux manages to make more of an impact in the overall number of people who actually use it.  Until then we should just be happy that we get a buggy flash player for linux.

Flash is getting a bit bloated imo lately.  I guess from the business perspective it's what Adobe wants to do with the technology.  But from the www perspective it's definitely not working out as I thought it would at first when flash came out.

Could always use Silverlight/Moonlight instead, except nobody else is using it yet.

If it ever does, though, I would hope that Moonlight would be open enough that they could build an IDE for it which works with Silverlight.  

But I think I have a better chance of seeing Flash for Linux.

---

### Post by Tibuda on 2009-10-09
> **Niva said:**
> Flash is getting a bit bloated imo lately.  I guess from the business perspective it's what Adobe wants to do with the technology.  But from the www perspective it's definitely not working out as I thought it would at first when flash came out.

Sure. With browsers like Chrome/ium working on JavaScript performance, many of stuff that used Flash in the past don't need it anymore. Those libraries like jQuery make it even easier than Flash IDE, if you know JavaScript.

---

### Post by hessiess on 2009-10-09
HTML 5, though there is absolutely no support in IE.

---

### Post by kayosiii on 2009-10-09
No but Google and some others are making server side shims that leverage existing technologies like flash and silverlight compatibility for IE.(and other browsers that don't support html5 yet)

---

### Post by vinutux on 2009-10-11
stay on windows (i know its hell...but..) until adobe make flash for Linux platform............

---

### Post by coldReactive on 2009-10-11
> **vinutux said:**
> stay on windows (i know its hell...but..) until adobe make flash for Linux platform............

They won't, as long as windows has such market share.

---

### Post by mendozaro on 2009-10-12
Some older (not that old actually) versions of flash work in wine. Its a good option.

Another good option is VirtualBox + win xp + your flash.

I advise Wine and VirtualBox as a solution with all my heart. I used this combination for real business for a while. The tested version is Flash 8. That is also the last version of flash i acquired.

---

### Post by alex.rayu on 2009-10-13
Flash 8 works in Wine.
Virtual Box will run any Flash. It is a good option, if you have lots of RAM. If your job is only Flash though, then no sense to switch.

---

### Post by vinutux on 2009-10-13
> **alex.rayu said:**
> Flash 8 works in Wine.
Virtual Box will run any Flash. It is a good option, if you have lots of RAM. If your job is only Flash though, then no sense to switch.

but cs3 faild to work for me under wine.............

---

### Post by alex.rayu on 2009-10-13
CS3 is the next after Flash 8. It does not work, sadly.

---

### Post by ch1mp on 2009-11-03
Hey,

The flex SDK is open source, you can compile swfs with it in linux and write code with a text editor.

if you are looking for a replacement for the ide however you're in for a long wait. adobe have renamed the flex SDK the flash SDK recently as part of updating everything ready for the release of CS5. no sign of the flash SDK on linux yet.

for coding some people suggest eclipse + axdt. i'm going for that option at the moment as soon as probs i'm experiencing with karmic koala and eclipse are sorted out!

apart from that there is some talk of flashDevelop coming to linux, which would be perfect.

check out osflash.org, it's been the home of open source flash for quite a while. i'm going to be checking out haxe, i have it installed but need to find a good editor for it on linux...

---

### Post by kayosiii on 2009-11-03
It all depends on whether you are wed to a single application approach... Flash has a lot to offer as a complete platform - especially if your primary focus is graphic design. Flash Authoring isn't going to happen any time soon natively in linux.

What is more likely at least in the medium term is that emerging technologies will gain authoring tools on Linux.

Here are some projects that provide server side shims for existing web browsers.

[http://code.google.com/p/svgweb/](http://code.google.com/p/svgweb/)
[http://excanvas.sourceforge.net/](http://excanvas.sourceforge.net/)

---

