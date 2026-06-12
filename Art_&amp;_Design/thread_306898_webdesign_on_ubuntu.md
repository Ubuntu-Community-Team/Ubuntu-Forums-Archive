---
title: "webdesign on ubuntu ?"
date: 2006-11-25
forum: Art &amp; Design
---

### Post by vr.crawler on 2006-11-25
is there some linux software for webdesign?
something like dreamweaver or so.

---

### Post by wastrel on 2006-11-25
I don't know about dreamweaver but check out nvu for web design.

---

### Post by Tipo on 2006-11-25
Dreamweaver is proprietary software... you won't see it in Ubuntu.

I second the rec for Nvu. Not quite as good as Dreamweaver, but it's a good open-source alternative

---

### Post by commodore on 2006-11-26
Both Dreamweaver and Nvu suck. Learn to code yourself. Usually apps like Dreamweaver and Nvu don't create validating (correct) code.

---

### Post by uuwatti on 2006-11-26
Nvu is no longer in development. It's called kompozer now and and to find where it is scroll down on this page[http://www.ubuntuforums.org/showthread.php?t=293798]("http://www.ubuntuforums.org/showthread.php?t=293798")

---

### Post by smartalecks on 2006-11-26
Aptana is a pretty good alternative to Dreamweaver. It's still in development, but they are close to releasing a very functional version. The current version works fairly well as well, but there are a few bugs.

**Main Website:**
[http://aptana.com/](http://aptana.com/)

**Screencasts:**
[http://www.aptana.tv/](http://www.aptana.tv/)

**Screenshots:**
[http://www.aptana.com/screenshots.html](http://www.aptana.com/screenshots.html)

**Install in Ubuntu via Repos (standalone):**
[http://aptana.com/forums/viewtopic.php?t=520](http://aptana.com/forums/viewtopic.php?t=520)

**Install as an Eclipse Plugin:**
[http://aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration](http://aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration)

You'll need JRE. It's slightly slower than other applications (Java, to be expected) but it packs tons of features and could really be a as good or better (free) alternative to Dreamweaver in the future.
The only thing that is lacking atm is a WYSIWYG interface. It does, however, have a built-in preview (no external browsers :)), and as far as I can tell a WYSIWYG is in the works.

---

### Post by Madpilot on 2006-11-27
Learn to handcode, then use either [Bluefish]("http://bluefish.openoffice.nl/index.html"), [Screem]("http://www.screem.org/") or even just Ubuntu's default text editor, gEdit, to code up HTML & CSS.

You get far cleaner (therefore faster, and easier to modify later) code from doing it yourself with a good editor to help than you would from bashing around with a WYSIWYG editor like Nvu/Dreamweaver/et al.

---

### Post by justinjstark on 2006-11-28
I don't think there is really a reason for WYSIWYG web design applications these days.  Your best options are learn css and code it yourself or, if you're lazy, use something like drupal or joomba which are basically boxed websites with web-based admin controls.  Apply a template or make your own and, bam, there you go.

---

### Post by Rodneyck on 2006-11-28
If you have Dreamweaver, mine works perfectly under Wine (Dreamweaver MX version.)

---

### Post by frup on 2006-11-29
I'm in the learn to code group. I've been doing that way for 8 years since i got fed up with my old homestead account and moved to geocities :P

---

### Post by Tipo on 2006-12-02
Well, the thing is, once you learn to code, programs like Dreamweaver are a *very* valuable resource... Yes, Dreamweaver *does* create bad code when you use it as a _drag and drop_ program.  However, if you know how to code and use Dreamweaver as a text editor, it can be very useful, and reduce your coding time by a lot (i.e. key commands, shortcuts, auto-completion)

---

### Post by feest on 2006-12-03
mozilla composer allowsy you to do basic html with a gui, but not very comaptible with php

---

### Post by DarkN00b on 2006-12-03
Personally, I prefer to hand-code in a WYSIWYG program because I like the control of hand-coding along with instant preview. I suppose I could code in gedit and click Refresh in Firefox when I want to preview.

---

### Post by Rodneyck on 2006-12-03
From a "designer" standpoint, it is important to see visually how the design comes together as you code, thus the importance of a WYSIWYG editor. Especially important if you want to make quick edits, on the fly, design-wise.

Nvu, btw, is no longer supported. The developer is currently working on a new and improved web builder under the name Composer2, I think. Meanwhile, some other guy took the Nvu code and updated it, releasing it as Kompozer or something like that, so this is the the web builder for Linux you should get. It is billed as Nvu with bug fixes and updates.

---

### Post by smartalecks on 2006-12-03
> **DarkN00b said:**
> Personally, I prefer to hand-code in a WYSIWYG program because I like the control of hand-coding along with instant preview. I suppose I could code in gedit and click Refresh in Firefox when I want to preview.

[Aptana]("http://www.aptana.com") is definitely for you :). It doesn't have a WYSIWYG feature, but it does have a very fast in program preview feature (uses the Firefox engine).

---

### Post by vincentvee on 2006-12-04
> **vr.crawler said:**
> is there some linux software for webdesign?
something like dreamweaver or so.

i use mozilla suite, browser, editor all in one kinda setup, not as good as dreamweaver but it will get the job done
also, i don't use the publish feature included in the package, i save the file then upload it with gFTP, which is also in the repo's and in automatix

---

### Post by vincentvee on 2006-12-04
> **Rodneyck said:**
> From a "designer" standpoint, it is important to see visually how the design comes together as you code, thus the importance of a WYSIWYG editor. Especially important if you want to make quick edits, on the fly, design-wise.

Nvu, btw, is no longer supported. The developer is currently working on a new and improved web builder under the name Composer2, I think. Meanwhile, some other guy took the Nvu code and updated it, releasing it as Kompozer or something like that, so this is the the web builder for Linux you should get. It is billed as Nvu with bug fixes and updates.

it is called composer, part of the mozilla suite, or you can get it thru apt-get on its own

---

### Post by finferflu on 2006-12-04
I've been using [Quanta Plus]("http://quanta.kdewebdev.org/") for a while, even if it's a KDE app and goes a bit slower on GNOME. The problem was that used to crash too frequently for my taste, so I switched to something stable enough, Bluefish, even though it's not a WYSIWYG editor. You can check out Quanta Plus again and see if it's been fixed a bit.

---

### Post by vincentvee on 2006-12-04
> **finferflu said:**
> I've been using [Quanta Plus]("http://quanta.kdewebdev.org/") for a while, even if it's a KDE app and goes a bit slower on GNOME. The problem was that used to crash too frequently for my taste, so I switched to something stable enough, Bluefish, even though it's not a WYSIWYG editor. You can check out Quanta Plus again and see if it's been fixed a bit.

is it in synaptic?
hope so, otherwise it will have to wait till morning

---

### Post by finferflu on 2006-12-04
yes, it is, 

```
sudo aptitude install quanta quanta-data
```

Otherwise you can find it in the Add/Remove menu, under the section Programming.

---

### Post by aliyanage on 2006-12-06
Hi,

I've always been doing websites writing code on my own, thats best for me, plus I think you can make websites just as good as if you would use dreamweaver, meaning design wise and a lot better websites when it comes to speed...

maybe you'll need to combine it with some paint programm and some php code but it's worth it.

this is my brothers page: [www.entropy.ch](www.entropy.ch)
check it out all written by hand...

or
[www.banjoparadise.ch](www.banjoparadise.ch)
one that I did all written by hand...

aliyanage

---

### Post by will61 on 2007-01-16
I do webdesign for a living and I can hand code in fact I've probably produced some of my best work by hand 

However at times I have a pretty big workload and it's just not practical to hand code an entire site especially if complex forms are needed along with flash objects and other dynamic features and content.

For high volumes of design work I always use Dreamweaver that saves lots of time However every site I design always requires me to debug code Dreamweaver is far from perfect in that respect but it is very usefull to put a site together quickly but just as with hand coding it still needs fine tuning and debugging.

I still do all my design work from within Windows Xp mainly because I rely heavily on dreamweaver and flash I'm currently looking into installing wine so I can get dreamweaver running on Ubuntu However I'd like to know if anyone has tried running Flash on Ubuntu under Wine?

---

### Post by aliyanage on 2007-01-17
sounds cool, have you got some links for us... to check out few of your website that you've done... I am just interested :-D

this is one I did, just hand written code... [www.banjoparadise.ch](www.banjoparadise.ch)

regards
aliyanage

---

