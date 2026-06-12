---
title: "Color managed workflow..."
date: 2010-08-17
forum: Art &amp; Design
---

### Post by ravinderw on 2010-08-17
Hello All,

I'm trying to learn what is involved in setting up a color managed workflow for photography applications.

I was thinking of a flow of something like

Camera -> Rawtherapee -> Gimp -> Printer.
                                                 
                                                  Camera -> Rawtherapee -> Gimp ->Web

I have figured out how to profile the monitor and create an ICC profile using argyllcms.
I have applied that profile to my monitor.

Now my question is do I need to go and apply that profile to each application, or will they just use the monitor settings.

Secondly, I think that if the final product is going to be web I need to tell Gimp to output in sRGB and if it's to be printed for Gimp to use the supplied printer profile.

The question that arises here is after spending seconds, or hours, tweaking the photograph, how do I make sure that the colours displayed on the web are as I want them to be seen?

I apologise for the many questions, but I've spent the last month trying to read about this and actually am more lost than when I started.

Thanks.

Ravinder.

---

### Post by oldsoundguy on 2010-08-17
not sure how Argyle works as have not tried it yet, but most screen managers for color set the parameters up in the screen bios, and not just for one program.  Most hardware driven units are set up that way.  AND be sure to run your printer color chart on PHOTO paper to use for any Mark I eyeball adjustments you may need.

---

### Post by ravinderw on 2010-08-17
> **oldsoundguy said:**
> not sure how Argyle works as have not tried it yet, but most screen managers for color set the parameters up in the screen bios, and not just for one program.  Most hardware driven units are set up that way.  AND be sure to run your printer color chart on PHOTO paper to use for any Mark I eyeball adjustments you may need.

So is it the case that if I set up the color management in Ubuntu and tell gimp to try to use the system color, then that's it gimp is profiled with respect to the screen?

I do note that the colors in gimp and the colors in firefox look slightly different with firefox looking slightly washed out. Is the implication from that if I want to look at photographs I should only look at them in gimp?

Many thanks.

Ravinder.

---

### Post by oldsoundguy on 2010-08-17
If Argyle only works in Gimp, then yes.  To do editing you will have to use Gimp.  

I still have a Windows box for my photography.  To me, personally, Linux of any form and it's added programs are not up to snuff in many categories.  And, because I get updated Adobe FREE on a corporate license for doing services for a graphics shop, why not utilize them? 

Makes the work flow a lot easier and makes color management a snap.

When I see serious Linux discussions occurring on photography boards, maybe THEN I will consider doing a swap.  But most is confined to Windows/Mac and Adobe at present.

---

### Post by graphius on 2010-08-20
> Linux of any form and it's added programs are not up to snuff in many categories
While I agree that many programs lack the polish of a mac, or possibly Photoshop, I would counter that there are a few programs that offer better functionality and output than their commercial counterparts.
Because they cost so much, programs like Photoshop try to be all things to all people. If you move outside the box, and stop trying to replace Photoshop with Gimp (for example) and use a few of the other tools available, you can (at least I can, and I used to teach Photoshop at college level) produce as good, or possibly better images. However the learning curve is steep.
Also, many of the programs in the *nux world are not designed for high volume shooters like wedding or event shooters, or for Joe Amateur who wants wizards and auto settings.

Back on topic: Colour management is still a weakness, and requires a fair bit of knowledge of the underlying principles to work. Argyle et al are working toward a goal of easy calibration, and they are getting very close, but they are not quite as good as Apple.

---

### Post by oldsoundguy on 2010-08-20
> **graphius said:**
> Back on topic: Colour management is still a weakness, and requires a fair bit of knowledge of the underlying principles to work. Argyle et al are working toward a goal of easy calibration, and they are getting very close, but they are not quite as good as Apple.

I use an older Gretag-Macbeth USB Eye-1 plug in "puck" and have done so for several years. It only works in Windows right now. (some attempts have been made to get it to work in Linux, but have not see any program that REALLY works.

Things like this are really specialty items and not really used in mass amounts.  Hard to justify several days of code work just to get something that maybe a couple of hundred people have to get to work in the system. (unless some programmer takes it as a challenge!)

---

