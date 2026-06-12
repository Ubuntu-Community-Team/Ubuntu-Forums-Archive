---
title: "Diference Between Photoshop and gimp?"
date: 2010-12-01
forum: Art &amp; Design
---

### Post by DMKryl on 2010-12-01
After seeing a few posts i began to wonder why people keeps putting gimp outside the frame, what are the professional things that make people stick to photoshop (well aside the floating windows, and the 20 years of photoshop experience)

Diferences so far (well actually lacks)
* Price
* no CMYK, LAB, Pantone and Hexachrome native profile
* color depth is 8-bit at current version 2.6.10.
* Adjustment layers
* _Lock Layers_ they promised it at 2.8
* Layer comps
* Patch tool
* A free transform tool (A merged one, they exist but at separated tools e.g: rotate, scale; )
* Clipping mask layer
* Editable vector supporting layer masks and effects for working only in gimp
* Advanced character settings and writing on curved paths that remain editable also missing but this belong more to a vector program.
* Conversion of font elements (Convert text to path) into shapes with subsequent editing
* Maybe too much to ask but no Content-Aware Scale, quick selection tool, Smart objects

---

### Post by amauk on 2010-12-01
It always used to be support for CMYK
but I believe the Gimp has had CMYK support for a while now

---

### Post by DMKryl on 2010-12-01
searching a little i found that it doesn't have a native CMYK profile but there's a plug in for separating to cmyk, separate+, besides that anything else?

---

### Post by amauk on 2010-12-01
Nothing major that I know of

---

### Post by prokoudine on 2010-12-01
Just google for "photoshop vs. gimp".

Off-top of my head:

- higher precision in terms of bits per color channel, which means not so much loss of useful data during color grading
- transparent access to different color spaces such as LAB, because every color space is good for its own set of scenarios
- adjustment layers, which means being able to edit some changes you did even if you save and close
- actions, because you can quickly record and replay a set of changes to different pictures
- better retouching tools; e.g. GIMP's healing brush starts drawing garbage when you are close to edge of an object, and there is no patch tool

---

### Post by dpny on 2010-12-01
> **prokoudine said:**
> Just google for "photoshop vs. gimp".

Off-top of my head:

- higher precision in terms of bits per color channel, which means not so much loss of useful data during color grading
- transparent access to different color spaces such as LAB, because every color space is good for its own set of scenarios
- adjustment layers, which means being able to edit some changes you did even if you save and close
- actions, because you can quickly record and replay a set of changes to different pictures
- better retouching tools; e.g. GIMP's healing brush starts drawing garbage when you are close to edge of an object, and there is no patch tool

I was about to post something similar, so I will just amplify.

Most of the things missing from the GIMP are things which only matter for professional print, production and pre-press work. If 16/48-bit color, LAB, Pantone and Hexachrome don't mean anything to you, then, for your purposes, there isn't much difference.

---

### Post by Niva on 2010-12-01
As an artist and a user of both platforms the biggest thing which prevents me from using GIMP full time is the brush engine.  Photoshop's brush engine is incredible and completely intuitive to me.  GIMPs suffers multiple setbacks while managing to do some things better albeit different from the way PS handles them.

Adjustment layers and layer grouping are huge features for digital artists that are either missing or badly implemented within GIMP.

---

### Post by oldsoundguy on 2010-12-01
Still think you need a separate program to process camera raw images in order to process them with Gimp, but that may have changed.

But the big difference(s) are Adobe Bridge (which is integrated) and allows seamless integration with Illustrator .. being able to use Light Room for professional photo management .. PLUG INS .. LOTS of plug ins such as a complete filter program from Tiffen that allows some real art work in black and white, for instance.

BUT ... for the point and shoot camera person that just wants to crop and do minor corrections .. Gimp is MUCH MORE than they need (they need a lighter and more easy to use program for Linux .. and that is under development.)

---

### Post by Rodney9 on 2010-12-01
There are hundreds of gimp plug-ins and many photoshop plug-ins will work in gimp
[http://registry.gimp.org/](http://registry.gimp.org/)

---

### Post by DMKryl on 2010-12-02
ok i started to see for myself what things are really missing dpny and prokoudine you're absolutely right gimp max color depth is 8-bit.

*taken from [http://www.tek-tips.com/faqs.cfm?fid=1908](http://www.tek-tips.com/faqs.cfm?fid=1908)

Bit depth defines the number of colours available to each pixel within an image:

**Bit                              Depth Colours Available **
1-bit                               black and white 
2-bit                               4 colours 
4-bit                               16 colours 
8-bit                               256 colours  
8-bit greyscale                     256 shades of grey 
16-bit                              32768 colours 
24-bit                              16.7 million colours 
32-bit                              16.7 million + 256 Levels of transparency

I messed around with a file, save it and closed and gimp maintain my layers with his mode,

LAB, Pantone and Hexachrome i agree the right tool for the work, 

Healing brush needs a little more work but nothing you can't do using brush and clone, 

Group layers announced for version 2.7.1, 

Adjustment layers well yes for a lot of designers big concern, i rather duplicate the file and work on it ;), 

Although photoshop is used by many digital artist i believe and stand my ground that photoshop wasn't made for that, i'd stick for mypaint, krita while y wish painter come to linux, 

Ughhh adobe bridge, i never met a program so useless, take years to open, a total waste of memory the only program that i unselect when i'm installing any cs suite, the program may integrate the whole suite but still i'd prefer to move things manually, in the other hand ia gree with you oldsoundguy plugins are waste time savers, thx for the plug-in page Rodney9

---

### Post by alex.rayu on 2010-12-02
To add to the above. What is missing in GIMP for me as a web designer that is in Photoshop:

1. Layer folders and comps
[B]2. Layer masks
3. Layer effects
4. Editable vector supporting layer masks and effects[/B]
5. Conversion of font elements into shapes with subsequent editing, and of shapes into brushes
6. Smart objects
7. Advanced objects alignment and smart guides
8. Advanced character settings and writing on curved paths that remain editable
9. Slices
10. Advanced optimization for web

I could name more - but these are the biggest ones I guess. The ones I wrote in bold make GIMP unusable for web design for me.

---

### Post by Niva on 2010-12-02
> **DMKryl said:**
> 

Although photoshop is used by many digital artist i believe and stand my ground that photoshop wasn't made for that, i'd stick for mypaint, krita while y wish painter come to linux, 


Just because it wasn't meant for that doesn't mean it's not the best tool for it.  Everything that's useful for photography manipulation applies to digital art.  Actually digital artists probably are more fluent in PS than the vast majority of pro photographers in terms of exploring its features.

---

### Post by umba on 2010-12-02
I've used both Photoshop, Gimp and now recently Pixelmator (mac). Pixelmator wins, hands down. Personally I didn't like GIMP since it crashed a lot, but compared to Photoshop it is a decent and free alternative.

---

### Post by dpny on 2010-12-02
> **Niva said:**
> Just because it wasn't meant for that doesn't mean it's not the best tool for it.  Everything that's useful for photography manipulation applies to digital art.  Actually digital artists probably are more fluent in PS than the vast majority of pro photographers in terms of exploring its features.

Depends on the photographer. I've known some who were Photoshop whizzes, and some who could only do basic stuff.

---

### Post by wolfgangmcq on 2010-12-02
Major difference? Price:

Gimp: $0
Photoshop:  $699

---

### Post by ArunavAm on 2010-12-02
I think it depends upon the hardware too (apart from being a photographer.. lol :D ).. if it's a netbook.. use GIMP.. If it's a biggie machine.. use PHOTOSHOP.. If u are a photographer.. use nothing.. use your camera.. lol :D

---

### Post by DMKryl on 2010-12-02
For the layer folders well like i said before they're announced for the 2.7.1 ver., for the layer comps i never heard of it (everyday you learn something new) but you're right this feature is missing, 

layer mask are in the layer menu>mask>add layer mask, 

layer effects can be added by this plug-in (it has what i use), but they appear in the menu, not double clicking in the mask, [http://registry.gimp.org/node/186](http://registry.gimp.org/node/186),

Editable vector supporting layer masks and effects just for working in gimp, you can add a svg vector as a layer but no edit in gimp you need to use another vector program, 

conversion of font elements into shapes with subsequent editing another missing feature, 

shapes into brushes i don't know if this what you're talking about [http://emptyeasel.com/2008/10/03/gimp-brushes-tutorial-how-to-modify-and-create-brushes-in-gimp/](http://emptyeasel.com/2008/10/03/gimp-brushes-tutorial-how-to-modify-and-create-brushes-in-gimp/)

Smart objects took photoshop to cs2 version to add it

Advanced objects alignment and smart guides, e.g?

Advanced character settings and writing on curved paths that remain editable also missing but this belong more to a vector program.

Slices, missing and i never understand what the tool do

Advanced optimization for web maybe this is what you're looking for [http://registry.gimp.org/node/33](http://registry.gimp.org/node/33)

> Just because it wasn't meant for that doesn't mean it's not the best tool for it. Everything that's useful for photography manipulation applies to digital art. Actually digital artists probably are more fluent in PS than the vast majority of pro photographers in terms of exploring its features.

I stay my ground is not the best, the best is painter, but you're right many digital artist use photoshop and i know a few that are awesome working on the program, but what features are missing in gimp that you could use in photoshop, the only one that i see missing is clipping mask layer

---

### Post by sidzen on 2010-12-02
> **wolfgangmcq said:**
> Major difference? Price:

Gimp: $0
Photoshop:  $699

Hooray, someone finally got it!

Having worked in a GIS shop geocorrecting satellite imagery and making 3-D avi fly-by movies (among other things), I found that reducing 3 bands to 256 colors is quite a resource saver and made things manageable.

BTW, can the human eye really tell the difference beyond 8-bit color?  Just curious.

Lest we forget -- to the rest of the world, outside W Europe and the former Commonwealth nations, America is elitist by definition!  *Gratis* and *Libre* mean more than money and convenience (my own propensities included).

G'day!

---

### Post by DMKryl on 2010-12-02
> **ArunavAm said:**
> I think it depends upon the hardware too (apart from being a photographer.. lol :D ).. if it's a netbook.. use GIMP.. If it's a biggie machine.. use PHOTOSHOP.. If u are a photographer.. use nothing.. use your camera.. lol :D

Where is the like button when you need it? XD, as my digital image teacher said to us once "if you can take the photo (yes he mean take the photo not just press the shutter) avoid searching it on internet because the more time you spend preparing the photo the less time you spend editing it"

---

### Post by earlycj5 on 2010-12-02
> **DMKryl said:**
> Where is the like button when you need it? XD, as my digital image teacher said to us once "if you can take the photo (yes he mean take the photo not just press the shutter) avoid searching it on internet because the more time you spend preparing the photo the less time you spend editing it"

Yep.  Ansel Adams certainly spent a lot of time waiting, and waiting and waiting patiently for just the right moment for the photo, then spent NO time in the darkroom at all.  Sure...

When I see comments against using PS/Gimp in photography it just drives me nuts.  It's a tool, just like any other that use, my camera body, lenses, filters, tripods, etc.

Often I take the photo with edits in mind, it's just part of my workflow.

Reading this thread, I guess I don't know what I'm missing.  I was trained on PS, but adapted to use Gimp and it works fine for this photographer.  Not discounting what people are saying, but seems like if you want to make it work for you, most, not all, people can.

---

### Post by DMKryl on 2010-12-02
> BTW, can the human eye really tell the difference beyond 8-bit color?  Just curious.

Yes we can identify around 10 millions of colors that's something between 16 bits - 24 bits

16-bit 32768 colours 
24-bit 16.7 million colours 

beyond that point anything else is for professional print, production and pre-press work so i really don't know much about it

---

### Post by dpny on 2010-12-02
> **DMKryl said:**
> Yes we can identify around 10 millions of colors that's something between 16 bits - 24 bits

16-bit 32768 colours 
24-bit 16.7 million colours 

beyond that point anything else is for professional print, production and pre-press work so i really don't know much about it

You kind of get the point: this isn't about what the eye can see: it's about me being in control of all my color data.

Any time you begin to retouch or color correct a picture you begin to throw away color data. 16/48-bit color, which you can get from many pro digital cameras and drum scanners, means I start with a much larger amount of color data, so when I start to manipulate it I can have much more control of how the picture looks. I can selectively throw away what I don't need rather than the program deciding what to throw away.

This is especially important because CMYK has a small gamut when compared to RGB, so when I'm working with an image which will be printed, deep color gives me many more options. This becomes especially important when I need to take an image which has problems--too dark, too light, bad color cast, etc.--and make it print well at a large size.

Photoshop is the primary pro tool because it has features built into which are specifically meant for professional retouchers and production/pre-press work. These features don't mean anything to someone using Photoshop for casual use. But, for me, they're indispensable.

---

### Post by prokoudine on 2010-12-02
> **Niva said:**
> As an artist and a user of both platforms the biggest thing which prevents me from using GIMP full time is the brush engine.  Photoshop's brush engine is incredible and completely intuitive to me.

What's so incredible about Photoshop's brush engine apart from dual brush and the new stuff in CS5? Tell me. I'm really curious, because I know all about it, having reverse-engineered it. GIMP's painting dynamics are far more flexible (yes, I'm talking about 2.7, nor 2.6).

> **DMKryl said:**
> Adjustment layers well yes for a lot of designers big concern, i rather duplicate the file and work on it ;), 

Only designers? You never do color grading of photos?

> **alex.rayu said:**
> 1. Layer folders and comps
[B]2. Layer masks
3. Layer effects
4. Editable vector supporting layer masks and effects[/B]
5. Conversion of font elements into shapes with subsequent editing, and of shapes into brushes
6. Smart objects
7. Advanced objects alignment and smart guides
8. Advanced character settings and writing on curved paths that remain editable
9. Slices
10. Advanced optimization for web

Admit it &#8212; you never really used GIMP.

1. Layer group already there in 2.7, go read [here]("http://libregraphicsworld.org/articles.php?article_id=21") (English) or [here]("http://gimp.ru/articles.php?article_id=31") (since you are from Ukraine)
2. Layers masks have been there since forever
3. Layer effects &#8212; missing indeed.
4. Vector layers are partly there, but not exposed in UI. WIll probably have to wait till 2.10 as there is no specification for UI ready.
5. You have Inkscape for such conversion, and creating brushes from selection has been available in GIMP since early 2000s at the very least.
6. Smart objects missing indeed.
7. "Advanced objects alignment" &#8212; care to elaborate?
8. "Advanced character settings" &#8212; already there in 2.7, not the text-on path yet though
9. Install gimp-sharp
10. Install save-for-web plug-in

---

### Post by jcolyn on 2010-12-02
> **ArunavAm said:**
> I think it depends upon the hardware too (apart from being a photographer.. lol :D ).. if it's a netbook.. use GIMP.. If it's a biggie machine.. use PHOTOSHOP.. If u are a photographer.. use nothing.. use your camera.. lol :D

As a photographer myself most of my editing is done in camera while composing and adjusting exposure etc.

I use Gimp for touch up or if I want to get creative. I will also do editing when needed.

> **sidzen said:**
> 
BTW, can the human eye really tell the difference beyond 8-bit color?  Just curious.

G'day!

I don't know about the human eye but the printer can. 8 bit sRBG is ideal for chemical processed photo papers while 8 bit RGB works for output to an ink jet printer.

16 bit color is a waste for out put to either in fact most processing businesses will reject a 16 bit color file and let you know you need to upload a 8 bit file.

Where I work we use chemical processed photo paper and will only accept 8 bit sRGB files.

> **earlycj5 said:**
> 
When I see comments against using PS/Gimp in photography it just drives  me nuts.  It's a tool, just like any other that use, my camera body,  lenses, filters, tripods, etc.

Often I take the photo with edits in mind, it's just part of my workflow.

I agree. No matter what image editing program you use it is nothing more than a tool. I use PhotoShop at work but prefer Gimp and DigiKam at home. For me any one of them will work.

I prefer to do as little editing as possible so I try to get exposure, color, etc right in camera but will edit when it suits what I want the final image to look like.

---

### Post by Tenzy on 2010-12-03
As someone who uses GIMP mainly for amateur art work, fun edits (i.e stick an ear on someone's forehead), and webs graphics and not photography or painting, these are the things I'd like to see in GIMP that are already in Photoshop.

- **Proper layer effect**.
I've seen this requested so many times and have no idea why this isn't a priority. I use the layerfx script but you can't beat the nice dialog box with preview in Photoshop. 
- **A free transform tool**.
When you need to rotate and resize something, you first need to rotate, then resize, then maybe rotate a bit more etc etc. The end result is blurry because of the many times you applied a change. It's a real challenge to get it to look nice. It can be done, but you have to undo and start again a lot. 
In PS, rotate and resize is in one tool and you only have the apply the changes ones, when you are happy with the result.
-**Layer Groups**.
Luckily they will be there in 2.8 :)
-**A much better text tool.**
Hopefully will be there in 2.8. It will be better, but will it be much better? Fingers crossed. 

The rest is doesn't really matter to me (yet?). If you know GIMP well enough, there's usually a solution.

---

### Post by DMKryl on 2010-12-03
> Only designers? You never do color grading of photos?
Color grading isn't in films? idk the term or maybe i know it by another name, could you be more especific? (i googled it but it always pointed to movies)

> - **Proper layer effect**.
I've seen this requested so many times and have no idea why this isn't a priority. I use the layerfx script but you can't beat the nice dialog box with preview in Photoshop. 

There's some layer effect missing?

> If you know GIMP well enough, there's usually a solution
i'd change some words in that sentence "If you know what are you going to do, there's always a solution" ;)

---

### Post by prokoudine on 2010-12-04
> **Tenzy said:**
> 
- **A free transform tool**.

It's in the plans. There is a [functional specification]("http://gui.gimp.org/index.php/Transformation_tool_specification") for that tool even.

> **Tenzy said:**
> -**A much better text tool.**
Hopefully will be there in 2.8. It will be better, but will it be much better? Fingers crossed. 

It's already much better. No need to cross your fingers. Just install and see for yourself :)

> **DMKryl said:**
> Color grading isn't in films? idk the term or maybe i know it by another name, could you be more especific? (i googled it but it always pointed to movies)

Color grading, color adjustment, color correction — different words, same meaning. Being able to redo curves or levels on a layer makes life a lot easier.

---

### Post by I'mGeorge on 2010-12-04
I don't know if the differences count much, regarding the fact that PhotoShop it's quite expensive, and it's one of those programs you won't buy just for fun while Gimp doesn't cost a dime, and we have to agree it does quite a lot.

---

### Post by DMKryl on 2010-12-04
> I don't know if the differences count much, regarding the fact that PhotoShop it's quite expensive, and it's one of those programs you won't buy just for fun while Gimp doesn't cost a dime, and we have to agree it does quite a lot.
Yes they count a lot, i didn't start the thread for knowing which program is better because after all they're just tools, the main issue is time, when you know your way into a program you can do a lot of stuff and really quick, and that's extremely important when you work and when you came from another OS (whatever was the reason, mine was a disgust with microsoft line service[it may sound stupid, but when you get hanged up while you're asking a question to the "service guy" that counts and a lot "A business absolutely devoted to service will have only one worry about profits. They will be embarrassingly large. - Henry Ford"]) and can't find a program you just can't give up and go back for a single program, more when the tools exist in the OS, i started this thread to know which things i wouldn't have and start looking around for another way to do it

---

### Post by I'mGeorge on 2010-12-05
Gimp it's a great software, if you have a lot of time on your hands, and it's pretty much based on the keep it simple philosophy. With the proper amount of time, talent and imagination you can do anything in gimp, but this ain't really a good thing when you must use it for real work, when you actually have to work with it, and you have to do a lot of photo editing using it. 

It's very powerful, easy to understand and it's quite a wonder it's only open source. I use it a lot under linux for editing my personal photos, small projects and so on, when I like to have total control on my photo editing, so the picture enhancements would bare my signature instead the software's one, which can only be achieved with a basic software like Gimp.

But when you have to do massive photo editing, in a short amount of time, working on a large scale projects than I'm afraid Gimp won't really cut it. For that some other users recommended me, here on this forums, LightZone and Bibble. I have to say I've didn't had a lot of time to check out their trial versions, but they seam quite alright, so if you want something that could match Photoshop in linux you should give them a look also.

Cheers.

---

### Post by alaukikyo on 2010-12-05
> **I'mGeorge said:**
> which can only be achieved with a basic software like Gimp.


Gimp by no means s a basic software

> **I'mGeorge said:**
> 
But when you have to do massive photo editing, in a short amount of time, working on a large scale projects than I'm afraid Gimp won't really cut it. For that some other users recommended me, here on this forums, LightZone and Bibble. I have to say I've didn't had a lot of time to check out their trial versions,
Cheers.

lightzone and bibble are not alternatives to  photoshop or gimp

---

### Post by I'mGeorge on 2010-12-05
> **alaukikyo said:**
> Gimp by no means s a basic software

I'm not implying it's like MS Paint, but it is basic compared to a professional image editor. It's not about that gimp doesn't have a lot of handy tools, but the way the tools behave, how they actually work it's a basic one.

> **alaukikyo said:**
> 
lightzone and bibble are not alternatives to  photoshop or gimp



I never had the time to really give them a test or work with them so I'll take your word for granted.

---

### Post by DMKryl on 2010-12-05
> **I'mGeorge said:**
>  but the way the tools behave, how they actually work it's a basic one.

Could you be a more specific,which tools and why?

---

### Post by Chronon on 2010-12-06
> **DMKryl said:**
> Yes we can identify around 10 millions of colors that's something between 16 bits - 24 bits

16-bit 32768 colours 
24-bit 16.7 million colours 

beyond that point anything else is for professional print, production and pre-press work so i really don't know much about it

But this 24-bits is total.  8 bits per channel gets you that.  8 bits = 256 output levels for each color.  The total number of combinations is (2^8)^3 = 2^24 = 16 777 216.  So if we can really identify about 10 million colors then 8-bits per channel already surpasses our ability to discriminate between arbitrary colors.

---

### Post by dpny on 2010-12-06
> **Chronon said:**
> But this 24-bits is total.  8 bits per channel gets you that.  8 bits = 256 output levels for each color.  The total number of combinations is (2^8)^3 = 2^24 = 16 777 216.  So if we can really identify about 10 million colors then 8-bits per channel already surpasses our ability to discriminate between arbitrary colors.

See above about retouching and deep color.

---

### Post by Chronon on 2010-12-06
Sure.  I can understand that you may want more bits for processing.  I was mostly clarifying that 24-bits is the same as 8-bits per channel.

---

### Post by Niva on 2010-12-06
> **prokoudine said:**
> What's so incredible about Photoshop's brush engine apart from dual brush and the new stuff in CS5? Tell me. I'm really curious, because I know all about it, having reverse-engineered it. GIMP's painting dynamics are far more flexible (yes, I'm talking about 2.7, nor 2.6).



Only designers? You never do color grading of photos?



Admit it — you never really used GIMP.

1. Layer group already there in 2.7, go read [here]("http://libregraphicsworld.org/articles.php?article_id=21") (English) or [here]("http://gimp.ru/articles.php?article_id=31") (since you are from Ukraine)
2. Layers masks have been there since forever
3. Layer effects — missing indeed.
4. Vector layers are partly there, but not exposed in UI. WIll probably have to wait till 2.10 as there is no specification for UI ready.
5. You have Inkscape for such conversion, and creating brushes from selection has been available in GIMP since early 2000s at the very least.
6. Smart objects missing indeed.
7. "Advanced objects alignment" — care to elaborate?
8. "Advanced character settings" — already there in 2.7, not the text-on path yet though
9. Install gimp-sharp
10. Install save-for-web plug-in

Hello there, first off I'd like to say that you sound internet angry and that you should perhaps calm down a bit.

I've never used 2.7 and I'm sure most other people posting here haven't either.  It's not part of the software available by default in any of the linux distros I've tried.  My understanding is that it's the alpha/beta branch of GIMP and that it's not stable now.  If what you're saying is true that's great.  I'll be glad to see GIMP improve and advance upon PS.  Problem is that it generally lags behind, years behind.  

At some point in the near future I'll hope to see 2.8 released and stable with all the great features you've said are there.  If I can get away from Photoshop it will make me happy.

Your post was useful and gave some good info, too bad for the dramatics.

---

### Post by Tenzy on 2010-12-06
> **DMKryl said:**
> 


There's some layer effect missing?



Sorry, should have said layer effects. And yes, just compare the script to the function in Photoshop.  



About the text tool:
> **prokoudine said:**
> 

It's already much better. No need to cross your fingers. Just install and see for yourself :smile:



I'm currently on windows :sad: on an old laptop where there's no room to double boot and can't get  linux to play nice with the hardware either, plus I need some windows  programs so I'm stuck with it for now. The latest windows installer is  2.7.1 but the text tool keeps crashing on me. So I'm keeping my fingers  crossed until 2.8 comes out, or I'll get a new computer, whichever comes  first. :wink:

---

### Post by I'mGeorge on 2010-12-06
> **DMKryl said:**
> Could you be a more specific,which tools and why?

They both do mostly the same things but photoshop just does it better, for now.

[http://everything2.com/title/Gimp+is+not+superior+to+Photoshop](http://everything2.com/title/Gimp+is+not+superior+to+Photoshop)

[http://meetthegimp.org/is-gimp-better-than-photoshop/](http://meetthegimp.org/is-gimp-better-than-photoshop/)

Do the following test to convince yourself. Get an image, or some photo of yours that should be as colored as it can be. Make a list of at least 10 tools common to photoshop and gimp, tools that you could use to enhance the image or even for some artistic effects.

Look carefully at the image and think what should be the right values to use (for example +10% contrast, -5% saturation, +12% more on the green channel and so on) to enhance your image, so after you apply the changes your image would still look normal even if you considered using some artistic effects (don't think of doing something exaggerated as a test, think at something that would make your image look better without radically modifying it, so you could still use the original image as a witness). After you thought at those values use them on the similar tools from Gimp and Photoshop.

**The test shouldn't be done in the following manner: **
You shouldn't load the image into Gimp or vice versa, so you would enhance it this way and after that put the same values into the other program 'cause it wouldn't be fair regarding the last program. Even if they mostly do the same things they deal with certain aspects in different ways, using different algorithms and so on.

It doesn't really matters how Gimp relates to Photoshop but what matters it's how they both relate to you. So even if you don't have a lot of experience in dealing with these kinda software, look carefully at the original image, and just think of what should be the right values and common tools that should be used for both Gimp and Photoshop to enhance the chosen image.
[B]----------------------------------------------------------------
[/B]

This being said as far as I can think you will end up with the following results:

a) the case where both resulting images look bad, even if you thought really hard of how you could enhance it without radically modify it. I've already specified why this aspect matters so much. (the case of a less experienced or less involved user)
   **1.Both images look bad by an overall feeling of exaggeration(too intense colors, excessive brightness and/or contrast, artistic effects that corrupts the image too much etc.). In this case the program that did the most damage, so the resulting image looks worst, wins.** (think at it this way: Let's say you're cutting yourself from being careless while using a knife to cut some bread. If you're using a sharper knife it would do much more damage than a knife with a used blade. In the same manner a more powerful program would actually do more damage to the image if it's not handled properly) 
    **2.Both images look bad by an overall feeling of less than it should be (greyish colors, an existing feeling of desaturation, everything looks pale and lifeless). In this case the program that made the less damage, so the resulting image looks prettier wins.** A more powerful program if you've underestimated the right values will bring you closer to the desired results than a weaker one.
 
  b)**3.The case where both images look good (the case of the experienced ore more involved user) In this case obviously the program that made the image look better wins.**

  c)**4.(rare/almost impossible but theoretically still possible)The case where a resulting image looks good while the other one looks bad. In this case the results should be considered inconclusive.**
-----------------------------------------------------------------

**The test should be performed in the following manner:**

- if you've only done the test a single time it has no meaning, it doesn't says nothing whatsoever. 
- start as being actually less involved (even if you have a lot of experience) Just open both programs choose the image and the right common features and give the values thinking at the fact that those values you've used shouldn't mess the image too much.
- the test has a meaning if it's performed so many times that in the end you would have at least 5 results from the 1, 2 and 3 cases. If you wanna perform further tests choose an uneven number.
- as you perform further tests, try to guess the right values so the images would look better in both programs, having the previous results as a reference, therefore becoming more involved, until, as I've already specified, you will end up having at least five conclusive results.
- the final result it's an overall comparison between the results obtained by doing the tests. Choosing an uneven number of tests you would surely end up having a winer.

Because we have to consider the fact that humans have different individual perceptions, the test it's only conclusive for you, and ONLY FOR YOU. 

To honestly decide if Gimp it's better than Photoshop or vice versa you should add a poll to this thread so others that would perform the test (assuming that they are sincere with their results) or any other test you might suggest, could vote who's better. When you will have at lest 100 votes you can say, hey this one's better than the other.
-----------------------------------------------------------------

Now as far as I can tell in a few words this it's how it goes
- regarding the number of existing tools both programs are even. The tools that photoshop has and gimp doesn't or the other way around are meaningless, and you would probably only use them rarely.
- regarding the professionalism/quality photoshop has a fair advantage over gimp, Not a big one but still a fair one.
- regarding the price gimp has a huge advantage over photoshop (a decent legal copy of photoshop costs thousands of euros, I won't say more so some would think I'm advertising for photoshop around here). So in this case gimp doesn't only have a fair advantage but a huge obvious one.

Overall if you do the quality/price rapport Gimp wins by the distance. Still if you need a program to actually do some serious work with, and money are not an issue for you I would recommend buying photoshop but it doesn't worths the money if you only need something for your own personal photos, small projects or fooling around with the effects to create individual artistic images. 

Sorry for my bad english
Cheers

---

### Post by prokoudine on 2010-12-06
> **Tenzy said:**
> The latest windows installer is  2.7.1 but the text tool keeps crashing on me.

Ah, this can be worked around. Remove 45th line from C:\Program Files\GIMP 2.7\share\themes\MS-Windows\gtk-2.0\gtkrc that mentions "wimp" engine. Admittedly you will get not a very native looking GIMP.

---

### Post by prokoudine on 2010-12-06
> **Niva said:**
> Hello there, first off I'd like to say that you sound internet angry and that you should perhaps calm down a bit.

Oh, I'm so internet angry that I might go as far as insist in hearing more about advanced alighnment that you mentioned. Answering a question asked would be most polite from you. If you managed to not discover layer masks, maybe you also missed Alignment tool? :)


> **alaukikyo said:**
> lightzone and bibble are not alternatives to  photoshop or gimp

It very much depends on what you do. E.g. with localized editing they cover quite a lot of what photographers do.

---

### Post by DMKryl on 2010-12-06
> **I'mGeorge said:**
> 
**The test shouldn't be done in the following manner: **
You shouldn't load the image into Gimp or vice versa, so you would enhance it this way and after that put the same values into the other program 'cause it wouldn't be fair regarding the last program. Even if they mostly do the same things they deal with certain aspects in different ways, using different algorithms and so on

I didn't understand, Do i should made the same test at the same time?

> Now as far as I can tell in a few words this it's how it goes
1- regarding the number of existing tools both programs are even. The tools that photoshop has and gimp doesn't or the other way around are meaningless, and you would probably only use them rarely.
2- regarding the professionalism/quality photoshop has a fair advantage over gimp, Not a big one but still a fair one.
3- regarding the price gimp has a huge advantage over photoshop (a decent legal copy of photoshop costs thousands of euros, I won't say more so some would think I'm advertising for photoshop around here). So in this case gimp doesn't only have a fair advantage but a huge obvious one.
4-Overall if you do the quality/price rapport Gimp wins by the distance. Still if you need a program to actually do some serious work with, and money are not an issue for you I would recommend buying photoshop but it doesn't worths the money if you only need something for your own personal photos, small projects or fooling around with the effects to create individual artistic images. 


Sorry i made a few changes in the quote to made a reply
1- That's true but in that few times you use them are when they more needed, so it's better know which one aren't there for avoid waste time and of course money (electric fee mainly).
2- There just tools, Photoshop will always have a head-on (small or large) because they invest a lot of money into it and have six years ahead gimp.
4- Sometimes i believe photoshop is overpriced, most of all for people who doesn't gain big incomes, (a lot of factors, market, freewhoresnoob-put your profession here- who gift the work for get money for a beer weekend, bills - just buy the original copy photoshop here where i live is almost a little more than 3 times the minimun wage), but if you really need to work with it well try to get the original copy, 

So gimp isn't made for serious work (I'm on a little vacation so i haven't made the experience in work with GIMP)?, because that could be a huge difference, if the program it's just for the lulz then it's a must unnistall

---

### Post by earlycj5 on 2010-12-06
> **prokoudine said:**
> 
It very much depends on what you do. E.g. with localized editing they cover quite a lot of what photographers do.

Indeed, I've used Bibble's trial before.  The localized editing and layers in Bibble cover the majority of what I do if I need Gimp for my photography.

Everyone has a different workflow, I'm drifting more toward Darktable and Bibble and away from Gimp for most photos.

---

### Post by Tenzy on 2010-12-06
> **prokoudine said:**
> Ah, this can be worked around. Remove 45th line from C:\Program Files\GIMP 2.7\share\themes\MS-Windows\gtk-2.0\gtkrc that mentions "wimp" engine. Admittedly you will get not a very native looking GIMP.

Thanks for the tip. Will definitely try that! :D

As for the test George set. I myself approach things differently. I did several tests by setting up a goal of what I want the image to look like. Then try to achieve that goal in both programs and see what went easier and faster and how good the outcome is. 

I found that mostly GIMP and Photoshop score alike. But PS has the edge for having more tools which will is helpful if you know the program well to speed up your work flow. (I also found that ironically most people (not all) shouting that PS is better and GIMP stinks, don't know PS well enough to make use of all the extras.)

If I do the same tests with GIMP versus Paint.net or online editors I often find that I can't get a good enough outcome from the other editors with the tools available to me.

After these tests I decided to stick with GIMP.

---

### Post by Niva on 2010-12-06
> **prokoudine said:**
> Oh, I'm so internet angry that I might go as far as insist in hearing more about advanced alighnment that you mentioned. Answering a question asked would be most polite from you. If you managed to not discover layer masks, maybe you also missed Alignment tool? :)

You must be confusing me with someone else in this thread, I've never talked about alignment in this discussion and it's generally not something I use except in very rare instances.  Precise alignment is never an issue for any of the work I do with either PS or GIMP though.  

Internet tone can be easily confused, you just internet-sound angry to me over this discussion. Peace :)

---

### Post by I'mGeorge on 2010-12-07
> **DMKryl said:**
> I didn't understand, Do i should made the same test at the same time?

The idea is you have to think at what the values for both photohop and the gimp should be, before doing the actual editing on the image.

> **DMKryl said:**
> 
So gimp isn't made for serious work (I'm on a little vacation so i haven't made the experience in work with GIMP)?, because that could be a huge difference, if the program it's just for the lulz then it's a must unnistall

About serious work I've meant if you have to use the programs for actual work. It's not that the GIMP it's a joke or anything like this. Any program, open source or retail will always have it's pros and cons. If anybody finds the perfect piece of software please give me a call :-).

My personal advice would be that if at your work you have to use Photoshop, because the institution you work for (or the ones you work in collaboration with) bought it than fine, get used to it 'cause PS it's still the best on the market in what it does. For your personal use, if you're orientated on photography, don't spend your money on photoshop, save them to buy a really good camera and lens, and learn everything that has to be known about your gadgets, 'cause there's no piece of software in this entire world that could make a good photographer out of you, and just use the GIMP when you need a software for image editing, or if you wanna make something really artistic, it's more than good enough.

---

### Post by prokoudine on 2010-12-07
> **Niva said:**
> You must be confusing me with someone else in this thread, I've never talked about alignment in this discussion


Ah, right. It's because you replied instead of a different person. Apologies.

---

### Post by dpny on 2010-12-07
> **andrew_mehra said:**
> Essentially both are Image Manipulation Softwares.- Currently a bit less perfect for high quality commercial printing(No CMYK, 8bitRGB)

That's not 'a bit less perfect;. That's close to 'completely unusable.' No access to Pantone/Hexachrome makes it completely useless.

---

### Post by SeijiSensei on 2010-12-07
> **dpny said:**
> That's not 'a bit less perfect;. That's close to 'completely unusable.' No access to Pantone/Hexachrome makes it completely useless.

I presume you're speaking here about commercial settings.  Many ordinary users like me are playing with photos or video frames to post on the web where Pantone® colors don't matter.

---

### Post by DMKryl on 2010-12-07
I have been looking around for plug-ins and stuff for gimp, this program has a lot of it, i feel like in "pimp my gimp", doing this i have found a add-on who gives a little more flexibility for painting (i've trying mypaint but the program still lack of something maybe are those annoying floating window BTW is one of the thigs i dislike in painter) something called gimp paint studio.
[http://code.google.com/p/gps-gimp-paint-studio/downloads/list](http://code.google.com/p/gps-gimp-paint-studio/downloads/list), i will give a try this week

Something off-topic for image editing one of my friends told me of two programs for image edit, darktable (reminds me lightroom) and cinepaint (supports 16-32 color depth, but i haven't tried yet) the reason i bring this programs is because through the thread i notice that people who work manipulating images stay away for gimp, maybe another program might fill the hole that linux has in this area.

---

### Post by dpny on 2010-12-08
> **SeijiSensei said:**
> I presume you're speaking here about commercial settings.  Many ordinary users like me are playing with photos or video frames to post on the web where Pantone® colors don't matter.

The post to which I replied specifically said "commercial", so, yes. Both Photoshop and the GIMP are overkill for playing around with photos.

---

