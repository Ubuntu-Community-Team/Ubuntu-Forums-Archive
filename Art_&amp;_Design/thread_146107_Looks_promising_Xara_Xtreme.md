---
title: "Looks promising: Xara Xtreme"
date: 2006-03-17
forum: Art &amp; Design
---

### Post by Peturrr on 2006-03-17
Anybody has already seen this 'new' opensource graphics software for Linux?
They pretend it's a killer app. It made me quite enthousiast. But it looks like almost nobody knows it exists. What do you think?

[http://www.xaraxtreme.org](http://www.xaraxtreme.org)

The movies on that site show quite some power of it!
[http://downloads.xara.com/products/xtreme/movies/intro2.mov](http://downloads.xara.com/products/xtreme/movies/intro2.mov)

---

### Post by commodore on 2006-03-18
I think I have to use it just to support the idea of turning a properiaty app into free software. I have heard of it before. I even tried it out.

---

### Post by majikstreet on 2006-03-18
hey, that's cool! A little advanced looking though - but I think that'd be good to show to new linux users worried about losing XXX graphics program.

---

### Post by Dreams on 2006-03-19
Looks really cool! Unfortunatly i can't get it to work on Dapper. I need libstdc++.so.5 and i don't know how to install that :(

---

### Post by Peturrr on 2006-03-19
You'll need to 
```
sudo apt-get install libstdc++5
```
According to the info in synaptic this will install '/usr/lib/libstdc++.so.5' among other files.
It works on my dapper installation.

---

### Post by eriqk on 2006-03-19
Has anyone managed to build it on Breezy? I can't get past the ./configure stage.
Xara looks really cool, though. I think it's a potential Killer App.

Groet, Erik

---

### Post by Dreams on 2006-03-19
[QUOTE=Peturrr]You'll need to 
```
sudo apt-get install libstdc++5
```
According to the info in synaptic this will install '/usr/lib/libstdc++.so.5' among other files.
It works on my dapper installation.[/QUOTE]
Thanks
[img]http://uploader.64kpixels.net/img/itworks.jpg[/img]

---

### Post by Peturrr on 2006-03-19
[QUOTE=eriqk]Has anyone managed to build it on Breezy? I can't get past the ./configure stage.
Xara looks really cool, though. I think it's a potential Killer App.

Groet, Erik[/QUOTE]
I didn't build anything from source. Are you sure you cannot just download the recommended version from [http://www.xaraxtreme.org/download/](http://www.xaraxtreme.org/download/) and run XaraLX after extraction to a directory? It's allready compiled.
Ofcourse you need the lidstdc++5 to run it.

---

### Post by bradlis7 on 2006-03-21
I've used that program on windows. It has a lot of cool features that I'd like to see in other programs, but it is lacking in a lot of areas. I think it's a vector based program, so maybe inkscape will someday will incorperate a lot of the features of xara xtreme, and even outdo it. Or even better, the GIMP and inkscape become one mega cool program.

---

### Post by s|k on 2006-03-21
[QUOTE=bradlis7]I've used that program on windows. It has a lot of cool features that I'd like to see in other programs, but it is lacking in a lot of areas. I think it's a vector based program, so maybe inkscape will someday will incorperate a lot of the features of xara xtreme, and even outdo it. Or even better, the GIMP and inkscape become one mega cool program.[/QUOTE]
Inkscape is amazing, but as I love vector programs I'm going to give this one a try! :)

It's downloading at 7kb/s lol. :(

---

### Post by Jordao on 2006-03-21
I've installed in my ubuntu dapper and it works fine but i can't save the images i create. anybody with the same problem???

---

### Post by eriqk on 2006-03-21
[QUOTE=Peturrr]I didn't build anything from source. Are you sure you cannot just download the recommended version from [http://www.xaraxtreme.org/download/](http://www.xaraxtreme.org/download/) and run XaraLX after extraction to a directory? It's allready compiled.
Ofcourse you need the lidstdc++5 to run it.[/QUOTE]

Ah, ok, I guess I'll try that then. I have libstdc++5 so that shouldn't be a problem.

Groet, Erik

---

### Post by s|k on 2006-03-21
I can't even run the autoreconf:

```
autopoint: *** cvs program not found
autopoint: *** Stop.
autoreconf: autopoint failed with exit status: 1

```

This is after I installed the wxWidgets as explained here:
[http://www.xaraxtreme.org/developers/documentation/xara_lx_linux_build_instructions.html](http://www.xaraxtreme.org/developers/documentation/xara_lx_linux_build_instructions.html)


EDIT: Installing CVS helped. :::|

---

### Post by s|k on 2006-03-21
Wont install for me. I get this error:

[http://ubuntu.pastebin.com/614857](http://ubuntu.pastebin.com/614857)

---

### Post by Dreams on 2006-03-22
[QUOTE=Jordao]I've installed in my ubuntu dapper and it works fine but i can't save the images i create. anybody with the same problem???[/QUOTE]
Saving doesn't work jet, linux xara is still work in process

---

### Post by s|k on 2006-03-22
[QUOTE=Dreams]Saving doesn't work jet, linux xara is still work in process[/QUOTE]
lol, well I couldn't even install it, even though I had all the dependencies.

---

### Post by welshbyte on 2006-03-24
I couldn't get it past the autoreconf stage on dapper. Here's my autoreconf output with errors highlighted at the bottom: [http://ubuntu.pastebin.com/619370](http://ubuntu.pastebin.com/619370)

If I ignore the autoreconf error and go on with the ./configure it doesn't throw any errors at me. The make stage bombs out with exactly the same error as s|k: [http://ubuntu.pastebin.com/614857](http://ubuntu.pastebin.com/614857)

Sigh. Any ideas?

---

### Post by eriqk on 2006-03-26
[QUOTE=Peturrr]I didn't build anything from source. Are you sure you cannot just download the recommended version from [http://www.xaraxtreme.org/download/](http://www.xaraxtreme.org/download/) and run XaraLX after extraction to a directory? It's allready compiled.
Ofcourse you need the lidstdc++5 to run it.[/QUOTE]

Just did this, and it works.
Too bad it's still so early in developement (some of my favourite tools aren't even implemented yet), but it looks really cool.
The example .xars are impressive, btw.

Groet, Erik

---

### Post by joehill on 2006-03-26
I just downloaded it--both the "stable" version and the snapshot.  The snapshot, which apparently is built daily (so no need to compile it), has a lot of features that the "stable" one doesn't have, but it still isn't functional for saving/opening and a lot of other things.  But some of the features are really fun to play with and look very promising.  I hope some developers will get interested in this and contribute.  It makes a lot of stuff relatively easy that seem much more complicated to do in GIMP, Photoshop, or Inkscape (watch the cool videos on their site).

Their development model is one I've never seen before--a GPL'd Linux version and a commercial Windows version.  They're hoping some of the Linux developers will give them permission to use their code in the Windows version.  I don't know if a lot of Linux developers would accept that, but it's an interesting idea.

---

### Post by mojo on 2006-03-26
:D This is a good news for Linux users. We begin to see many commercial Linux programs ported over. Btw, have u seen the comparsion performance chart, the Xara CDraw engine is crazily fast, I wish one day when Xara CDraw is GPL-ied, GNOME might merge them to replace the low perfomance Cairo.

---

### Post by commodore on 2006-03-27
I don't want Linux to have commerical apps ported to it. I want the commercial apps to be made free software as Xara.

---

### Post by s7eam on 2006-03-31
Great to see comercial software turning to open source. 
I've tried this program and I must say it looks impressive, I like it allready.
I guess this will develop soon to new "Photoshop" for Linux users. :) 

Though, much is left to do but when you look at their subversion developing it looks very very promising. Every day comes new subversion.

---

### Post by s7eam on 2006-03-31
[QUOTE=bradlis7]I've used that program on windows. It has a lot of cool features that I'd like to see in other programs, but it is lacking in a lot of areas. I think it's a vector based program, so maybe inkscape will someday will incorperate a lot of the features of xara xtreme, and even outdo it. Or even better, the GIMP and inkscape become one mega cool program.[/QUOTE]

I don't know what does this program lacks but I know that there are no other graphic tool available on the market with this speed.

Take a look at Xara Gallery ;) 
[http://www.xara.com/gallery/](http://www.xara.com/gallery/)

---

### Post by wyo on 2006-04-06
[QUOTE=Peturrr]
[http://www.xaraxtreme.org](http://www.xaraxtreme.org)
[/QUOTE]

I'd really like to see Xara LX in Ubuntu (Dapper) but it might not happen because of this sad story [http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb](http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb)

O. Wyss

---

### Post by Alexander Grundner on 2006-06-23
[QUOTE=wyo]I'd really like to see Xara LX in Ubuntu (Dapper) but it might not happen because of this sad story [http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb](http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb)

O. Wyss[/QUOTE]
FYI, it's already in the Debian repo - [http://packages.debian.org/unstable/graphics/xaralx](http://packages.debian.org/unstable/graphics/xaralx)

I'm waiting with great anticipation to see xaralx added to the Ubuntu Dapper repo :D

---

