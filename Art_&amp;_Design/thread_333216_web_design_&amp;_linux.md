---
title: "web design &amp; linux"
date: 2007-01-07
forum: Art &amp; Design
---

### Post by benoitc on 2007-01-07
I am currently tryng to find a way to work professionnaly under GNU/Linux in web graphism & development.

What's bug be for now is problem of compatibility between photoshop & gimp or such things. From time to time i have to work with graphists that use last adobe product. And havind a bad render in gimp don't help. So how do you manage it ?

I'm also interrested in testimonials from professionals about their experience on it. Do you have some work to show ? About that , how is managed ubuntu website ?

let's go for the thread now :)

- benoit

---

### Post by ingo on 2007-01-07
ubuntu website is run using dokuwiki, no idea about the rest, sorry

---

### Post by benoitc on 2007-01-07
> **ingo said:**
> ubuntu website is run using dokuwiki, no idea about the rest, sorry

thought it was moinmoin ? does it change since ?

---

### Post by 23meg on 2007-01-07
> From time to time i have to work with graphists that use last adobe product. And havind a bad render in gimp don't help. So how do you manage it ?Honestly I've never had interoperability problems with GIMP, and upon hearing that, a few people I know dropped their pirated copies of Photoshop in favor of GIMP on the Windows platform and haven't looked back.

If you do have problems, Photoshop runs quite fine under WINE.

For a testimonial I agree with, see [this thread]("http://www.ubuntuforums.org/showthread.php?t=314780"). I have no problem developing with Aptana, and as long as you do standards compliant CSS based design you're unlikely to have significant problems using Ubuntu or any other flavor of Linux.

---

### Post by benoitc on 2007-01-07
> **23meg said:**
> Honestly I've never had interoperability problems with GIMP, and upon hearing that, a few people I know dropped their pirated copies of Photoshop in favor of GIMP on the Windows platform and haven't looked back.

the problem appear when you get some psd that use fx layer . And the fact that gim don't handle text layer could be annoying. See this thread about it :
[http://bchesneau.info/articles/2006/11/08/photoshop-vs-gimp](http://bchesneau.info/articles/2006/11/08/photoshop-vs-gimp)

Other stuff works good. I only need vim to code :)

---

### Post by 23meg on 2007-01-07
> **benoitc said:**
> the problem appear when you get some psd that use fx layer . And the fact that gim don't handle text layer could be annoying. See this thread about it :
[http://bchesneau.info/articles/2006/11/08/photoshop-vs-gimp](http://bchesneau.info/articles/2006/11/08/photoshop-vs-gimp)

Other stuff works good. I only need vim to code :)People develop working habits that overcome such glitches over time. Whenever I go to a printing house that uses Macs, the first thing they ask is "Did you convert the text to paths?" because they're used to having font problems, especially with Illustrator, and designers adapt the habit in turn, giving up on the convenience of having editable text. Not an optimal solution, but it works and saves the day.

Compromises happen with "professional" proprietary software as well, and interoperability often involves compromises in many areas, not just this.

---

### Post by ingo on 2007-01-07
> **benoitc said:**
> thought it was moinmoin ? does it change since ?

sorry mate, moinmoin it is!

---

### Post by benoitc on 2007-01-08
> **23meg said:**
> People develop working habits that overcome such glitches over time. Whenever I go to a printing house that uses Macs, the first thing they ask is "Did you convert the text to paths?" because they're used to having font problems, especially with Illustrator, and designers adapt the habit in turn, giving up on the convenience of having editable text. Not an optimal solution, but it works and saves the day.
This appear when work is finished. But when som graphist share with you the last photoshop of the page you're working on you can't play like it. And there is always the problem with shadow and such. That's the problem.

> **23meg said:**
> Compromises happen with "professional" proprietary software as well, and interoperability often involves compromises in many areas, not just this.

There have been always problem with interoperability. And I 'm used with it since a long time.  But in case of graphism, I didn't find a good way to manage without having finally the same software. Or did you find a better way ?

---

### Post by Simanek on 2007-01-09
I'm a web designer that's just converting from OSX to Linux. If interacting with PSDs is a big concern, you can always buy Photoshop and install in Ubuntu:

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

I haven't done it, but looks like it's worth trying. Otherwise, I'd get the people you are collaborating with to send you flattened TIFFs instead.

There is also a program called 'Pixel' that might be worth looking into. Perhaps it can import PSDs with the layers intact. You have to pay for it, but it's cheap.

Another note on interoperability with CS or CS2: Even if you are running Photoshop 7 you can't open those files with the layer effects intact. Photoshop will continue to change and Adobe's interest is in selling Photoshop. They don't need to interoperate with anybody if they don't want to. All the more reason to promote the use of the GIMP, Inkscape and other open source graphics applications to the graphics professionals around you.

I have a question for you. Your use of the terms 'graphism' and 'graphists' are strange to me. As far as I know the proper terms are 'graphics' or 'graphic arts' and 'graphic designers' or 'commercial artists'. Could you explain? Just curious.

---

### Post by Elijah on 2007-04-30
Well, we have here around 9 linux boxes for web development... most of the tools we used are gimp, vnc, and a few editors. For ie6/7 & safari checks we sometimes use ie4linux, konqueror, vnc to another windows machine and one of those browser screenshots service (ipinfo's netrenderer & browsrcamp) 

yeah, the problem part is when the customer sends out psd's and looks garbled in gimp. We had to rely on screenshots to get the cut-up images instead.. if there is a better way of making this work I'd definitely like to know.

Maybe photoshop can somehow export to xcf??

---

### Post by mech7 on 2007-04-30
I have the same problem.. photoshop does run under under WINE but it has it's bug if you can work with GIMP then that would be a solution personally it would only slow me down. Got prety much everything running XAMPP, Dreamweaver, Zend Studio, IE 6 (Ie7 under virtual pc) 

But for now I stay at windows for work as Adobe suite just works and I don't have any headaches's with WINE,

---

### Post by skullmunky on 2007-04-30
doing web design as a profession, no matter what platform, means suffering the most excruciating hell of interoperability issues as a permanent occupational hazard, not just in production tools but of course in the final product itself!  :)    

but for tools - it's a good point that if you need frequent and rapid file exchange in the workflow between artists then interoperability's important.  i keep an assortment of different versions of things around - old versions of photoshop, illustrator, weird things like Quark, a couple of machines still running mac os 9, etc just 'cause you never know.    so i guess my answer would be to mostly keep using gimp but keep a copy of photoshop around for situations like that.  and encourage other people to use gimp too, and make life easier and free-er.

really the thing to do is just improve layer effect support in gimp.  can't be that hard, right...?  

i think maybe graphisme is a french term...  though fr.wikipedia.org points out that

"Le terme design graphique est parfois aujourd'hui préféré au terme graphisme, jugé trop vague par certains. Ce glissement linguistique provient sans doute d'une traduction de l'anglais Graphic Design."

---

### Post by lyceum on 2007-04-30
I just started working on my first "real" website (all others have been school projects) and I am detrmined to just use my Ubuntu box and FOSS programs. I have only had time to build 2 pages thus far, but I think I am off to a good start. I am linking them to show my GIMP button (for Ubuntu LoCo Ohio group) and the site logo. GIMP took a while to get use to, but all and all it is working great. 

[http://whitetreeevolution.com](http://whitetreeevolution.com)

[http://whitetreeevolution.com/ircloginohioloco.html](http://whitetreeevolution.com/ircloginohioloco.html)

Both of these are just a start, but I really think they are good example of what you can do.

---

### Post by bakermiller on 2007-05-02
> I have a question for you. Your use of the terms 'graphism' and 'graphists' are strange to me. As far as I know the proper terms are 'graphics' or 'graphic arts' and 'graphic designers' or 'commercial artists'. Could you explain? Just curious.

Because il est Francais, non?

I dropped windows last week and the whole CS2 suite. I'm looking forward to learning new tools under this OS. GIMP, inkscape (or xara too) and scribus will totally replace photoshop, illustrator and indesign for me. So far, the interface and menus are very different, but many tools look interesting and surprisingly efficient.

i managed to import .ai files into GIMP, no problem, it just opened it-up like i was using photoshop!!!!
i have not noticed anything about photoshop files when imported into GIMP, they are supposed to look bad??
 
you can always export as .PDF if you are afraid of your printers reactions to your files. there is surely a way to do that!!

PS: outlining type is the worst thing to do when printing, postscript is a good thing  you don't want to ruin. Just include or embed your fonts, or export .PDFs.

a plus

---

### Post by Nicu Alecu on 2007-05-06
Well, it seems like there's a lot of us struggling with the same issues: files from clients/designers, old PSD files from Palaeozaic era (to be read as " m$ windows times" - it's only been 2 months since we switched to ubuntu, but it surely seems like ages).
GIMP is good (I can open all our old PSDs and alter them to my liking, we only used PS7 in the "windoze era", no CS or CS2) but so far it takes 2 to 3 times longer to get the same things done; it's the learning curve,I know ...
Xara is really good, though I haven't have time to fully grasp the things it can do, and it's just an addition (a good one, I have to admit) to a web worker's set of tools.
But what I really miss is my good-old Homesite and my dear TopStyle; imho, bluefish or quanta or any other editors or IDEs (be it for linux or windows) don't live up to the standards set by Allaire some many years ago ... too bad Macromedia virtually killed the development of homesite and Adobe put a cross on it's grave. As for Topstyle, I ended up runing the Lite version under wine, until I get the chance to fiddle with CSSed (which, by the way, look like  a very poor cousin of Topstyle).

---

### Post by mech7 on 2007-05-06
> **Nicu Alecu said:**
> 
But what I really miss is my good-old Homesite and my dear TopStyle; imho, bluefish or quanta or any other editors or IDEs (be it for linux or windows) don't live up to the standards set by Allaire some many years ago ... too bad Macromedia virtually killed the development of homesite and Adobe put a cross on it's grave. As for Topstyle, I ended up runing the Lite version under wine, until I get the chance to fiddle with CSSed (which, by the way, look like  a very poor cousin of Topstyle).

Homesite engine is integrated in dreamweaver i think since v7.. Dreamweaver 8 seems to run good on WINE, just put it on code view and you have practically the same or actually better then homesite ;)

Have not tried topsyle yet though as i usually use the css editor in dreamweaver it's enough for my needs thoug topstyle is a bit more powerfull :)

---

### Post by Corey on 2007-05-07
I'm a web designer working under linux. I don't mess with PSDs since I do most the graphics myself with the gimp. Asking for flattened images is probably your best bet. Or perhaps using wine or a dual boot system where you can flatten the FX layers yourself. You'll need some sort of access to windows for testing in IE anyway, although ie4linux is not bad at all. As for code I use gedit. I have tried bluefish and screem but they arn't as stable as I like and I really don't need the extra functionality they offer. I do wish gedit had a more standard form of autocomplete though. Working in linux does have it's advantages. Its great to be able to work on a linux machine when you know your work will be hosted on a linux server. Its easy to run servers and PHP for instance instead of having to constantly upload you code to check if it works. The Gimp isn't quite as powerful as photoshop, but once you get the hang of it there really isn't much you'll miss out on, plus there are some features that photoshop doesn't have like fractal generators and other oddities. Apress has a great book out on the gimp which can get anyone up to speed techincally.  I love working with inkscape too, though the discrepency in features compared to Illustrator is even greater than that of the gimp and photoshop. Agave is a nice little color picker tool that I use quite a bit. My biggest headache under linux is fonts. There is no usable font manager for my massive collection. And there is no support for OpenType fonts that have alternate characters and other advanced features. All a small price to pay though since my OS and software is free. Normally I stress free as in freedom more than as in beer, but considering the prices of adobe's products and upgrades you'll save tons of money.

---

### Post by mech7 on 2007-05-07
> **Corey said:**
> plus there are some features that photoshop doesn't have like fractal generators and other oddities.

There are fractal generators for photoshop as plugin.. not that i ever use them :)

---

