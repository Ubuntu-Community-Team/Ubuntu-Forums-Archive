---
title: "GIMP - Where It Fails..."
date: 2008-05-13
forum: Art &amp; Design
---

### Post by Xfcn on 2008-05-13
Okay, I've been browsing the forums for awhile, and I've noticed that a lot of people say that GIMP falls short of needed work for professional photographers and a few other mediums. I'd like to see some specifics, here, as I only tend to encounter vague generalities.

I in no way shape or form represent or have the attention of the GIMP development team, but I am always curious to see what can be improved.

So, let's get specific here: where does GIMP fail you, and (if applicable) why?

---

### Post by days_of_ruin on 2008-05-13
It doesn't fail me...except I like inkscapes user interface better.
If that was an option it would be sweet.

---

### Post by ajgreeny on 2008-05-13
I think for professional photographers who send items to commercial printing firms, GIMP does not output the appropriate colour profiling, or something of that kind.  For most, if not all amateur and casual users, it is more than adequate, with most of us probably using only a small percentage of its capabilities.  I think it is the best, though I did take a while to get used to the unusual multi-window interface and menu set up.  Once you've done that it is soooo powerful!

---

### Post by Merk42 on 2008-05-13
> **days_of_ruin said:**
> It doesn't fail me...except I like inkscapes user interface better.
If that was an option it would be sweet.
How would that work? Inkscape is a vector application and GIMP is a raster one.

> **ajgreeny said:**
> I think for professional photographers who send items to commercial printing firms, GIMP does not output the appropriate colour profiling, or something of that kind

That would be CMYK, GIMP only does RGB.  That has always been a major complaint.  Some other things where alternatives are better such as non-destructive editing (which I believe it set to be in a future version of GIMP)

---

### Post by Xfcn on 2008-05-13
Interesting stuff so far.

**@days_of_ruin**
I'm curious to know how Inkscape could possibly influence the GIMP in interface, except maybe for an all-in-one resizable window like Inkscape has. Is that what you mean?

---

### Post by peitschie on 2008-05-13
For me GIMP has some major issues dealing with very large pictures.  On my computer it appears to have a limit of 3Gb for memory for the Tile cache size.  I have one or two art pieces that are ridiculous sizes & values (1200dpi and reasonably large) that in Photoshop takes up 10Gb of swap.  This picture fails epically under GIMP.  I can't open it.

Another one I have is a 400Mb tiff file (based of the 1200dpi image) which opens okay, except I can't actually do anything to the image.  That is, if I change the colours and then try and save the changes, the tiff writer fails claiming its out of memory.

These are the primary issues I have with GIMP.

Having said that, for anything reasonably sized (e.g, less than 50-60mb for the picture file), I use GIMP without any hassles.  Oh, I have 2Gb of ram and about 1Tb of free space just for reference sake.

---

### Post by Xfcn on 2008-05-13
> **peitschie said:**
> For me GIMP has some major issues dealing with very large pictures.  On my computer it appears to have a limit of 3Gb for memory for the Tile cache size.  I have one or two art pieces that are ridiculous sizes & values (1200dpi and reasonably large) that in Photoshop takes up 10Gb of swap.  This picture fails epically under GIMP.  I can't open it.

Another one I have is a 400Mb tiff file (based of the 1200dpi image) which opens okay, except I can't actually do anything to the image.  That is, if I change the colours and then try and save the changes, the tiff writer fails claiming its out of memory.

These are the primary issues I have with GIMP.

Having said that, for anything reasonably sized (e.g, less than 50-60mb for the picture file), I use GIMP without any hassles.  Oh, I have 2Gb of ram and about 1Tb of free space just for reference sake.

I didn't know it maxed out at 3 GB... that would be a bit of a short-coming in pro design.

---

### Post by peitschie on 2008-05-13
I'm actually a little intruiged as to where that limit actually comes from.  I couldn't find any documentation justifying the limit anywhere...

I found this link about the Tile Cache... but again.  It makes no assertions or even hints that this 3Gb limit exists: [http://www.gimp.org/unix/howtos/tile_cache.html](http://www.gimp.org/unix/howtos/tile_cache.html)

---

### Post by Xfcn on 2008-05-13
I'm curious as well, as I've only got 1GB of RAM, so I know it's not a function of the RAM available on the computer.

---

### Post by jedimasterk on 2008-05-13
> **Xfcn said:**
> Okay, I've been browsing the forums for awhile, and I've noticed that a lot of people say that GIMP falls short of needed work for professional photographers and a few other mediums. I'd like to see some specifics, here, as I only tend to encounter vague generalities.

I in no way shape or form represent or have the attention of the GIMP development team, but I am always curious to see what can be improved.

So, let's get specific here: where does GIMP fail you, and (if applicable) why?

Let me see
Full 16/32 bit support
User interface way below todays standards
Plugins/Actions
Printing
Addons
Better marketing (when was the last time you read about Gimp in any Professional Photography magazine like ProPhoto)
Has Gimp innovated on anything. Is their anything that Gimp does that Photoshop doesn't.

You also need to ask why the pros use Photoshop. What highend capabilities does it have that the competition doesn't. Check out Lightroom. The majority of professionals are beginning to use that more than Photoshop for organizing thousands of photos. And then Photoshop mainly for enhanced editing. Look at all the addons that can be purchased for Photoshop. Just read a good Photography magazine and you will see.

---

### Post by jedimasterk on 2008-05-13
From ZDNet:

"If you use Photoshop to create artwork for print, then you can forget about replacing it with GIMP for now, as GIMP supports only RGB colour. CMYK support is due to be added, but for now it's not available. If you’re sending artwork or images off to repro, they’re going to want everything in CMYK mode; and if you want to see on-screen how things will look on paper, you’ll need a CMYK preview mode. Furthermore, Pantone colour requires licensing and is therefore unlikely to be included in a free software package, so there’s no industry-standard spot colour capability.

The lack of CMYK therefore makes GIMP unsuitable for use where you’re producing professional work for print. It’s still absolutely fine for printing on your inkjet at home or at a kiosk, as these printers use RGB drivers anyway. Lab colour is also missing from GIMP, leaving you with only device-dependent RGB to work with, which brings us on to the next missing feature.

No colour management
Accurate colour reproduction is critical for imaging professionals, and Photoshop takes full advantage of the colour management support available in Windows and Mac OS X.

Full support for ICC and ColorSync profiles means that you can guarantee consistent colour from one PC to the next. This means you can create accurate — or at least repeatable — soft proofs, predicting with some degree of certainty what colours will end up in print or whatever your final delivery medium might be.

As standard, the GIMP has no support for colour management, although attempts have been made to incorporate it via plugins. The good news is that the forthcoming version 2.4 release of GIMP will incorporate native support for colour management. Current releases of CinePaint also support colour management on Linux.

Colour management is something no-one wants to have to worry about, and much work has gone into making it happen mostly behind the scenes in Windows Vista. Unfortunately, when it’s not happening at all, getting your photos to look right can result in you attempting all sorts of strange adjustments to compensate for your poor monitor, or the fact that you’ve loaded a photo from a camera set to Adobe RGB mode."

---

### Post by jedimasterk on 2008-05-13
Another reply to a similar post on another website.

--Adobe Bridge browser
--Actions & Batch Processing
--Adjustment Layers (someone earlier mentioned GIMP doesn't have these, which instantly makes it useless to me. I LIVE in adjustment layers).
--Layer Masks (I think GIMP has these)
--Export as layeres PSD. (I need to import PSDs into many other applications -- like "After Effects")
--Slices for the web
--Rollovers via Imageready
--Non-square pixel support for video
--Unsharp Mask or Smart Sharpen
--Liquify filter
--Layer Sets
--Clipping Groups
--Layer Effects
--Curves
--Blend Modes (Multiply, Overlay, etc.)
--Brushes that work with Wacom Tablets

---

### Post by Xfcn on 2008-05-13
The last post I'll actually respond in kind to, that which I have any clue about:

Actions & Batch Processing is accomplished via scripting, I believe. I could be wrong.

Adjustment Layers aren't available, no. I believe that same person also mentions that GIMP is taking an alternate (and they believe more effective) route.

Layer Masks -- Actually, I think it does have these.

Export as Layered PSD -- As far as I know it can do this, too...

Rollover via ImageReady -- ImageReady is an Adobe product. Right now the GIMP team does not have an ImageReady-competeing product, so expecting them to conform to that application might be a tad unrealistic. Or it might be entirely realistic. That's for the GIMP team to decide.

Blend Modes -- Uh... every layer has a blend mode... or it WOULD be useless... Or are you talking about something else?

Brushes -- My Wacom works fine with all the brushes, and several I've brought in from other places. What's the problem you're having?

---

### Post by jedimasterk on 2008-05-13
My last two posts were from other sources. Also I may add as well. No magazine articles in photography magazines with tutorials, or learning material apart from web on Gimp. Go into a local bookstore and you will find literally allot of learning material on Photoshop, and even Paintshop Pro. Your lucky to find a single book on the Gimp. Even thogh Amazon does have a selection.

---

### Post by Xfcn on 2008-05-14
I see those as failure of community, not of the application, myself.

---

### Post by Half-Left on 2008-05-14
> **jedimasterk said:**
> Another reply to a similar post on another website.

--Adobe Bridge browser
--Actions & Batch Processing
--Adjustment Layers (someone earlier mentioned GIMP doesn't have these, which instantly makes it useless to me. I LIVE in adjustment layers).
--Layer Masks (I think GIMP has these)
--Export as layeres PSD. (I need to import PSDs into many other applications -- like "After Effects")
--Slices for the web
--Rollovers via Imageready
--Non-square pixel support for video
--Unsharp Mask or Smart Sharpen
--Liquify filter
--Layer Sets
--Clipping Groups
--Layer Effects
--Curves
--Blend Modes (Multiply, Overlay, etc.)
--Brushes that work with Wacom Tablets

GIMP 2.4 has, 

1. Liquefy type filter called iWarp which shows in real time.

2. GIMP is not a web editor but has optimizations for web images.

3. GIMP has Curves and Blend modes.

4. GIMP supports PSD, export and import.

5. GIMP does Layer mask.

6. As Far as I know GIMP works with Wacom Tablets and as I remember in Photoshop you have to set the right brush for them anyway.

But who cares about professionals, most of them would still use Photoshop regardless.

---

### Post by jedimasterk on 2008-05-14
> **Half-Left said:**
> GIMP 2.4 has, 

1. Liquefy type filter called iWarp which shows in real time.

2. GIMP is not a web editor but has optimizations for web images.

3. GIMP has Curves and Blend modes.

4. GIMP supports PSD, export and import.

5. GIMP does Layer mask.

6. As Far as I know GIMP works with Wacom Tablets and as I remember in Photoshop you have to set the right brush for them anyway.

But who cares about professionals, most of them would still use Photoshop regardless.

True but if Photoshop was natively ported to Linux, then more professional photographers would use Linux over Windows!. And probably be happier. Get my point!.

---

### Post by days_of_ruin on 2008-05-14
> **Xfcn said:**
> Interesting stuff so far.

**@days_of_ruin**
I'm curious to know how Inkscape could possibly influence the GIMP in interface, except maybe for an all-in-one resizable window like Inkscape has. Is that what you mean?

Yes, that all I meant.No clue what else that would mean.

---

### Post by Half-Left on 2008-05-14
> **jedimasterk said:**
> True but if Photoshop was natively ported to Linux, then more professional photographers would use Linux over Windows!. And probably be happier. Get my point!.

That really depends, alot use Mac's, thats like saying if Cuebase got ported to Linux all of the sound professionals would move to Linux, it's just not true.

Being devils advocate, why would they have paid for a Mac and Photoshop just to move to Linux and pay for Photoshop again?  These people dont increase desktop share at all for Linux.

---

### Post by jedimasterk on 2008-05-14
> **Half-Left said:**
> That really depends, alot use Mac's, thats like saying if Cuebase got ported to Linux all of the sound professionals would move to Linux, it's just not true.

Being devils advocate, why would they have paid for a Mac and Photoshop just to move to Linux and pay for Photoshop again?  These people dont increase desktop share at all for Linux.

I'm mainly talking about Windows XP users and graphics shops who are using Photoshop. Who may be very reluctant to upgrade to Vista do to it's poor reviews and performance. They may want to switch to Linux, but need to take Photoshop with them. Cheaper to bye a Linux version of Photoshop vs a whole new Mac on top of all new Mac software.

---

### Post by Half-Left on 2008-05-14
Well they still have to pay £650 for the Linux version if their was one, why not take their Windows version and use it with WINE until there is. CS3 should be working alot better soon in WINE anyway, I bet it will work perfect before a native version and have the same speed.

---

### Post by Xfcn on 2008-05-14
@jedimasterk & Half-Left

I appreciate the input, but this is a thread to discuss GIMP's short-comings for various artistic types, not Photoshop and why it should or should not be ported to Linux.

Anyhow. I do know that for my needs, GIMP has met them all head-on at every point, including down to filters. The only thing I can think of off the top of my head that I couldn't immediately figure out how to do in GIMP as opposed to Photoshop is the effect "Outer Glow", which traces a halo around the transparencies of an image. I used to use that to make very tight outlines for things, but I can come up with a comparable trick in GIMP.

---

### Post by peitschie on 2008-05-14
Gimp has some very exciting directions its heading in by the way.  See [http://geek2live.blogspot.com/2008/04/gimp-25-screenshots.html](http://geek2live.blogspot.com/2008/04/gimp-25-screenshots.html) for some of them.  It will be good to use free software :D

---

### Post by Xfcn on 2008-05-14
GIMP does look like it's heading in a great direction. I wish I had the programming skill to make a program like Sketchbook Pro (From AutoDesk, formerly Alias) or ArtRage. Those are great for doing art.

---

### Post by AJB2K3 on 2008-05-16
Gimp 2.4 is supposed to have CMYK support but are you saying that this CMYK support doesn't work?

Photo wise the most I've done in gimp is import raw images, resive then to 600px width then save as png.
I know png isn't ideal but at least its not a proprietary format.

---

### Post by Xfcn on 2008-05-16
As far as I know, GIMP's images are only RGB mode. While there IS a CMYK color mixer, you really aren't dealing with a true CMYK image, which is imperative to professional print as nobody prints in anything BUT CMYK.

---

### Post by hessiess on 2008-05-16
Photoshops interfase on windows is plain disgusting, far too much wasted screen space. however its much better on mac, and in this case its not all that difarent to GIMP.

---

### Post by yousufinternet on 2008-05-16
cmyk support can be easily done by separate plugin :D 
i used gimp to make books covers so many times without problems :D

---

### Post by eilu on 2008-05-16
> **peitschie said:**
> Gimp has some very exciting directions its heading in by the way.  See [http://geek2live.blogspot.com/2008/04/gimp-25-screenshots.html](http://geek2live.blogspot.com/2008/04/gimp-25-screenshots.html) for some of them.  It will be good to use free software :D

Polygonal selection at last! Looks like it is going in the right direction.

---

### Post by squidmaster on 2008-05-17
can't handle png transparency. Major turn off.

---

### Post by peitschie on 2008-05-17
Eh?  What's wrong with it's handling of png transparency...?  It seems to open and save png's with transparent backgrounds okay to me...

---

### Post by AJB2K3 on 2008-05-17
> **peitschie said:**
> Eh?  What's wrong with it's handling of png transparency...?  It seems to open and save png's with transparent backgrounds okay to me...
Agreed, works fine for me but the apng format (very expermental) only works via online creator.

---

### Post by peitschie on 2008-05-17
Ahh!  You bleeding edger you :D.  Glad to hear I don't need to get all fanboi lol :D

---

### Post by Xfcn on 2008-05-17
Yeah, PNG works absolutely perfectly for me on all levels. In fact, it works better for me than Photoshop... that's why I use GIMP. Because I save exclusively to PNG format.

---

### Post by Sockerdrickan on 2008-05-17
Yeah PNG is TEH format and is workin great. I bet the post was ironic.

---

### Post by jrusso2 on 2008-05-17
> **yousufinternet said:**
> cmyk support can be easily done by separate plugin :D 
i used gimp to make books covers so many times without problems :D

Yeah I tried that plugin never could get it to work.

---

### Post by Xfcn on 2008-05-17
> **Jiraya said:**
> Even pictures with just a few colors? I think in this case the best format is .GIF, isn't?

GIF is technically the superior format for something like that, but the kind of work I do never has less than 16 colors, even if it appears to only be black and white. The more colors you throw into the mix, the less GIF is reasonable for use. Frankly, I try to avoid GIF as much as possible. And JPEG. Everything I need from GIFs and JPEGs I get from PNG. Yes, sometimes the cost of file size is a bit higher, but honestly I work in such large formats that that particular issue isn't a true handicap.

---

### Post by AJB2K3 on 2008-05-18
> **Jiraya said:**
> Even pictures with just a few colors? I think in this case the best format is .GIF, isn't?

err no
the only thing is gif is good for is simple animations.
I gave up on gif when it kept distorting the colour on a simple 8 colour pixelart.

---

### Post by jedimasterk on 2008-05-18
[http://grimthing.com/archives/2007/01/11/Gimp_vs_Photoshop/](http://grimthing.com/archives/2007/01/11/Gimp_vs_Photoshop/)

This article makes a good point. For commercial printing two features are "crucial" native CMYK support and Pantone. Pantone is out of the question do to legal issues. But native CMYK support isn't. Also 16/32 color bit support is also crucial for printing, high resolution photos. Some of us do have Digital SLR's!.

---

### Post by cb951303 on 2008-05-18
> **jedimasterk said:**
> [http://grimthing.com/archives/2007/01/11/Gimp_vs_Photoshop/](http://grimthing.com/archives/2007/01/11/Gimp_vs_Photoshop/)

This article makes a good point. For commercial printing two features are "crucial" native CMYK support and Pantone. Pantone is out of the question do to legal issues. But native CMYK support isn't. Also 16/32 color bit support is also crucial for printing, high resolution photos. Some of us do have Digital SLR's!.

this post summarizes the short comings of gimp for pro use.
I remember RGB-to-Pantone converters being closed by Pantone Inc. How is that possible? I mean what is that they license? isn't it only a color? Can I license 255-0-255 then? :lolflag:

---

### Post by Xfcn on 2008-05-18
I fully agree with that article.

---

### Post by Sordelka on 2008-05-19
> **cb951303 said:**
> this post summarizes the short comings of gimp for pro use.
I remember RGB-to-Pantone converters being closed by Pantone Inc. How is that possible? I mean what is that they license? isn't it only a color? Can I license 255-0-255 then? :lolflag:

That is specifically license. Didn't hear about the PEPSI blue color?

---

### Post by cb951303 on 2008-05-19
> **Sordelka said:**
> That is specifically license. Didn't hear about the PEPSI blue color?

oh no did they license the pepsi blue? :confused:

---

### Post by jedimasterk on 2008-05-19
It's funny how Pixel Image Editor can support 8,16,and 32 bit, plus CMYK natively, and is maintained by one lone developer. and GIMP does neither!. Pittiful isn't it!.

---

### Post by Xfcn on 2008-05-19
No no. You cannot license a single color. Otherwise nail polish companies would sue each-other into oblivion, and the countries of The United States of America, France, Russia, Cuba and England would all wage battle over flag colors. Oh, and Japan would fight Canada.

---

### Post by cb951303 on 2008-05-19
> **Xfcn said:**
> No no. You cannot license a single color. Otherwise nail polish companies would sue each-other into oblivion, and the countries of The United States of America, France, Russia, Cuba and England would all wage battle over flag colors. Oh, and Japan would fight Canada.

what exactly Pantone Inc. licenses then? I'm really curious about it. How can they have power to shut down a RGB-to-Pantone converter website?

---

### Post by jedimasterk on 2008-05-19
Another good article from Linux Journal on were Gimp fails.

[http://www.linuxjournal.com/article/9706](http://www.linuxjournal.com/article/9706)

Krita and Cinepaint both have a better chance of gaining more highend features than Gimp for professionals.

---

### Post by Xfcn on 2008-05-19
> **cb951303 said:**
> what exactly Pantone Inc. licenses then? I'm really curious about it. How can they have power to shut down a RGB-to-Pantone converter website?

Pantone licenses swaths of colors.

[quote="WikiPedia Article"]Pantone asserts that their lists of color numbers and pigment values are the intellectual property of Pantone and free use of the list is not allowed.[9] This is frequently held as a reason why Pantone colors cannot be supported in Open Source software such as GNU Image Manipulation Program (GIMP) and are not often found in low-cost software. It has been claimed that "it seems as if the company is being intentionally unclear" but it is acknowledged that "the simplest claim would be trademark misappropriation or dilution towards someone who produced a color palette marketed as compatible with Pantone's".[10] However, Pantone palettes supplied by printer manufacturers can be obtained freely, and depending on supplier, do not come with usage restriction beyond sales ban on hard copy of the palette.

Pantone also possesses patent 5,734,800, a six-color Hexachrome printing system.[/quote]

---

### Post by King_Critter on 2008-05-19
> **jedimasterk said:**
> It's funny how Pixel Image Editor can support 8,16,and 32 bit, plus CMYK natively, and is maintained by one lone developer. and GIMP does neither!. Pittiful isn't it!.

Well, the Gimp was not originally designed to support those things. When Cinepaint forked, they had to rewrite a majority of the code to support those higher bit-depths. In fact, though, that's what the Gimp team is doing at the moment with GEGL. The next version of the Gimp (2.6) should have, among other things, support for higher bit-depths and CMYK.

---

### Post by Twitch6000 on 2008-05-19
> **King_Critter said:**
> Well, the Gimp was not originally designed to support those things. When Cinepaint forked, they had to rewrite a majority of the code to support those higher bit-depths. In fact, though, that's what the Gimp team is doing at the moment with GEGL. The next version of the Gimp (2.6) should have, among other things, support for higher bit-depths and CMYK.

I believe they are also trying to support a few other things that photoshop has that gimp does not am I right?

---

### Post by jedimasterk on 2008-05-20
> **King_Critter said:**
> Well, the Gimp was not originally designed to support those things. When Cinepaint forked, they had to rewrite a majority of the code to support those higher bit-depths. In fact, though, that's what the Gimp team is doing at the moment with GEGL. The next version of the Gimp (2.6) should have, among other things, support for higher bit-depths and CMYK.

Should!. But will it. Like I mentioned before one lonely developer created Pixel Image Editor, which is as close to Photoshop that you are going to get on Linux, from a support standpoint. Meaning supporting standards. Now what can a team (Gimp Team) do that one lonely developer can't. I'm not trying to be sarcastic here, but what is most needed for Gimp to get real attention is support for higher bit depths (8, 16, and 32) and CMYK, before the competition ups the ante again, and were back to being on the bottom of highend features. Remember the Linux Journal article. That was from 2005, and now it is 2008. So what has really been accomplished. Were still waiting for the great GEGL, and 16/32/CMYK support. Full support!. Just a thought!. Even Krita and Digikam supports these higher bit depths.

---

### Post by Half-Left on 2008-05-20
> **jedimasterk said:**
> Should!. But will it. Like I mentioned before one lonely developer created Pixel Image Editor, which is as close to Photoshop that you are going to get on Linux, from a support standpoint. Meaning supporting standards. Now what can a team (Gimp Team) do that one lonely developer can't. I'm not trying to be sarcastic here, but what is most needed for Gimp to get real attention is support for higher bit depths (8, 16, and 32) and CMYK, before the competition ups the ante again, and were back to being on the bottom of highend features. Remember the Linux Journal article. That was from 2005, and now it is 2008. So what has really been accomplished. Were still waiting for the great GEGL, and 16/32/CMYK support. Full support!. Just a thought!. Even Krita and Digikam supports these higher bit depths.

Why do you have to keep going on about this, It's funny though, they started Krita on the things GIMP lacked rather than develop it with all the other features. It's got a long way to go before it gets close to GIMP, higher bit depths and CMYK are useless when the rest of it is far behind.

Do you really think that these two features will get pros using GIMP all of a sudden, sorry it's just not going to happen and it only matters on the printing level. GIMP 2.5.0 already has GEGL, you can use it right now.

---

### Post by nihilvaio on 2008-08-30
I wish GIMP had a decent interface for the IWarp tool, since right now it is a real show-stopper. Using it as a tool probably would improve it dramatically, since you can zoom in and out, have the possibility of undoing single strokes, and masking with selections the areas you want to affect: pretty much what Photoshop does, but better (hopefully)!

---

### Post by _sAm_ on 2008-08-30
Do you know if Gimp will become faster then before when it use GEGL? 

I read that PS work much faster then Gimp on the same pc(with the settings changed for Gimp from default(cpu and ram usage to higher).

---

### Post by AJB2K3 on 2008-08-30
I take it you haven't explored all gimps menu's then?
Gimp can use seperate CMYK .icc colour profiles for both input and output formats so (in my case) I use a fuji icc to import the pictures then output it via a HP printer icc.

---

### Post by Howitzer777 on 2008-08-30
if gimp were to import some of ps's tools and stuff, that would be great. I know gimp isn't trying to emulate ps but some things just can't be helped.
Like adjustment and fill layers

magnetic scirrors should act like magnetic lasso meaning it should go continiusly with your mouse rather than clicking

i want better quick select tool

i want to better know  the features of gimp, not have them hidden.

i want more tools!

i want a simple user interface



and here is one idea that would just be f'ing amazing. 

How about we have different gimps inside the gimp. you know that internet explorer 8 has a feature to emulate ie 7?  we could have a button on the gimp to switch from

*normal gimp
*a photoshop emulator,(NOT GIMPSHOP unless its upgraded)
*one for people that are working on photographs and not custom graphic design
*graphic design gimp

---

### Post by Rhubarb on 2008-08-30
I'd like to see better metadata support.
Support for exif, IPTC, and XMP would be great.

And a few other things that have already been covered in this thread, such as 16bit colour per channel support.
But thankfully most of what I want is being developed for GIMP (GEGL) now anyway.
And thankfully again, exiftool is an excellent CLI based app that can do simply amazing things with metadata in pretty much any format.

---

### Post by Swenghk on 2008-08-30
I completelyquit using GIMP and used Blender, even for 2D creations, and using the Bezier Tool is much easier.

---

### Post by neota on 2008-08-31
> **King_Critter said:**
> Well, the Gimp was not originally designed to support those things. When Cinepaint forked, they had to rewrite a majority of the code to support those higher bit-depths. In fact, though, that's what the Gimp team is doing at the moment with GEGL. The next version of the Gimp (2.6) should have, among other things, support for higher bit-depths and CMYK.

No, it shouldn't. It does indeed use GEGL currently (2.5.x and development versions). There is more to it than that: You can apply arbitrary GEGL operations to the image, and color adjustments like Levels are calculated in floating-point thanks to GEGL; There are still many things to do before higher bitdepths and different colorspaces can be made available to the user:


 * All of the GIMP code must use GEGL to request pixel data; It needs some intelligence in how it does this (for example, if we are working with 8bit or 16bit integers for each channel, calculating using floating point is plenty accurate enough; For 32bit integers, calculating in double precision may be required to minimize loss of precision)

 * The fileformat must support it. This is actually fairly simple, but, any changes of this kind will require a redesign of the GIMP fileformat. Supporting higher bitdepths also requires supporting larger amounts of data, which requires different storage strategies. 
It looks like OpenRaster is a likely candidate for becoming the new standard GIMP fileformat.
see [http://pippin.gimp.org/xcf2/](http://pippin.gimp.org/xcf2/)
and
[http://pippin.gimp.org/OpenRaster/](http://pippin.gimp.org/OpenRaster/)
for some ideas on this. The basic model is 'xml document with attached resources, packaged in a zipfile'

* Much of the current plugins (eg 'Gradient map') need to become GEGL Ops instead of GIMP plugins. 
They all need to be more discerning about what kind of input image format they actually want (for instance, many filters currently operate on gamma-corrected 8bit data as if it were linear, which leads to wrong results. They need to ask for >=16bit linear data from GEGL so their results will be accurate.)

---

### Post by neota on 2008-08-31
> **Howitzer777 said:**
> if gimp were to import some of ps's tools and stuff, that would be great. I know gimp isn't trying to emulate ps but some things just can't be helped.
Like adjustment and fill layers

Non-destructive adjustments to layers : almost certainly going to happen
Adjustment layers: 100% certainly not going to happen.

Fill layers: What are they??

> 
magnetic scirrors should act like magnetic lasso meaning it should go continiusly with your mouse rather than clicking

i want better quick select tool

Have you tried the hybrid free/poly select tool in 2.5? I find that amazingly fast to use.

> 
i want to better know  the features of gimp, not have them hidden.

i want more tools!

i want a simple user interface

Those are in conflict.
More tools != simple user interface
more knowable gimp is actually not in conflict with simple user interface -- Go and submit a mockup to [http://gimp-brainstorm.blogspot.com](http://gimp-brainstorm.blogspot.com) of your ideas for making gimp simpler and more knowable!

> 
and here is one idea that would just be f'ing amazing. 

How about we have different gimps inside the gimp. you know that internet explorer 8 has a feature to emulate ie 7?  we could have a button on the gimp to switch from

*normal gimp
*a photoshop emulator,(NOT GIMPSHOP unless its upgraded)
*one for people that are working on photographs and not custom graphic design
*graphic design gimp
[/QUOTE]
This has been brought up before (eg. on the gimp-developer mailing list, and gimp-brainstorm.blogspot.com) , and is always promptly shot down. That's because having multiple user interfaces == hellishly confusing.

Simpler things like switchable keyboard shortcuts for different kinds of editing are more likely to be accepted.


You obviously have ideas -- go post some on [http://gimp-brainstorm.blogspot.com](http://gimp-brainstorm.blogspot.com) !

---

### Post by gimphoto on 2008-08-31
hi, i saw some misinfo about GIMP, afaik:

- Gimp is support CMYK but to use it we must install Separate+ plugin, can get it at: [http://cue.yellowmagic.info/softwares/separate.html]("http://cue.yellowmagic.info/softwares/separate.html")
if you have tried to install it and failed to use it that because Separate+ need ICC color profile that NOT supplied by default at all Linux distro, so you need to download it from internet, try to search at Google: "adobe icc color profile", yes it's free to download it and use it.

- If you processing BIG image then maybe you can consider to resize/create bigger SWAP file or move your SWAP to different partition to improve its performance, this because Linux depend on this SWAP file/partition as Virtual Memory even if your RAM is big.

- I saw some features list that stated not supported by GIMP actually can be replaced by plugins or scripts but you need to search it at Internet and install it by yourself. 

This is the most important features that i think is BIG missing from GIMP:
- Layer folder (create massive layer effects is disaster but this feature will be implemented after GEGL finish)
- 16 bit (really useful for photographer that use RAW or for processing HDR image, this is GEGL what for)
- Layer adjustment (implement image/color/effect adjustment without destroy original image and can be change the parameters anytime)
- Brush manager (for now for add new brush we must copy it manually to GIMP brush folder and also there is no brush categories)
- Plugin manager (for install new brush we must copy the plugin file to GIMP plugin folder, i think PS users also do it manually but we want GIMP better than PS, right? ;) )
- Image Browser (for now we depend on external image management program like Digikam or Picasa)  

actually there is many small things that can be improved on GIMP but this is the most missing point i think.

---

### Post by neota on 2008-08-31
> **gimphoto said:**
> 
This is the most important features that i think is BIG missing from GIMP:
- Layer folder (create massive layer effects is disaster but this feature will be implemented after GEGL finish)

This is more dependent on GIMP actually -- see what I said above about OpenRaster. 

> 
- 16 bit (really useful for photographer that use RAW or for processing HDR image, this is GEGL what for)

Also for painting. Painting in 8bit sRGB just doesn't work; Painting in 8bit scRGB (linear rgb) destroys detail as things get darker; 16bit scRGB is a sensible painting format. (painting in 16bit sRGB is just silly.)

> 
- Brush manager (for now for add new brush we must copy it manually to GIMP brush folder and also there is no brush ca tegories)

Aurimas Juska implemented resource tagging as a Google SoC 2008 project for GIMP. It's quite likely this will end up in GIMP 2.8.

---

### Post by sennep on 2008-09-17
> **gimphoto said:**
> 
- Layer folder (create massive layer effects is disaster but this feature will be implemented after GEGL finish)


Does anyone know when this will happen? Do I dare hope for it in 2.8?

---

### Post by Half-Left on 2008-09-17
> **sennep said:**
> Does anyone know when this will happen? Do I dare hope for it in 2.8?

It's in the 2.5.x version now.

---

### Post by sennep on 2008-09-18
> **Half-Left said:**
> It's in the 2.5.x version now.

Sweet:)

---

### Post by AJB2K3 on 2008-09-18
> **gimphoto said:**
> hi, i saw some misinfo about GIMP, afaik:

- Gimp is support CMYK but to use it we must install Separate+ plugin, can get it at: [http://cue.yellowmagic.info/softwares/separate.html]("http://cue.yellowmagic.info/softwares/separate.html")
if you have tried to install it and failed to use it that because Separate+ need ICC color profile that NOT supplied by default at all Linux distro, so you need to download it from internet, try to search at Google: "adobe icc color profile", yes it's free to download it and use it.

- If you processing BIG image then maybe you can consider to resize/create bigger SWAP file or move your SWAP to different partition to improve its performance, this because Linux depend on this SWAP file/partition as Virtual Memory even if your RAM is big.

- I saw some features list that stated not supported by GIMP actually can be replaced by plugins or scripts but you need to search it at Internet and install it by yourself. 

This is the most important features that i think is BIG missing from GIMP:
- Layer folder (create massive layer effects is disaster but this feature will be implemented after GEGL finish)
- 16 bit (really useful for photographer that use RAW or for processing HDR image, this is GEGL what for)
- Layer adjustment (implement image/color/effect adjustment without destroy original image and can be change the parameters anytime)
- Brush manager (for now for add new brush we must copy it manually to GIMP brush folder and also there is no brush categories)
- Plugin manager (for install new brush we must copy the plugin file to GIMP plugin folder, i think PS users also do it manually but we want GIMP better than PS, right? ;) )
- Image Browser (for now we depend on external image management program like Digikam or Picasa)  

actually there is many small things that can be improved on GIMP but this is the most missing point i think.
Urm 2 things with this
1 did you look in the options? there a pannels for specyfying *.icc profiles for import/print/export.
2, profiles are given buried in windows printer driver installers and its taken me 2 years to get my HP 8450 profiles (2 years to find out they were hiding in the windows spoiler folder :confused:.

Do people even explore gimp before moaning about function?

---

### Post by Half-Left on 2008-09-18
You can get your monitor ICC profile from your manufactures website, it usually comes with the windows driver like mine in a zip.

Then you can use this in gimp for proper colour profile when you import a image and it will convert it to your colour profile.

---

### Post by BLTicklemonster on 2008-09-20
> **Swenghk said:**
> I completelyquit using GIMP and used Blender, even for 2D creations, and using the Bezier Tool is much easier.

How in tarnation do you use blender to do 2d stuff? Show me some stuff you've done, I find this interesting.

One major failure in gimp for me, is like when I have an image I want to make larger, if the dpi is low to begin with, I can't get a clean looking picture when I enlarge it. I always have extreme "pixelization".

---

### Post by AJB2K3 on 2008-09-20
> **Half-Left said:**
> You can get your monitor ICC profile from your manufactures website, it usually comes with the windows driver like mine in a zip.

Then you can use this in gimp for proper colour profile when you import a image and it will convert it to your colour profile.

Lucky you, mine are hidden in thoose damn exe installer files, not seperate file :confused:


> **BLTicklemonster said:**
> How in tarnation do you use blender to do 2d stuff? Show me some stuff you've done, I find this interesting.

One major failure in gimp for me, is like when I have an image I want to make larger, if the dpi is low to begin with, I can't get a clean looking picture when I enlarge it. I always have extreme "pixelization".

First point, alot of talented artist do because they get better colur/profile/shadows.
Secound point - every piece of software I've use is like that.
PSP, PS, Gimp, Paint.net, mspaint, etc.

---

### Post by BLTicklemonster on 2008-09-20
Thanks alphanumeric person. Irfanview is good with blowing stuff up and smoothing them over, I just got spoiled using it when making larger images out of small ones. :(

---

### Post by lilpannell on 2008-09-20
I actually like gimp more than photoshop and fireworks

---

### Post by BLTicklemonster on 2008-09-20
Me, too. Just compiled 2.5.0 last night and realized right at the end that I should have compiled 2.5.4, doh.

The thing I like most about this one is, it opens with 

1. a canvas

and

2. a toolbox.

If you go to dialogs in the canvas toolbar and choose a dialog, it automatically docks to the toolbox. Sweet!!!! I've been docking dialogs to the toolbox all along, this saves me a step, plus it keeps many people from freaking out quite as much.

I still don't see why people freak that gimp doesn't wrap itself in a big window instead of using the desktop as it's work space. Open Photoshop and ignore the big window it opens up in; there's like 4 or 5 or more different docks independent of one another in there. Way more sloppy than gimp, but no one ever makes note of it.

---

### Post by civetta on 2008-10-05
Nice discussion. As a photographer, the two major changes I'm awaiting are 16 bit and non-destructive editing. I find that working with large images, it doesn't take long for my memory to fill up. I have to erase my undo history in order to go on editing.

As for user interface, suggestions on [http://gimp-brainstorm.blogspot.com](http://gimp-brainstorm.blogspot.com) are very interesting, especially idea for curve tool and the display filter/preview window. Very nice. Would be great for those working with slower machines. Same idea, but with a 100% loupe, as many RAW developers have, would be immensely helpful too. Rather than embedding buttons and tools into the tiny preview window, how about simply making an option to preview effects using the loupe window, or full image? GUI improvements like these would make GIMP more functional to GIMP users. Making it look and feel like Photoshop would only make it more usable if you were already accustom to working in Photoshop. I personally like having more windows (I only regularly work with two as one toolbar with tabs is enough to contain all the tools I use. I find this lets you switch around using the panel, and quickly make the most use of desktop space to display the image.

A question: I'm using Gimp 2.6 with GEGL, it's not possible to work with 16 bit images yet, or am I missing something? Is this planned for 2.8, or is full GEGL integration a target for 3.0?

Otherwise, GIMP is a very sophisticated program, and plugins are wonderful. For me, as for most photographers, the final test is the printed image, and I've made (RGB) prints I'm extremely satisfied with from GIMP, 8 bit image processing, destructive editing and all.

---

### Post by Half-Left on 2008-10-05
> **BLTicklemonster said:**
> How in tarnation do you use blender to do 2d stuff? Show me some stuff you've done, I find this interesting.

One major failure in gimp for me, is like when I have an image I want to make larger, if the dpi is low to begin with, I can't get a clean looking picture when I enlarge it. I always have extreme "pixelization".

Raster apps ALWAYS do, you can't scale something small to big and expect the same quality, only Vector can do that.

The only difference with GIMP, PS whatever is the way they filter the image, which basically makse it look better when enlarging, you still loose quality everytime.

---

### Post by Half-Left on 2008-10-05
> **civetta said:**
> nice discussion. As a photographer, the two major changes i'm awaiting are 16 bit and non-destructive editing. I find that working with large images, it doesn't take long for my memory to fill up. I have to erase my undo history in order to go on editing.

As for user interface, suggestions on [http://gimp-brainstorm.blogspot.com](http://gimp-brainstorm.blogspot.com) are very interesting, especially idea for curve tool and the display filter/preview window. Very nice. Would be great for those working with slower machines. Same idea, but with a 100% loupe, as many raw developers have, would be immensely helpful too. Rather than embedding buttons and tools into the tiny preview window, how about simply making an option to preview effects using the loupe window, or full image? Gui improvements like these would make gimp more functional to gimp users. Making it look and feel like photoshop would only make it more usable if you were already accustom to working in photoshop. I personally like having more windows (i only regularly work with two as one toolbar with tabs is enough to contain all the tools i use. I find this lets you switch around using the panel, and quickly make the most use of desktop space to display the image.

A question: I'm using gimp 2.6 with gegl, it's not possible to work with 16 bit images yet, or am i missing something? Is this planned for 2.8, or is full gegl integration a target for 3.0?

Otherwise, gimp is a very sophisticated program, and plugins are wonderful. For me, as for most photographers, the final test is the printed image, and i've made (rgb) prints i'm extremely satisfied with from gimp, 8 bit image processing, destructive editing and all.

**gegl**

> important progress towards high bit-depth and non-destructive editing in gimp has been made. Most color operations in gimp are now ported to the powerful graph based image processing framework gegl, meaning that the interal processing is being done in 32bit floating point linear light rgba. By default the legacy 8bit code paths are still used, but a curious user can turn on the use of gegl for the color operations with colors / use gegl. 

---

### Post by civetta on 2008-10-05
> **Half-Left said:**
> **gegl**

Thanks Half-Left. I see you can turn GEGL on and off, and that this changes internal processing, but I guess I still can't open 16 bit images without them being converted to 8 bit before I can work on them.

---

### Post by neota on 2008-11-26
> 
Then you can use this in gimp for proper colour profile when you import a image and it will convert it to your colour profile.

Just to be clear here: It's a good idea to get your monitor profile, and set it as 'display profile' in GIMP. It's not so good an idea to actually convert an image to your monitor profile -- in fact, that would often make your image seem discolored when viewing in a non-color-managed app (ie. the majority of them). Leaving the 'Working profile' as 'srgb built in' is usually appropriate.

---

### Post by elucidblue on 2009-09-21
KERNING!  I can't believe Gimp doesn't have such basic (and essential) functionality.

---

### Post by bruno9779 on 2009-09-21
> **jedimasterk said:**
> True but if Photoshop was natively ported to Linux, then more professional photographers would use Linux over Windows!. And probably be happier. Get my point!.

touche!!!

This is a really good point here...

I have tried many times to introduce linux to some professional photo-imaging friends, and the answer has always been:

"Linux? I know it, it is kool, I had (X distro) and I liked it, but it is completely useless for my work"

---

### Post by mcduck on 2009-09-22
> **elucidblue said:**
> KERNING!  I can't believe Gimp doesn't have such basic (and essential) functionality.

It does have the option, at the bottom of the text options dialog.

Or do you mean manual letter spacing between individual letters, and not the overall kerning of the text?

---

### Post by Neon Lights on 2009-09-22
> **mcduck said:**
> It does have the option, at the bottom of the text options dialog.

Or do you mean manual letter spacing between individual letters, and not the overall kerning of the text?
He means manual letter spacing, most definitely. It is a pretty big thing Gimp's missing. /: There was a script for it somewhere once upon a time, but that was way old xP

---

### Post by unutbu on 2009-09-22
How about use LaTeX to produce nice looking text with ligatures and kerning in a pdf file, then import the pdf into GIMP.

In the same vein, there is also the [textext plugin]("http://www.elisanet.fi/ptvirtan/software/textext/") for inkscape...

---

### Post by Danoz on 2009-09-24
> **Xfcn said:**
> Okay, I've been browsing the forums for awhile, and I've noticed that a lot of people say that GIMP falls short of needed work for professional photographers and a few other mediums. I'd like to see some specifics, here, as I only tend to encounter vague generalities.

I in no way shape or form represent or have the attention of the GIMP development team, but I am always curious to see what can be improved.

So, let's get specific here: where does GIMP fail you, and (if applicable) why?

GIMP is very powerful, though I personally find the interface to be a little clumsy and prefer Photoshop or PSP in this regard. I will use Gimp on occasion, I'm just not practiced with it.

Unless you work in the print industry, CMYK isn't an issue (and you shouldn't be using GIMP for this, anyway).

---

### Post by mamid on 2009-09-25
[I've been using gimp for nearly a decade now.]("http://www.justbreathecomic.blogspot.com/")  I like the cost in comparison to photoshop.  I'm sorry, but nothing beats FREE when you're staring at a $699.99 price tag for a program that although you really really really want, you can't justify the cost.  Does the student version come with the full program and if so, how much is it? (and does taking one course justify my label as student?)

So what if it doesn't do all the effects the photoshop does?  That's the main difference between them.  I can wait for the improvements come in.  If I couldn't, then I'd go and buy photoshop, even though it would mean my kids and I would eat mac and cheese for two months straight. :P

I find that gimp is good enough for me and what I need for now.  I have access to some of the other programs mentioned in this thread and I plan on trying them out.  But I'll stick with gimp.

---

### Post by Exodist on 2009-09-25
GIMP can do just as many and more effects then Photoshop. I have used both for so many years. IMHO GIMP is better and can do more, but the user has to know how to do them. I know this sounds confusing, at least at 4:30am I confuse myself.. Anyway. GIMP can be harder to learn at first to produce good graphics, unlike PS that many neat little graphic stuff is just a simple click away. That being said GIMP can out do photoshop after the user has learned how to fully take advantage of the tools and learned many of the tricks.

---

### Post by alex.rayu on 2009-09-25
If the cost is #1 concern you can as well dig your courtyard with a wooden stick, why buy a shovel - you'll get used to it. But if you are selling vegetables and the competition is high, the guy with a shovel will beat you. But nothing like a FREE stick!

Same with GIMP VS Photoshop. The guy is saying he lacks font spacing. another suggests: "Do it through PDF"... How nice! No-no, you CAN dig you court yard with a wooden stick!

---

### Post by etnlIcarus on 2009-09-25
If the, "competition is high", I don't know what you'd hope to achieve with a 'courtyard vegetable garden', anyway.

I also wouldn't accept the stick/shovel analogy, if only due to the exaggerated disparity.

---

### Post by alex.rayu on 2009-09-25
Yeah, there's task that is #1, not the price. If I need to edit a photo, GIMP will do. But if I make a design where I need to include raster images and vector shapes, editable text, with varied letter spacing or editable effects like shadow, glow, etc., that can be edited later without having to redo the whole layer, and you send it to a client, who may want to give it to another designer to further edit - then GIMP is like a wood stick where Photoshop is a shovel. Say, you want to work professionally in web design. This means that you will receive PSD files, AI files, and Fireworks layered editable PNG files to slice and dice. And there you go. You simply can't go beyound a garage studio freelancer with GIMP.

If you go pro, you earn money that will cover the cost of Photoshop. If you go with free GIMP, you will be out of serious business as a designer.

---

### Post by coldReactive on 2009-09-25
It's too bad GIMP is moving the Save as file type to the export feature, and is going to go with GEGL instead of adjustment layers. I'm getting annoyed with all these changes these days. GNOME-Shell included.

---

### Post by alex.rayu on 2009-09-26
**2 coldReactive:** Hold on man, wait and see what it's like in the end. Will always have time to to switch. I am now using win 7 for Photoshop reasons. Looking forward to Ubuntu running on GTK 3 and being more usable and intuitive, more like Mac OS and Win 7 and KDE. It appears to be likely that it will get spoilt though - but will wait to see the final thing.

---

### Post by Incendia on 2009-09-26
The sponge tool.

LOL.
I couldn't find it on gimp.
I don't mind using photoshop anyway.

---

### Post by kayosiii on 2009-09-27
AFAIK it doesn't exist... The closest thing is to put the paintbrush into saturation mode and use the colour to give the amount of saturation this works in an absolute way rather than a relative way.

---

### Post by kayosiii on 2009-09-27
For me the only reason I don't use the gimp more often than I do is lack of 16bit per channel image support.

Lack of CMYK support doesn't really bother me. I usually do print runs in the hundreds using high end laser rather than runs in the thousands using Offset printing. The really high quality stuff is really low runs so either gets put through High end 6 or more colour Inkjet printers or through photo processing. In both cases I have found CMYK to be more of a hinderance than a help. I usually request no colour correction when I get a print job done (so I can see where my system is out of calibration). I think to a large degree I got lucky and my Camera, Monitor and printed output match up fairly closely. CMYK is definately needed by some but you are going to have to show me your hardware calibrated CRT screen, or High end flat panel before I take you at all seriously about "needing" CMYK.

Photoshop is now something of a hybrid Vector / Raster editor the gimp really isn't. I remember photo-shop when it wasn't either - the best way to get things done was to work with photoshop in concert with a Vector editing program. These days I work mostly from inside Inkscape, I can drag and drop images or layers from the gimp directly into inkscape and I can save paths from inkscape and drop them into gimp from dolphin (yes I am a kde user). I would welcome gimp support for effects layers and vector objects but these are no where near as important to me as 16bit editing. 

The gimp's user interface feels a bit clunky and dated particularly for folks coming from photoshop. There is a setting you can change in the config file that makes it quite nice to use in fullscreen mode (in kde anyways - apparently it breaks badly in some enviroments which is why there is no UI for it). 

The UI isn't as bad as most people make out... Is not as good as other people make out either. I am annoyed both by the people who just want a free photoshop clone and by the folks who won't take a rational look at the UI problems of the existing interface. I say this as somebody who has used the gimp since before it reached version 1.0 and photoshop for a little bit longer. Interestingly about 2 years ago I was using the gimp to do something at a friends place to do some small job. Another of my friend was watching what I was doing over my shoulder... His comment took me by suprise - he said that what I was doing with he gimp was a lot more fluid than he had ever seen anybody do in photoshop.

File exchange thing - well I would like that to be better... I usually instruct people I work with that they can send me psd files but that I won't nessarily get things like effects layers and that sending me a multilayered tiff would be the prefered option. I am hoping that this openraster thing takes off as that will probably make a good interchange format.

---

### Post by emigrant on 2009-10-15
gimp doesnt have (what i noticed so far):

[LIST]
[*]folders (to put the layers in)
[*]blending options (emboss, glowing effects, shadow etc...)
[*]text resizing is weird
[*]most of the functions lack short cut keys compared to PS
[*]i don't find a way to deslect a selection
[*]etc... ;)
[/LIST]

---

### Post by mcduck on 2009-10-16
> **arshad3m said:**
> gimp doesnt have (what i noticed so far):

[LIST]
[*]folders (to put the layers in)
[*]blending options (emboss, glowing effects, shadow etc...)
[*]text resizing is weird
[*]most of the functions lack short cut keys compared to PS
[*]i don't find a way to deslect a selection
[*]etc... ;)
[/LIST]

Layer grouping would be nice indeed, although I consider it just a nice feature and not actual necessity.

Gimp has blending options. What youa re asking for are layer effects. I agree that they are nice is some situations, although I usually need to do the smae things manually anyway since most programs that I use with Photoshop files (like Motion) don't support layer effects anyway.

I never notices anything weird in text resizing. What do you mean?

Lack of pre-defined shortcut keys most likely comes from GTK's built-in support for user-defined shortcuts (System/Preferences/Appearance, Interface-tab, and enable "Editable menu shortcut keys".

To deselecet a selection go to Select/None. Or press Shift-Ctrl-A

---

### Post by etnlIcarus on 2009-10-16
> Layer grouping would be nice indeed, although I consider it just a nice feature and not actual necessity.I'd consider it a necessity. Doesn't matter how well you name your layers; without grouping, the 'mess' threshold is much lower.

Annoys me with Transmission-Gtk as well, doubly so since Transmission's Aqua GUI has had the feature for a while.

---

### Post by coldReactive on 2009-10-16
> **mcduck said:**
> Gimp has blending options. What youa re asking for are layer effects. I agree that they are nice is some situations, although I usually need to do the smae things manually anyway since most programs that I use with Photoshop files (like Motion) don't support layer effects anyway.

Adjustment Layers are never coming. GIMP Dev team said themselves they would be using GEGL instead.

---

### Post by mcduck on 2009-10-17
> **coldReactive said:**
> Adjustment Layers are never coming. GIMP Dev team said themselves they would be using GEGL instead.

I rarely use adjustment layers anyway (for the same reason why I don't use layer effects much, they don't work well together with other programs). But I suppose emigrant meant layer effects, not blending options (which Gimp has) or adjustment layers (which Gimp is not going to get).

---

### Post by kayosiii on 2009-10-17
> **emigrant said:**
> gimp doesnt have (what i noticed so far):

[LIST]
[*]folders (to put the layers in)
[/LIST]
This is a target for the current development release.

> [LIST]
[*]blending options (emboss, glowing effects, shadow etc...
[*]text resizing is weird
[*]most of the functions lack short cut keys compared to PS
[/LIST]
I don't find that to be true - most common operations have keyboard shortcuts (they are not the same as the photoshop ones) and you can assign a keyboard shortcut to pretty much everything in the peferences (or dynamically if enable that functionality.
> [LIST]
[*]i don't find a way to deslect a selection
[/LIST]
CTRL + SHIFT + A or click outside your selected area.

[*]etc... ;)
[/LIST][/QUOTE]

---

### Post by kayosiii on 2009-10-17
> **coldReactive said:**
> Adjustment Layers are never coming. GIMP Dev team said themselves they would be using GEGL instead.

coldReactive - you are confusing the ends and the means. GEGL is the technology they will use to implement Adjustment Layers amongst other things. GEGL opens up possibilities beyond this though.

---

### Post by Exodist on 2009-10-18
> **kayosiii said:**
> coldReactive - you are confusing the ends and the means. GEGL is the technology they will use to implement Adjustment Layers amongst other things. GEGL opens up possibilities beyond this though.



[http://gegl.org/](http://gegl.org/)

Never says it will, unless I overlooked it. But it could open the possibility in the future. Right now its base usage is not to destroy the image as you are editing it.

---

### Post by DirtDawg on 2009-10-19
Here's a real simple way for folks to see a GIMP FAIL in action. Please note I am a huge GIMP fan. I use it 90% of the time for my graphics need and actually find the GUI more efficient than Photoshop's (yeah that's right, I like it better).

That said, it's FAIL time, step by step:

**Step 1:** Open a new file. Size doesn't matter. My default is 800x600.

**Step 2:** Change the foreground color to the brightest red you can find. Next, choose the paintbucket tool (shift+B) and fill the entire background that bright red color. 

**Step 3:** Change the foreground color to a really bright blue, the idea being maximum contrast between background and foreground. Now choose the paintbrush tool (P) and use the mouse to draw a blob or sloppy circle. Make sure the final shape is closed. 

**Step 4:** With the blue from step 3 still selected, once again choose the paintbucket tool (shift+B). Now try to fill the blue shape you made with the paintbucket tool. 
Seems simple, right? But look what happens. A tiny sliver of red remains between the blue outline you created and the fill. You know what that line is called? It's called a FAIL.

Go ahead and undo your fill, play with the paintbucket settings and try again. Try playing with the threshold. Play with it all day long or all week long, it will never work. You will always get that little "moat" between the outline and the fill that can only be eliminated, tediously, by hand. Or the threshold will be too high, filling the entire canvas. Photoshop has anti-aliased fills, so this problem does not exist.

Now seriously, I love the GIMP. I can't stress that enough. But I see a lot of threads complaining that professional's problems with the GIMP stem from our inability to be flexible, or our general snottiness, or whatever. I just wanted to post this to show everyday users, who should not be expected to understand CMYK processing, a simple demonstration that exposes one of the small flaws that plague the GIMP. These small flaws really add up when working in a professional capacity and can slow workflow to a crawl or, occasionally, stop it altogether.

So yeah, long live the GIMP, warts and all!

---

### Post by mcduck on 2009-10-19
Sorry, just tried that, with a proper threshold for the paint bucket tool there's no seam. :)

And if you actually used the pencil tool instead of paintbrush you wouldn't even have to adjust the threshold.

---

### Post by DirtDawg on 2009-10-19
> **mcduck said:**
> Sorry, just tried that, with a proper threshold for the paint bucket tool there's no seam. :)

And if you actually used the pencil tool instead of paintbrush you wouldn't even have to adjust the threshold.

What? What threshold would that be? Please share.

As far as the pencil suggestion, the lack of anti-aliased fill affects more than this simple demonstration. For example, if something is scanned in, then filled in this way.

EDIT: I went back just to be certain. Sure enough, set the threshold to 170.9, you get the FAIL moat (don't see it? Zoom in). Set the threshold to 171.0 (that's a .1 difference), it floods the entire canvas. 

Maybe 170.9995 worked for you?

---

### Post by etnlIcarus on 2009-10-19
DirtDawg is correct.

[Looks fine](http://img26.imageshack.us/img26/470/thresholdk.png)

[...until](http://img18.imageshack.us/img18/1333/threshold2.png).

---

### Post by mcduck on 2009-10-20
> **DirtDawg said:**
> What? What threshold would that be? Please share.

As far as the pencil suggestion, the lack of anti-aliased fill affects more than this simple demonstration. For example, if something is scanned in, then filled in this way.

EDIT: I went back just to be certain. Sure enough, set the threshold to 170.9, you get the FAIL moat (don't see it? Zoom in). Set the threshold to 171.0 (that's a .1 difference), it floods the entire canvas. 

Maybe 170.9995 worked for you?

Sure, it could be that there's a small line if zoomed in close enough. I only checked at 200% zoom. :)

But I still wouldn't call that a "FAIL", it's a image manipulation app after all, not a drawing program. If I needed pixel-perfect drawings I'd use Inkscape instead.

(besides, drawing a selection and filling it would solve even this "FAIL", and that's how I'd do this kind of thing regardless of if I'm working in Photoshop or Gimp.)

Edit: I actually tried this same thing in Photoshop. Guess what? Exactly the same results, with default tolerance a clearly visible seam, and even with the paint bucket tool's settings adjusted there are some wrong colored pixels when zoomed in close enough. I wonder what program you'll use now since even Photoshop doesn't allow you to "work in a professional capacity".

Honestly, drawing things that way might have been a nice method in Microsoft Paint, but when using antialiased tools, possibly with opacity falloffs like most brush tools have, you really can't except pixel-perfect results. Not even with Photoshop. Now isn't *that* annoying. :D

---

### Post by Exodist on 2009-10-20
> **DirtDawg said:**
> Here's a real simple way for folks to see a GIMP FAIL in action. Please note I am a huge GIMP fan. I use it 90% of the time for my graphics need and actually find the GUI more efficient than Photoshop's (yeah that's right, I like it better).

That said, it's FAIL time, step by step:

**Step 1:** Open a new file. Size doesn't matter. My default is 800x600.

**Step 2:** Change the foreground color to the brightest red you can find. Next, choose the paintbucket tool (shift+B) and fill the entire background that bright red color. 

**Step 3:** Change the foreground color to a really bright blue, the idea being maximum contrast between background and foreground. Now choose the paintbrush tool (P) and use the mouse to draw a blob or sloppy circle. Make sure the final shape is closed. 

**Step 4:** With the blue from step 3 still selected, once again choose the paintbucket tool (shift+B). Now try to fill the blue shape you made with the paintbucket tool. 
Seems simple, right? But look what happens. A tiny sliver of red remains between the blue outline you created and the fill. You know what that line is called? It's called a FAIL.



LMAO!!  NO my friend YOU FAIL.. LOL 

Dont get all upset because you dont understand how to adjust your tools to work the way you want.

Also Paintbrush by default is soft on the edges. The reason it doesnt fill in the area the way you think it should is because the feathering of the brush edge is actually purple you dumass.. You choose to fill BLUE not PURPLE...

Something tells me you failed in art class!!

---

### Post by strycore on 2009-10-20
I went through the 11 pages and tried to make a summary of missing functionalities, I removed anything that isn't true anymore with Gimp 2.6 but maybe I forgot some stuff.

- Slices for the web
- Rollovers via Imageready
- Non-square pixel support for video
- Unsharp Mask or Smart Sharpen
- Liquify filter (iWarp ?)
- Clipping Groups
- Layer Effects
- CMYK support (plugin ?)
- Pantone (Legal issues ?) (use imported file ?)
- 16 bit (really useful for photographer that use RAW or for processing HDR image, this is what GEGL is for) 
- Layer folders : This is a target for the current development release.
- Layer adjustment : implement image/color/effect adjustment without destroy original image and can be change the parameters anytime (Made possible by GEGL ?)
- Brush manager : for now for add new brush we must copy it manually to GIMP brush folder and also there is no brush categories. Aurimas Juska implemented resource tagging as a Google SoC 2008 project for GIMP. It's quite likely this will end up in GIMP 2.8.
- Plugin manager : for install new brush we must copy the plugin file to GIMP plugin folder, i think PS users also do it manually but we want GIMP better than PS, right? 
- Image Browser (Adobe Bridge browser) : For now we depend on external image management program like Digikam or Picasa
- Kerning ( [http://en.wikipedia.org/wiki/Kerning](http://en.wikipedia.org/wiki/Kerning) ) : Don't know if this is true
- The sponge tool : The closest thing is to put the paintbrush into saturation mode and use the colour to give the amount of saturation this works in an absolute way rather than a relative way.
- Better metadata support. Support for EXIF, IPTC, and XMP would be great.

My goal is to provide a tiny script to change default behavior of Gimp so that Photoshop users won't be lost with Gimp. This is somehow similar to Gimp forks such as gimpshop or GimPhoto but without being a fork, only a small set of scripts. These forks are poorly maintained and you don't get the enhancement of Gimp 2.6.
I started a project on Launchpad called gimpshop-ng, feel free to flood the Questions section ! [https://launchpad.net/gimpshop-ng](https://launchpad.net/gimpshop-ng)

I also ask you to do some work here : [https://answers.launchpad.net/gimpshop-ng/+question/86349](https://answers.launchpad.net/gimpshop-ng/+question/86349) ("What is the first thing that disturbs a Photoshop user in Gimp ?")

---

### Post by etnlIcarus on 2009-10-20
> **etnlIcarus said:**
> DirtDawg is correct.

[Looks fine](http://img26.imageshack.us/img26/470/thresholdk.png)

[...until](http://img18.imageshack.us/img18/1333/threshold2.png).

> **Exodist said:**
> LMAO!!  NO my friend YOU FAIL.. LOL 

Dont get all upset because you dont understand how to adjust your tools to work the way you want.

Also Paintbrush by default is soft on the edges. The reason it doesnt fill in the area the way you think it should is because the feathering of the brush edge is actually purple you dumass.. You choose to fill BLUE not PURPLE...

Something tells me you failed in art class!!

I used separate layers









..."dumbass".

---

### Post by saxasm on 2009-10-20
> **strycore said:**
> I went through the 11 pages and tried to make a summary of missing functionalities, I removed anything that isn't true anymore with Gimp 2.6 but maybe I forgot some stuff.

- Slices for the web
- Rollovers via Imageready
- Non-square pixel support for video
**- Unsharp Mask or Smart Sharpen**(Both exist, the second only with resynthesizer plugin)
- Liquify filter (iWarp ?)
- Clipping Groups
- Layer Effects
- CMYK support (plugin ?)
- Pantone (Legal issues ?) (use imported file ?)
- 16 bit (really useful for photographer that use RAW or for processing HDR image, this is what GEGL is for) 
- Layer folders : This is a target for the current development release.
- Layer adjustment : implement image/color/effect adjustment without destroy original image and can be change the parameters anytime (Made possible by GEGL ?)
- Brush manager : for now for add new brush we must copy it manually to GIMP brush folder and also there is no brush categories. Aurimas Juska implemented resource tagging as a Google SoC 2008 project for GIMP. It's quite likely this will end up in GIMP 2.8.
- Plugin manager : for install new brush we must copy the plugin file to GIMP plugin folder, i think PS users also do it manually but we want GIMP better than PS, right? 
- Image Browser (Adobe Bridge browser) : For now we depend on external image management program like Digikam or Picasa
- Kerning ( [http://en.wikipedia.org/wiki/Kerning](http://en.wikipedia.org/wiki/Kerning) ) : Don't know if this is true (It is. Very easy to test)
- The sponge tool : The closest thing is to put the paintbrush into saturation mode and use the colour to give the amount of saturation this works in an absolute way rather than a relative way.
- Better metadata support. Support for EXIF, IPTC, and XMP would be great.

My goal is to provide a tiny script to change default behavior of Gimp so that Photoshop users won't be lost with Gimp. This is somehow similar to Gimp forks such as gimpshop or GimPhoto but without being a fork, only a small set of scripts. These forks are poorly maintained and you don't get the enhancement of Gimp 2.6.
I started a project on Launchpad called gimpshop-ng, feel free to flood the Questions section ! [https://launchpad.net/gimpshop-ng](https://launchpad.net/gimpshop-ng)

I also ask you to do some work here : [https://answers.launchpad.net/gimpshop-ng/+question/86349](https://answers.launchpad.net/gimpshop-ng/+question/86349) ("What is the first thing that disturbs a Photoshop user in Gimp ?")

Some of those exist.

---

### Post by DirtDawg on 2009-10-20
Alright, well clearly "FAIL" was too strong a word. I used it since it was in the title of the thread, so I thought it was sort of cute, I suppose. But I can see now it gets people riled up. So I'll call things, "overlooked annoyances," from here on. 

@McDuck: Turn the anti-aliased option "on" for your Photoshop paintbucket tool and try again.
That's really all I'm pointing out is GIMP's lack of anti-aliasing for the fill tool. It's not a big deal, just an overlooked annoyance. What I'm trying to relate is the idea that the GIMP's lack of polished corners can add up when you're trying to get work done, fast, on someone else's dime. Still, I use it nearly all of the time because I prefer it to Photoshop. Really!

@Strycore: You forgot to add anti-aliasing for the paintbucket tool to your list for whatever it is you're doing.

---

### Post by mcduck on 2009-10-20
> **DirtDawg said:**
> Alright, well clearly "FAIL" was too strong a word. I used it since it was in the title of the thread, so I thought it was sort of cute, I suppose. But I can see now it gets people riled up. So I'll call things, "overlooked annoyances," from here on. 

@McDuck: Turn the anti-aliased option "on" for your Photoshop paintbucket tool and try again.
That's really all I'm pointing out is GIMP's lack of anti-aliasing for the fill tool. It's not a big deal, just an overlooked annoyance. What I'm trying to relate is the idea that the GIMP's lack of polished corners can add up when you're trying to get work done, fast, on someone else's dime. Still, I use it nearly all of the time because I prefer it to Photoshop. Really!

@Strycore: You forgot to add anti-aliasing for the paintbucket tool to your list for whatever it is you're doing.

I already had anti-aliasing enabled in Photoshop. And also tested with different values for tolerance. Still, exactly the same result as with Gimp.

[[IMG]http://pontusschonberg.net/files/ps_bucket_small.png[/IMG]]("http://pontusschonberg.net/files/ps_bucket.png")

edit: Actually Gimp did this better than photoshop does. At least with Gimp I could get a result where the border wasn't visible unless zoomed in very close, while Photoshop leaves a seam that's visible even at normal zoom, even with the highest possible tolerance setting..

---

### Post by DirtDawg on 2009-10-20
> **mcduck said:**
> I already had anti-aliasing enabled in Photoshop. And also tested with different values for tolerance. Still, exactly the same result as with Gimp.

[[IMG]http://pontusschonberg.net/files/ps_bucket_small.png[/IMG]]("http://pontusschonberg.net/files/ps_bucket.png")

edit: Actually Gimp did this better than photoshop does. At least with Gimp I could get a result where the border wasn't visible unless zoomed in very close, while Photoshop leaves a seam that's visible even at normal zoom, even with the highest possible tolerance setting..

Well, hell. When I'm wrong, I'm wrong. I tested this in Photoshop as well and it doesn't work! But I know what I'm talking about so you'll have to trust me on this one.

If you scan a grayscale drawing (black & white line drawing, for example), then try to color it with GIMP, it won't work because you'll get those little moats between the fill and the ink work.

I discovered this overlooked annoyance from a very real life scenario when a deadline was breathing down my neck and I had to color a b&w drawing with flat fills. I was horrified to find GIMP lacked anti-aliased fills and, as a result, a less than perfect product went to print. I was pissed. Photoshop has an anti-aliased option on the fill tool for a reason, it's not there for show.

Unfortunately, my demonstration was a poor one in the end, but I still stand by my original point.

---

### Post by Exodist on 2009-10-21
Proper way to fill the circle would be to select it, remove inner selection then use the fill color on the separate layer all together or just stay on the same layer and use the brush/pencil tool paint the selected area(s).

---

### Post by kayosiii on 2009-10-21
> **Exodist said:**
> [http://gegl.org/](http://gegl.org/)

Never says it will, unless I overlooked it. But it could open the possibility in the future. Right now its base usage is not to destroy the image as you are editing it.

What do you think an adjustment layer is if not a means of changing an image without destroying it. GEGL provides the backend, Gimp provides the interface and you have adjustment layers - is that really that hard to understand.

---

### Post by etnlIcarus on 2009-10-21
> **kayosiii said:**
> What do you think an adjustment layer is if not a means of changing an image without destroying it. GEGL provides the backend, Gimp provides the interface and you have adjustment layers - is that really that hard to understand.

"Adjustment layer", isn't a synonym for, "non-destructive editing". Adjustment layers are a specific metaphor for exposing non-destructive editing; one which The GIMP devs have no intention of implementing.

---

### Post by kayosiii on 2009-10-21
> **DirtDawg said:**
> Well, hell. When I'm wrong, I'm wrong. I tested this in Photoshop as well and it doesn't work! But I know what I'm talking about so you'll have to trust me on this one.

If you scan a grayscale drawing (black & white line drawing, for example), then try to color it with GIMP, it won't work because you'll get those little moats between the fill and the ink work.

I discovered this overlooked annoyance from a very real life scenario when a deadline was breathing down my neck and I had to color a b&w drawing with flat fills. I was horrified to find GIMP lacked anti-aliased fills and, as a result, a less than perfect product went to print. I was pissed. Photoshop has an anti-aliased option on the fill tool for a reason, it's not there for show.

Unfortunately, my demonstration was a poor one in the end, but I still stand by my original point.

Wow Ink drawing coloring 101 for you my friend...
1) add your ink drawing
2) add a white layer
3) place the white layer below the ink drawing
4) set the ink drawings layer mode to multiply
5) work on the white background layer It's now impossible to damage your inkwork.

If you are working all flat colours - there is a proceedure I can take you through in inkscape that gets results much faster.

---

### Post by kayosiii on 2009-10-21
> **etnlIcarus said:**
> "Adjustment layer", isn't a synonym for, "non-destructive editing". Adjustment layers are a specific metaphor for exposing non-destructive editing; one which The GIMP devs have no intention of implementing.

That is curious - can you post a link?

---

### Post by etnlIcarus on 2009-10-21
To what?

---

### Post by kayosiii on 2009-10-21
To where the gimp developers said that they were not interested in implementing adjustment layers....

The latest I have - from january this year on the gimp developer list is

> There are plans for adjustment layers but before it makes sense to start
adding such things to GIMP GEGL needs to be more integrated. We would
love getting help here so anything you are able to do that brings us
closer to adjustment layers is appreciated. The hard part will not be to
add adjustment layers once GEGL is integrated, the hard part is actually
getting GEGL integrated in a good way.


---

### Post by coldReactive on 2009-10-21
> **kayosiii said:**
> To where the gimp developers said that they were not interested in implementing adjustment layers....

The latest I have - from january this year on the gimp developer list is

As your quote says, they're more interested in GEGL than adjustment layers.

---

### Post by etnlIcarus on 2009-10-21
> **coldReactive said:**
> As your quote says, they're more interested in GEGL than adjustment layers.

That's rather disingenuous.

As for what the quote *does* state, I guess we're listening to different developers. The official line has been, for the longest time, that The GIMP devs had no intention of adding adjustment layers, as it was felt that Adjustment layers were the wrong way to expose non-destructive editing.

And no, I don't have any sources and have no intention of fighting with my browser history, trying to find any.

---

### Post by DirtDawg on 2009-10-21
> **kayosiii said:**
> Wow Ink drawing coloring 101 for you my friend...
1) add your ink drawing
2) add a white layer
3) place the white layer below the ink drawing
4) set the ink drawings layer mode to multiply
5) work on the white background layer It's now impossible to damage your inkwork.

If you are working all flat colours - there is a proceedure I can take you through in inkscape that gets results much faster.

Hey, thanks for the condescending advice I didn't ask for. I'm quite aware of the Multiply function, thank you very much. Turns out there's more than one way to skin a cat.

But, you know, I just started making art last week, so I have some catch up to do.

---

### Post by Exodist on 2009-10-21
> **kayosiii said:**
> What do you think an adjustment layer is if not a means of changing an image without destroying it. GEGL provides the backend, Gimp provides the interface and you have adjustment layers - is that really that hard to understand.

Thats what I said. _GEGL can provide a backend for it_. But they dont say they will add adjustment layers. They may have something else in mind for that backend to provide. I am not here trying to predict or speculate on the direction they are going to go in. Unless its in writing, we can only guess at best. Its like trying to argue they are building a house when someone has only poured the foundation for a structure that could be used also for a car garage or a grocery store.

---

### Post by kayosiii on 2009-10-21
> **coldReactive said:**
> Adjustment Layers are never coming. GIMP Dev team said themselves they would be using GEGL instead.

@exodist:: I was more-so replying to the above quote.
For the most part I agree with you.

---

### Post by Exodist on 2009-10-22
> **kayosiii said:**
> @exodist:: I was more-so replying to the above quote.
For the most part I agree with you.

All good :)

---

### Post by kayosiii on 2009-10-23
> **coldReactive said:**
> As your quote says, they're more interested in GEGL than adjustment layers.
What you are not understanding it seems is what GEGL actually is. It is a new graphics engine for the GIMP that will get rid of the current architectural limitations which make adding things like adjustment layers next to impossible. 

Its not a matter of being more interested in one or the other its that GEGL will bring about the the means by which Adjustment Layers could be implemented. 

Currently various subsystems are being slowly ported the GEGL once enough subsystems have been ported then it will be possible to add features that will be built on top of this.

How this will be exposed to the user is another is another question. Whether it will be adjustment layers as we know them in photoshop or something else is still not certain. 

If it is something else my guess something akin to what you find in node based compositors (eg shake,nuke,blender). I will be happy to see non destructive editing in gimp (I don't particularly care what form it takes). I will be even more happy to be able to edit 16 bit per channel images

---

### Post by kayosiii on 2009-10-23
> **DirtDawg said:**
> Hey, thanks for the condescending advice I didn't ask for. I'm quite aware of the Multiply function, thank you very much. Turns out there's more than one way to skin a cat.

But, you know, I just started making art last week, so I have some catch up to do.

Apologies for coming off condescending... Yes the fill tool in the gimp is substandard your suggestion that it should be anti-aliased is an excellent one.

I have done a lot of ink based illustration with computer colouring and I never even thought to use the fill tool (in a bitmap editor anyways).Its been a while since I have used  Photoshop so I ask. Does photoshops fill tool now give you a pixel perfect fill without eating into your linework?

I usually either use the layer multiply trick and quickly paint the background in gives the best quality results especially if you want to vary the colours a bit.

The other method I currently employ is to trace the bitmap in inkscape duplicate the trace.  I Break apart the duplicate and delete the outer path. Now I can select the inner shapes and assign the colour to them.
After the tracing there is no loss to quality of linework.

---

### Post by aspergerian on 2009-10-23
As an ~advanced amateur photographer, I've owned and used PS7, CS2, and now CS4. I'm new to Linux, having had an Asus 701, Asus 901, and now an HP Mini. On the latter two, I wiped the hd and installed Heron. I'd be entirely Ubuntu now except for some of the photoshop tools I've not found in Gimp (or haven't learned to use). 

I have yet to figure out how to do signatures in Gimp. Yes, I've tried Gimp's text command many times - but Photoshop makes very easy changing the color of the signature (text), the size of the signature, and the location. For a long time, I try that no more in Gimp. 

I have yet to find in Gimp something nearly identical to Photoshop's shadow/highlight tool. 

I just got an Acer 751h and intend to make it a dual boot - with XP hung onto for its photo processing options - tho' not for CS4. I looked at [http://www.gimp.org/](http://www.gimp.org/) again this morning and didn't find a users discussion group. Such a group would be helpful for those of us who are new to Linux and want to try hard to make Gimp work. 

Meanwhile, when a photo matters, I fall back to CS4 on two XP machines.

---

### Post by kayosiii on 2009-10-24
After reading up on exactly what the highlight shadow tool does... The closest I can think to emulate the effect would take a few steps
1) duplicate the layer you are working on and use the curves tool to adjust the highlights shadows to the correct value you will want a small upward facing bulge int the sw corner of the curves box and a small downward facing bulge in the ne corner.

2) create a layer mask for the adjusted layer
3) copy the original image to the layer mask 
4 these two steps will need to be adjusted until you get it right 
  a) The equivelent of radius can be set using a guassian blur
  b) use another curves control to return most of the image to normal.
   
This second curve should run accross the bottow of the curves dialog except at the extremes where it should move to the very top.

I am not sure if that will make a great deal of sense to you. If you like I could post some screenshots. Obviously the photoshop way of doing it is conciderably easier and I am not convinced of the utility of this method without 16bit editing but there you go.

---

### Post by aspergerian on 2009-10-24
kayosiii, 

Thnx for the reply. I use a wee bit of shadow highlight on many of my photos and would not want to have to enact the steps you set forth. Too laborious, too time consuming, too much eye strain.

---

### Post by Johnsie on 2009-10-25
I'm a full time professional programmer. The main problem I have with GIMP is it's name. It would be pretty hard for people in business to take me seriously if I went around recommending that people install "The Gimp". Photoshop and Paintshop Pro have good, professional sounding names, but GIMP... We'll, that's got nothing to do with what the program actually does and is just not professional sounding enough. Yes, the letters G.I.M.P. stand for something related to graphics but that's not what people are going to pick up on. Give it a less stupid name and people might actually take it seriously.

---

### Post by Penguin Guy on 2009-10-25
It's hard to learn, other than that it's great. Oh, and the name - 'I Gimped it.' doesn't quite have the same ring to it as 'I Photoshopped it.'. :(

---

### Post by kayosiii on 2009-10-25
@Johnsie -- you could just refer to it as the "GNU image manipulation program".... Can't say anybody around here has ever complained about the name - you must be from one of those sexually repressed parts of the world :p

@aspergerian... Well the photoshop method is faster if that (and the other benefits) are worth the price tag ($1400 local currency) to you then by all means go for it. It's the kind of thing that would be possible to write as a script-fu (or plugin). For me though the killer is lack of 16bit per channel editing.

---

### Post by aspergerian on 2009-10-25
> **kayosiii said:**
> Well the photoshop method is faster if that (and the other benefits) are worth the price tag ($1400 local currency) to you then by all means go for it. It's the kind of thing that would be possible to write as a script-fu (or plugin). For me though the killer is lack of 16bit per channel editing.

I already own CS4 and machines on which it runs. I would prefer to convert totally to Ubuntu but am held up due to photoshop's functionality. 

I shoot >99% of my images in Raw and, near the end of processing, turn them into 8 bit images (from something larger) so as to write as JPG (if that's the file type relevant to the final image). 

In this free Adobe Photoshop and digital photo essentials tutorial, we explain the benefits of working with 16-bit images over 8-bit images in Photoshop.
[http://www.photoshopessentials.com/essentials/16-bit/](http://www.photoshopessentials.com/essentials/16-bit/)

---

### Post by kayosiii on 2009-10-25
> **aspergerian said:**
> I already own CS4 and machines on which it runs. I would prefer to convert totally to Ubuntu but am held up due to photoshop's functionality. 

I shoot >99% of my images in Raw and, near the end of processing, turn them into 8 bit images (from something larger) so as to write as JPG (if that's the file type relevant to the final image). 

In this free Adobe Photoshop and digital photo essentials tutorial, we explain the benefits of working with 16-bit images over 8-bit images in Photoshop.
[http://www.photoshopessentials.com/essentials/16-bit/](http://www.photoshopessentials.com/essentials/16-bit/)

I know lack of 16 bit support is the main thing keeping me from using the GIMP. I can work around most of the other limitations (well more inconveniences). These days I use the raw conversion software for my camera (using wine) These are saved as 16 bit tiff files and I use  digikam for some very basic correction after that. I have found a place that will print my 16bit tiff files so I only ever go to jpeg when customers want electronic files or when they go to web. Lack of tools like photoshop is forcing me to focus on getting it right in the camera which for me is not entirely a bad thing.

---

### Post by Exodist on 2009-10-26
> **aspergerian said:**
> I already own CS4 and machines on which it runs. I would prefer to convert totally to Ubuntu but am held up due to photoshop's functionality.

So install Sun VirtualBox with XP and use it.. :-)

Even I got some home video software thats windows only I have to use XP in VB.

---

### Post by Rodney9 on 2009-11-03
Where do you find in Gimp 2.6.7 exif info.
I have searched and found they made a plug-in for 2.4 , I have searched help and the net but for the life of me I can not find it in 2.6.7

Any clues ?

Rodney

---

### Post by ElSlunko on 2009-11-04
I just discovered the fx-foundry plugins for GIMP. Pretty cool stuff!

---

### Post by BLTicklemonster on 2009-11-04
> **Penguin Guy said:**
> It's hard to learn, other than that it's great. Oh, and the name - 'I Gimped it.' doesn't quite have the same ring to it as 'I Photoshopped it.'. :(

Huh. Photosopped is the common term for digitally manipulating imagery, and I guess "Gimped it" might make people wonder what the heck you're talking about. Because there's so many different imaging packages out there, maybe there needs to be a new phrase born? Something that says, "I digitally manipulated it"...

I "diged it" (pronounced dijed) comes to mind...

If only it were that easy to start a catch phrase that would catch on...

---

### Post by King_Critter on 2009-11-06
I just say "Photoshopped" when I'm referring to digital image manipulation. Remember, if we use it enough it'll become a generic trademark. :P

---

### Post by hellocatfood on 2009-11-11
> **Johnsie said:**
> I'm a full time professional programmer. The main problem I have with GIMP is it's name. It would be pretty hard for people in business to take me seriously if I went around recommending that people install "The Gimp". Photoshop and Paintshop Pro have good, professional sounding names, but GIMP... We'll, that's got nothing to do with what the program actually does and is just not professional sounding enough. Yes, the letters G.I.M.P. stand for something related to graphics but that's not what people are going to pick up on. Give it a less stupid name and people might actually take it seriously.

I agree with you there. I'm sure it was a funny *in* joke at one point, but there's no way you can say to children in a classroom "open up gimp and start your work" and expect them to take you seriously.

I've learnt that the hard way

---

### Post by rattasongw on 2009-11-11
it *fails* when it doesn't meet your expectation.

---

### Post by johnboy1313 on 2009-11-11
I'm not really a big fan of the interface of gimp, but as for how it works, I have yet to have a real complaint with it.

---

### Post by kayosiii on 2009-11-13
> **Johnsie said:**
> I'm a full time professional programmer. The main problem I have with GIMP is it's name. It would be pretty hard for people in business to take me seriously if I went around recommending that people install "The Gimp". Photoshop and Paintshop Pro have good, professional sounding names, but GIMP... We'll, that's got nothing to do with what the program actually does and is just not professional sounding enough. Yes, the letters G.I.M.P. stand for something related to graphics but that's not what people are going to pick up on. Give it a less stupid name and people might actually take it seriously.

As you can see here there are many meanings for the word GIMP... [http://en.wiktionary.org/wiki/gimp](http://en.wiktionary.org/wiki/gimp)

It can mean... Neat; trim; delicate; slender; handsome; spruce; elegant.
It can also mean Gumption; spirit; ambition; vigor; pep. 

also To wrap or wind (surround) with another length of yarn or wire in a tight spiral, often by means of a gimping machine, 

and Any coarse or reinforced thread, such as a glazed thread employed in lacemaking to outline designs, or silk thread used as a fishing leader, protected from the bite of fish by a wrapping of fine wire.

---

### Post by BLTicklemonster on 2009-11-13
> **kayosiii said:**
> As you can see here there are many meanings for the word GIMP... [http://en.wiktionary.org/wiki/gimp](http://en.wiktionary.org/wiki/gimp)

It can mean... Neat; trim; delicate; slender; handsome; spruce; elegant.
It can also mean Gumption; spirit; ambition; vigor; pep. 

also To wrap or wind (surround) with another length of yarn or wire in a tight spiral, often by means of a gimping machine, 

and Any coarse or reinforced thread, such as a glazed thread employed in lacemaking to outline designs, or silk thread used as a fishing leader, protected from the bite of fish by a wrapping of fine wire.

Excellent.

As far as the interface, it's no worse than photoshop. Less clutter, actually. The beauty of it is, you're not locked in to the surrounding window, but have the entire desktop as your boundary. This way you can have the directory you're working on open full screen behind the gimp and drag and drop your work from there.
Count how much stuff photoshop has going on, then count what gimp has. Gimp's got what, 3 things as opposed to photoshop having what, 5 or 6 maybe 7?

After using gimp mostly for the past few years, I find photoshop to be clumsy. And I've used ps for a long time, and taken classes in using it.

But there's times when I have to use ps because it has better stuff, lol. At which time gimp unfortunately fails me...

---

### Post by hellocatfood on 2009-11-13
> **BLTicklemonster said:**
> After using gimp mostly for the past few years, I find photoshop to be clumsy. And I've used ps for a long time, and taken classes in using it.

I think that can be said of quite a lot of programs. If you use it for long enough then the alternatives will always be that little bit harder to get used to. That isn't to say that either GIMP or Photoshop has a clumsy interface, but there is always a period of adjustment when switching

---

### Post by RabbitWho on 2009-11-13
So far I haven't had a problem with it, everything I wanted to do I have been able to do... but it's taken me 5 times longer just because I'm not used to it. :)

---

### Post by AJB2K3 on 2009-11-13
I actually prefere the GNU Image program's fractured layout as I can dump all the tools to a small screen and have the canvas or work piece on a big monitor.
Heck if you were slightly clever you could have the tools on a touch screen seperate from the main screen without much work which i'm sure is impossible with ps.

---

### Post by Merk42 on 2009-11-13
> **AJB2K3 said:**
> I actually prefere the GNU Image program's fractured layout as I can dump all the tools to a small screen and have the canvas or work piece on a big monitor.
Heck if you were slightly clever you could have the tools on a touch screen seperate from the main screen without much work which i'm sure is impossible with ps.
So the only good way to use GIMP involves multiple monitors?

Also you can have all the tools on a separate screen in PhotoShop, at my old job where I had 2 monitors I did exactly that.

---

### Post by Exodist on 2009-11-13
> **Merk42 said:**
> So the only good way to use GIMP involves multiple monitors?

Also you can have all the tools on a separate screen in PhotoShop, at my old job where I had 2 monitors I did exactly that.


GIMPs layout is the same way Photoshops is on OSX. Only the windows version is one layout design.

---

### Post by kayosiii on 2009-11-13
> **Merk42 said:**
> So the only good way to use GIMP involves multiple monitors?

There is a hidden setting in the config files that will float your palettes always above the canvas (it breaks in some enviroments which is why it isn't in the ui).

You can set the canvas to full screen (F11) and the gimp is quite nice to work in. 

Without the setting the palettes will go behind when the canvas is clicked on. You can recall them by pressing [tab] twice...

I find GIMP quite usuable done this way.

---

### Post by dennis123123 on 2009-11-15
> **Johnsie said:**
> I'm a full time professional programmer. The main problem I have with GIMP is it's name. It would be pretty hard for people in business to take me seriously if I went around recommending that people install "The Gimp". Photoshop and Paintshop Pro have good, professional sounding names, but GIMP... We'll, that's got nothing to do with what the program actually does and is just not professional sounding enough. Yes, the letters G.I.M.P. stand for something related to graphics but that's not what people are going to pick up on. Give it a less stupid name and people might actually take it seriously.

I agree with you entirely. I brought up the subject a while back: [http://ubuntuforums.org/showthread.php?t=1141663](http://ubuntuforums.org/showthread.php?t=1141663)
but it wasnt received well by the community

---

### Post by graphius on 2009-11-16
> There is a hidden setting in the config files that will float your palettes always above the canvas

can you elaborate?

---

### Post by mcduck on 2009-11-18
> **kayosiii said:**
> There is a hidden setting in the config files that will float your palettes always above the canvas (it breaks in some enviroments which is why it isn't in the ui).

You can set the canvas to full screen (F11) and the gimp is quite nice to work in. 

Without the setting the palettes will go behind when the canvas is clicked on. You can recall them by pressing [tab] twice...

I find GIMP quite usuable done this way.

It's not hidden, it's in the Gimp preferences dialog. Just go to Edit->Preferences and you'll have two dropboxes called "Window Manager Hints" that allow you to change this setting separately for toolboxes and other docks.

---

### Post by kayosiii on 2009-11-18
> **mcduck said:**
> It's not hidden, it's in the Gimp preferences dialog. Just go to Edit->Preferences and you'll have two dropboxes called "Window Manager Hints" that allow you to change this setting separately for toolboxes and other docks.

That is not what I am talking about... If that works for you though great :)... (it doesn't work for me - I am on KDE that might be the problem - it keeps the palettes on top but not when I go into fullscreen mode)

What worked for me was adding the following line to the end of my ~/.gimp-2.6/gimprc 

```
(transient-docks yes)
```

---

### Post by laststop on 2009-11-18
How about export to MNG? Still fails?

I would also like to see export to APNG.

---

### Post by San Yad on 2010-09-02
Hi All !

I am using  gaussview03 for Gaussian. When I make the input file of the interaction of one of the Oxygen of Praseodymium (Pr) interact with One of the hydrogen of histidine.   I can model the interaction of Oxygen ( Pr-O) and N-H of histidine and make the input (.gjf) file.  This input file I submit the to get the output file.  I get the output file within seconds and in output file there is no RHF value. This suggest me that there is no interaction in between O and H or may be I am missing some important parameter to select while making then input file?

Can anyone please suggesting me what is the problem in this output file?

regards,
San

---

### Post by ccc123 on 2010-09-03
I think it is the best, though I did take a while to get used to the unusual multi-window interface and menu set up.

---

### Post by PayPaul on 2011-10-10
Aside from the lack of adjustment layers... that's been said and it's sad, I have to say the latest stumbling block is the convoluted way to resize images. It seems to require multiple steps and that scale image function no where near replaces how one does it in PS. I tried one and it came out horribly pixelated. I was looking for another program to resizing of my images. Ran across PHatch but it's confusing with all its emphasis on "actions" and I can't find any adequate documentation on how to open up images in it and resize. I'm very upset with my latest attempt to resize a photo in GIMP and so I'll have to keep looking for something else to do that job.

---

### Post by thatguruguy on 2011-10-10
> **PayPaul said:**
> Aside from the lack of adjustment layers...  that's been said and it's sad, I have to say the latest stumbling block  is the convoluted way to resize images. It seems to require multiple  steps and that scale image function no where near replaces how one does  it in PS. I tried one and it came out horribly pixelated. I was looking  for another program to resizing of my images. Ran across PHatch but it's  confusing with all its emphasis on "actions" and I can't find any  adequate documentation on how to open up images in it and resize. I'm  very upset with my latest attempt to resize a photo in GIMP and so I'll  have to keep looking for something else to do that job.

Wait a minute.  What steps are you going through to try to resize your image?

---

### Post by prokoudine on 2011-10-11
> **thatguruguy said:**
> Wait a minute.  What steps are you going through to try to resize your image?

Well, actually the old samplers suck badly. Try resizing a screenshot with some text at 8-10px font size and see for yourself :) So the roundtrip is:

1. Use gaussian blur with px amount that is source-width/final-width.
2. Scale your image down with linear interpolation.
3. Use either of the sharpening methods.

There are some pretty cool new samplers available in GEGL, but it's going to take some time till GIMP uses them by default.

---

### Post by BLTicklemonster on 2011-10-11
Parts of Pay Paul's post reads as a complaint that "GIMP didn't do a good enough job of copying Photo Shop".

I use phatch, it's confusing as heck, but once you get the hang of it, days have passed... I mean, it's really useful.

---

### Post by ofnuts on 2011-10-11
> **prokoudine said:**
> Well, actually the old samplers suck badly. Try resizing a screenshot with some text at 8-10px font size and see for yourself :) So the roundtrip is:

1. Use gaussian blur with px amount that is source-width/final-width.
2. Scale your image down with linear interpolation.
3. Use either of the sharpening methods.

There are some pretty cool new samplers available in GEGL, but it's going to take some time till GIMP uses them by default.
This is a known trick also used to resize photos and necessary whatever the scaling algorithm, when you have patterns about the  size of the scaling factor in the picture (roof tiles...), bricks or bricks joints. This is cause by spatial frequency folding. Using the pre-blur is the cure but indeed loses some perceived sharpness in the final image, so people won't do it blindly...

---

### Post by prokoudine on 2011-10-11
> **ofnuts said:**
> This is cause by spatial frequency folding.
I'm giving you a medal of honor for providing a comment that makes me want to dig deeper into the scientific side of this deeper. How about that? :)

---

### Post by galacticaboy on 2011-10-11
It is just not basic enough for me. I need something basic like MS Paint, so I use Pinta.

---

### Post by ofnuts on 2011-10-11
> **prokoudine said:**
> I'm giving you a medal of honor for providing a comment that makes me want to dig deeper into the scientific side of this deeper. How about that? :)I'll get the medal when you (or anothert eminent Gimp developer) use that knowledge to add a checkbox 'Avoid aliasing' in Image/Scale and the layer Scale tool :)

---

### Post by The Sorrow on 2011-10-12
Ive heard many artists say gimp is very manual and its methods are rather ridiculous compared to photoshop.

---

### Post by ofnuts on 2011-10-12
> **The Sorrow said:**
> Ive heard many artists say gimp is very manual and its methods are rather ridiculous compared to photoshop.Gimp is a mechanic's shop. It comes with a few basic tools, but you will find a lot of tools around to put on the shelves and you can make your own. No two people use the same Gimp...

---

### Post by apo1l on 2011-10-17
I'm still learning Gimp.  One thing I can say, don't compare Gimp with other photo softwares.  They are all different.  And you should use what best suits you.

---

### Post by Dry Lips on 2011-10-17
I think that it is ludicrous to have a thread where the words &#8220;GIMP&#8221; and &#8220;FAILURE&#8221; appear together 
in the title. Photoshop CS5 extended costs $999 if you live in the US, and if you live in other parts 
of the world, the prices are twice as high.
 
Gimp is totally free and is a very powerful tool in the right hands. Of course we would all like it to be
more advanced and have more features, but I think it is a remarkable success when you think about
the fact that it is a program developed on a non-commercial basis.

Do you want it to become better? Well, then I would recommend you to consider a donation: [http://www.gimp.org/donating/](http://www.gimp.org/donating/)

---

### Post by aeronutt on 2011-10-17
> **PayPaul said:**
> Aside from the lack of adjustment layers... that's been said and it's sad, I have to say the latest stumbling block is the convoluted way to resize images. It seems to require multiple steps and that scale image function no where near replaces how one does it in PS. I tried one and it came out horribly pixelated. I was looking for another program to resizing of my images. Ran across PHatch but it's confusing with all its emphasis on "actions" and I can't find any adequate documentation on how to open up images in it and resize. I'm very upset with my latest attempt to resize a photo in GIMP and so I'll have to keep looking for something else to do that job.

There used to be a plugin to Nautilus that worked quite well (that I believed used imagemagik)...but alas, no more.

---

