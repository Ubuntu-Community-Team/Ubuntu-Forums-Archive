---
title: "Anyone using Anime Studio Pro?"
date: 2007-11-03
forum: Art &amp; Design
---

### Post by Unterseeboot_234 on 2007-11-03
Hello, I was looking through the 2D offerings and came across mention of a commercial (you buy it) software solution called Anime Studio Pro. Trial download works with import/export limitations for 30 days. In the download section the company specifically mentions this software will **NOT** work on Ubuntu 64-bit. I suspect because of GTK 2.0+ is needed. Anyhow, to make a short story long, I do get the trial, from a public folder on my desktop and to run in 64-bit Gutsy with error warnings in the console at startup:
> 
(ASP.donotrunme:8727): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

(ASP.donotrunme:8727): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory


That is, I can save my original work in  this software's project file format.

I'd seriously consider purchase of the software ($179 USD) if I knew it would export out because one thing it offers is the .swf format.  I'm just concerned Anime Studio Pro will want 32-bit libraries for the exporting.

---

### Post by IanW on 2007-11-03
have you tried it with "getlibs" from [this thread?]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---

### Post by Unterseeboot_234 on 2007-11-03
Wow! I was reluctant but thought I would try your suggestion. getlibs worked like a charm. NO ERRORS. In the meantime I found the forums for the users of Anime Studio Pro. An Edgy 32-bit user getting help from the developers. There are issues but they have work-arounds. Issues like getting audio to work with a .swf and that takes 3rd Party polish like Cinelerra. But, I'm very impressed with what I've done in 1 hour's time with AS Pro demo trial version and trying out some of the tutorials.

---

### Post by Ralphie on 2007-11-06
ive seen some things on this, it has some really nice features, it works just like flash, except there are tools to make character animation much easier. that is pretty cool that they have an official port to linux. I might have to switch from flash to this when cs3 starts to date.

the only thing that would hinder me is that it is geared toward anime fans, of which, i am not :)

although, ive seen some good things done with it that were not anime.

---

### Post by Steveway on 2007-11-06
Before buying you should check out Synfig and Ktoon.
Maybe you like them as much as the commercial alternatives and you can save some money.

---

### Post by Unterseeboot_234 on 2007-11-07
Well, I've used the Trial version now for about a week. There are some very nice features in ASpro that no other animation program has, including Flash. The Trial version won't let you export to the Shockwave -- the only movie format available in the Linux version.

I have tried the KToon and Synfig. KToon is very basic alpha proof-of-concept. Synfig needs some more work also. I hope more dev gets done on both of them. My deepest hope would be that Inkscape begins accomplishing animation, with a timeline window. SVG is the future of vector art. I hope Linux shows the way before M$ messes it up.

Back to ASpro, beautiful tutorials show how to make vector art look like brush artwork. Rendering is like having a camera on a boom crane, which adds a lot of effects. ASpro is a weak drawing tool. It's drawing tools draw just enough to to aid other, imported art work. It is the bones feature of ASpro that sets it apart. And, the ability to link an audio file to those bones. Bones can even be added to bitmap images.

I was impressed I was able to make a 64-bit Ubuntu run ASpro even when eFrontier says on their website that their product will NOT run on 64-bit Ubuntu.

Having tried several different drawing to animation packages. Flash rules, but lets hope packages like ASpro, Synfig and KToon (and maybe Inkscape) start a new "branch" of SVG animation.

---

### Post by rylleman on 2008-04-25
Thank you!
ASP is one of my main tools and this thread helped me get it work on my 64-bit system.

---

### Post by MarkBremmer on 2008-12-20
Hi everyone,

If you're interested, I've posted new [**_Anime Studio Pro tutorial section on my site_**]("http://www.markbremmer.com/3Bpages/animestudiopro.html"). It's such a cool program! Since I use it professionally, many of the tips and tricks I offer are "real world" stuff. 

Just let me know if you have any questions. I do try to respond to everything and I do support the tutorial series for folks using it. 

Thanks for letting me poke my head in here.

Best regards,
Mark

---

