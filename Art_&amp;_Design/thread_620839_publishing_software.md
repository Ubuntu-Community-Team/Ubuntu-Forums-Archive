---
title: "publishing software"
date: 2007-11-23
forum: Art &amp; Design
---

### Post by Joseph Elliott on 2007-11-23
I'm writing a book and as I draw near completion of the literary side I want to start on the cover, layout, etc.  I have no idea what kind of programs are out there.  Basically I want to create the rough draft of a finished product that i can take to a publisher.  I just downloaded scribus but haven't tried it yet (searched previous posts and found it was often prescribed).

---

### Post by srblopes on 2007-11-24
Scribus is the only open source software in the desktop publishing afair, it´s commercial concorrents are Adobe InDesign and QuarkXpress. If I undestood what you want, Scribus is the perfect choice.

---

### Post by jjalocha on 2007-11-24
Scribus can be a profoundly frustrating experience. There are so many bugs and unpolished edges, so just be warned. But since so many people keep recommending it, you should just try, and see if it fits your need.

If you are aiming at the highest quality typesetting standards, then LaTex (or other TeX tool) is the way to go. And if you are not interested in some complex layout, it can be surprisingly easy to use!

Cover art is probably best created with Inkscape.

Oh, and then there is Apache FOP, which renders XML into PDF or other formats. This is VERY powerful for technical documentation with lots of auto-generated contents...

Hmmm somehow it really depends on what kind of book you're writing, and your needs.

---

### Post by allstar1971 on 2007-11-24
I am in the same boat. I have found Scribus to be a very frustrating experience. It is not close to Adobe InDesign, it is closer to Quark Xpress.

I believe the Linux world needs someone to give another alternative that is somewhat a cross between Xara, Scribus and Open Office.

I used to use InDesign and Serif PagePlus (awesome program) when I was under the evil one's platform.

---

### Post by lode on 2007-11-24
I second the LaTeX notion.

Final layout decisions (fonts, headings, title-page, ...) will probably be in the publisher's hands anyway, so you only have to present him/her a good, nicely readable and usable text (as far as I know).

---

### Post by kayosiii on 2007-11-26
I would go the scribus route if you want to do fancy layouts scribus is a good option... For a longer text without too much happening in terms of layout I think LaTeX will be a better option - and probably LyX a good starting point for LaTeX...

---

### Post by cancer10 on 2010-12-30
I installed scribus but it seems to have some kind of bug.

I created a page, added some text, made it a master page, added a new page, on the new page when I chose "Convert to master page" it did not add the text that was in my master page.

Is it a bug or am I missing something?

---

### Post by JimShortz on 2011-02-13
Scribus does have some unpolished edges, particularly if you try to work directly in text frames instead of using the Story Editor. Unless it's just a couple of words in the frame ALWAYS use the Story editor. That's my top tip!

Since switching to Linux recently I have been doing a lot of stuff at work using Scribus - adverts, brochures, etc. and I have to admit it confused me a lot to start with. You need to follow the correct workflow, then it's lovely!

I made a few video tutorials to go on our school Moodle for introducing Scribus to the High School students that I teach (and the teachers!). I can't give you access to the Moodle so I have also put them up on YouTube. If you are new to Scribus they may prove to be a quick way to "get you going" and avoid some of the frustrations that I went through...

They are at: [http://www.youtube.com/user/HumpyCreature007?blend=8&ob=5](http://www.youtube.com/user/HumpyCreature007?blend=8&ob=5)

I hope they are useful to somebody!

---

### Post by prokoudine on 2011-02-15
> **JimShortz said:**
> Scribus does have some unpolished edges, particularly if you try to work directly in text frames instead of using the Story Editor.

Only if you refer to older Qt3 based version like 1.3.3.13 :) Qt4 based versions are much, much better there.

> **addyj672 said:**
> For publication you can use Coral Draw. It is very famous or you can try some MAC publication software....

Vector graphics app for laying out a book. Right. Very funny.

---

### Post by frisket on 2011-02-19
> **kayosiii said:**
> I would go the scribus route if you want to do fancy layouts scribus is a good option... For a longer text without too much happening in terms of layout I think LaTeX will be a better option - and probably LyX a good starting point for LaTeX...

LyX is fine if your document is almost all text. It can be very difficult if you have tables and figures, or if you want anything other than the standard default layouts.

The OP said "cover and layout" but it's not clear if this means "layout of the cover" or "layout of the contents of the book". LaTeX *can* do cover layouts, but it needs a high level of skill; and you'd still need Inkscape and GIMP for the graphics.

LaTeX excels at the second: typesetting a book. So much so that I wrote a beginners' guide about LaTeX ([http://latex.silmaril.ie/formattinginformation](http://latex.silmaril.ie/formattinginformation)) to help other people get started.

Scribus could have been wonderful, but the interface was forbiddingly difficult, last time I checked.

---

### Post by Dry Lips on 2011-02-23
**prokoudine** wrote:

> Only if you refer to older Qt3 based version like 1.3.3.13 :smile: Qt4 based versions are much, much better there.A quick question: When you refer to the Qt4-versions,
do you mean the experimental "ScribusNG" version?

---

### Post by prokoudine on 2011-02-23
> **Dry Lips said:**
> **prokoudine** wrote:
A quick question: When you refer to the Qt4-versions,
do you mean the experimental "ScribusNG" version?

Short answer: yes.

Long answer: there are three Qt4 based branches:

1. The one that has upcoming new stable 1.4.0 version (currently at rc1 stage). Pretty safe to use. I was referring to this version in the first place.

2. The 1.5.0 branch. Will become v1.5.0 and eventually lead to new stable 1.6.0. Plenty of new features. Not very stable.

3. The OIF branch. Has code developed on OIF's money: modularized properties palette and new opentype shaper for proper support of complex scripts. Very unstable.

Which of them is ScribusNG, I have no foggiest idea, but I'm sure it's not the OIF one :)

---

### Post by Dry Lips on 2011-02-24
> Long answer: there are three Qt4 based branches:

1. The one that has upcoming new stable 1.4.0 version (currently at rc1  stage). Pretty safe to use. I was referring to this version in the first  place.
I've installed ScribusNG just to check it out... 
(From Ubuntu software centre) ScribusNG would be 
version 1.3.8 running Qt version 4.7.0. The old stable 
version (from USC) is version 1.3.3.13svn using Qt 
version 3.3.8b. 
I also checked out scribus.net, and you're right,
they've got newer versions. (for instance ScribusNG
version 1.4svn). I'm not installing that newer ScribusNG
right away, but that is just because I'm a newbie 
with Linux, and I haven't yet gotten used to installing 
stuff in any other way than through the software centre... :| 
Why don't they just offer the most recent versions in the
Software Centre? Perhaps a silly question?

---

