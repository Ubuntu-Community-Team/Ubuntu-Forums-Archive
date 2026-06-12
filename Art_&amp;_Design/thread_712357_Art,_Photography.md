---
title: "Art, Photography"
date: 2008-03-01
forum: Art &amp; Design
---

### Post by ReBcWoo on 2008-03-01
Hello!

I am an intern for a photographer who is teaching me all she knows through Photoshop and LIghtroom... 

I am trying to learn GIMP and Picasa (on my PC) but am having a hard time getting out of them what I get out of Photoshop and LIghtroom.

I have the basics down for GIMP but, for example, I am having a hard time adjusting the exposure of photos and that sort of thing.... 

Im just wondering if there is a Photographer or Graphic designer out there that uses GIMP and Picasa that can suggest ways to make this learning easier or steer me in a better direction...

Also, Photoshop and Lightroom have "actions"... I know that "actions" are the easy way to get things done but I would like to know if GIMP and/or any other program has those options and how to get them.

oh boy...

thanks for reading

---

### Post by Sam Lars on 2008-03-01
Well there is "[Gimpshop]("http://www.gimpshop.com")," which is basically the Gimp set up to look more like Photoshop.
Another download link if you want to avoid the link from the site above, which points to Rapidshare:
[http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)

---

### Post by ReBcWoo on 2008-03-01
Thank you! I will check those out!

---

### Post by kayosiii on 2008-03-02
You might also want to check out Digikam and Krita.... Both these support 16 bit precision which is a boon if you are working from raw images. You should be able to apt-get both of these. While we are concidering raw - if you doing that you might have some success with rawstudio. Oh and make sure you install the ufraw plugin for gimp.

Beyond that Gimp doesn't really use a photographers vocabulary (last time I used photoshop it didn't either - apart from raw developer, Lightroom does though). With specific regards to exposure - learn to use the curves and levels tools - these are your friends.

As for actions Gimp doesn't do this yet - but bear with me.... What gimp supports is script-fu which enables you to write scripts in a variety of scripting languages (lisp, python and perl I know are supported). This is harder to use but more powerful than actions.  You can also dynamically assign keyboard shortcuts which can speed up workflow if you have to do a task repeditively

I hope that all helps

---

### Post by jtclicker on 2008-03-02
you might also want to check out[ lightzone]("http://www.lightcrafts.com/support/try/") 
This is a commercial app that is available as a free unsupported beta for linux. It has similar functionality to lightroom - kinda - but it fills ths gap for me. I'm more concerned about the lack of noise ninja or photozoom! 
But I recommend you try lightzone. I too am coming from a pc background into ubuntu - but I'm keeping the dual boot for when I need th epc apps

---

### Post by ShodanjoDM on 2008-03-02
Don't forget to check this site: [http://registry.gimp.org/](http://registry.gimp.org/) it has many useful plugins and scripts.

And since you've already familiar with Photoshop, you might find GIMP shortcuts confusing. So here's a tip:

Copy the file  ps-menurc in directory /etc/gimp/2.0/ to your .gimp-2.4 folder in your home directory and rename it to menurc

Or use this command:

```
cp /etc/gimp/2.0/ps-menurc ~/.gimp-2.4/menurc
```

The next time you open GIMP, the shortcuts will be similar to the Photoshop shortcuts.

---

### Post by lyceum on 2008-03-02
I was lost in GIMP until I picked up Beginning GIMP: From Novice to Professional. The author's site is updated with the changes in GIMP, and the book is really easy to read.

[http://gimpbook.com/gimpchanges.html](http://gimpbook.com/gimpchanges.html)

---

### Post by ImpressMe on 2008-03-02
> **lyceum said:**
> I was lost in GIMP until I picked up Beginning GIMP: From Novice to Professional. The author's site is updated with the changes in GIMP, and the book is really easy to read.

[http://gimpbook.com/gimpchanges.html](http://gimpbook.com/gimpchanges.html)

I read it. It is because there is nothing in it... because GIMP is such a small and poor alternative to Photoshop. I jumped from GIMP to Photoshop, and I will never consider GIMP again unless it gets support for 16-bit, non-destructive layers, LAB mode... and much much more. Take a look at Pixel, btw.

**If you want an alternative to Lightroom (and especially if you work with RAW files (16-bit!), then take a look at [RawTherapee]("http://www.rawtherapee.com"). It opens RAW, JPG, PNG and TIFF files.**

Krita is too slow and clumsy.

Linux is not the greatest thing for a photographer. Non existant or poor support for colour and monitor profiles. I havent found a single viewer for Linux that supports **monitor** profiles, but at least GIMP does that now.

---

### Post by dmn_clown on 2008-03-02
> **ImpressMe said:**
> Linux is not the greatest thing for a photographer. Non existant or poor support for colour and monitor profiles. I havent found a single viewer for Linux that supports **monitor** profiles, but at least GIMP does that now.

A combination of UFRaw and Cinepaint work nicely for me, so I have to disagree with the assessment that Linux is not the greatest for photography, please don't base everything off the poor features of the GIMP.

---

### Post by jcornuz on 2008-03-02
Hi there,

Check my blog (down there). Its theme is Linux & Photography (RAW and 16bits processing, color management, high quality printing, etc).

Hope this will help... and show us some pics :-)

Take care,

Joel

---

### Post by AJB2K3 on 2008-03-03
> **ImpressMe said:**
> I read it. It is because there is nothing in it... because GIMP is such a small and poor alternative to Photoshop. I jumped from GIMP to Photoshop, and I will never consider GIMP again unless it gets support for 16-bit, non-destructive layers, LAB mode... and much much more. Take a look at Pixel, btw.

Rubbish, I have started using the raw file format and find ufraw+gimp is fine.
> **ImpressMe said:**
> 
**If you want an alternative to Lightroom (and especially if you work with RAW files (16-bit!), then take a look at [RawTherapee]("http://www.rawtherapee.com"). It opens RAW, JPG, PNG and TIFF files.**

Krita is too slow and clumsy.

Or lightzone
> **ImpressMe said:**
> 
Linux is not the greatest thing for a photographer. Non existant or poor support for colour and monitor profiles. I havent found a single viewer for Linux that supports **monitor** profiles, but at least GIMP does that now.

Agreed

[IMG]http://i51.photobucket.com/albums/f352/AJB2K3/sox/queen.png[/IMG] Taken in fuji raw (raf)format and saved in gimp.

---

### Post by jtclicker on 2008-03-03
There is another thing you need to consider, and the reason why I have just started using ubuntu... linux is the ONLY place where you have 64 bit access to ram. My photo montages start out at 1.2gig. Try that in a 32 bit system and you quickly get bored. I can't wholely use linux as there is some stuff I need, but cinepaint works for when the constructions get too big - but I still need windows for much of my processes

---

### Post by ReBcWoo on 2008-03-03
WOW! Ton of information! Thank you so much! 

I believe I will have a load of questions as I look into all of these different programs so until then...

---

### Post by stani on 2008-03-03
> **ReBcWoo said:**
> 
Also, Photoshop and Lightroom have "actions"... I know that "actions" are the easy way to get things done but I would like to know if GIMP and/or any other program has those options and how to get them.

Hi,
I am developing an new application "Phatch" (=PHoto & bATCH) which is built upon the concept of 'actions':
[http://photobatch.stani.be](http://photobatch.stani.be) > see the 'free download' link below for an ubuntu installer

There is quite a lot of documentation here:
[http://photobatch.wikidot.com](http://photobatch.wikidot.com)

You can follow a thread on this forum about it:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

It will be available in Hardy from the universe repositories.

Let me know if it is useful for you.

Stani

---

### Post by dmn_clown on 2008-03-03
> **AJB2K3 said:**
> Rubbish, I have started using the raw file format and find ufraw+gimp is fine.

You lose color data and fine details by using the gimp, as in all conversions from 16bpp to 8bpp.

---

### Post by jtclicker on 2008-03-04
technically, yes, 16 bit is better than 8 bit, but the loss is more apparent in BW  to colour, so it is a case of try it and see. But like you, I tend to stay in 16 bit all the way and only go down to 8 bit to print. I know many highly respected large format workers who only scan in 8 bit (colour) and these guys are obsessive about quality

---

### Post by mrsudo on 2008-03-06
i personally use gimpshop.  takes getting used to after using photoshop and fireworks on windows but i think its worth it

---

### Post by Aphorism on 2008-03-09
Go with jcornuz's blog for the colour temp adjustments.  His blog is terrific.

As you are probably already doing -- shoot raw.  dcraw is the standard from the CLI for getting into those proprietary formats.  You *must* have access to those bits outside the visible spectrum when it comes to adjusting your exposure details etc.

ufraw has come a long way.  It builds upon the dcraw work.

Blender also has a simple and complex photosensor node in the nodal compositor.  Convert to a greater than crippling 8 bits per channel colour depth using dcraw and plug your tiff into the photosensor node.  If you wish to retain the bits per channel, export one tiff for viewing and one openexr for keeping the data intact.  Use an SVN Blender for best results.

Imagemagick is also top shelf at handling >8bpc colour depths.  In my experience, it has some of the best algorithms available.  Use 'display' to get crude access to the toolset.  Ubuntu's ImageMagick is hideously out of date, so you would want to compile your own from SVN.

Better still, use that light meter and properly expose those shots so that you are limiting the amount of twiddling you are doing in post.  The 'fix it in post'-itus is a painful and costly bit of fun.  Not to mention that if you do any digital adjusting above and beyond hue / saturation / contrast, you head down the wonderful road of degraining and regraining.

And to the misinformers out there with the 16BPC and 8BPC knowledge -- yikes.  You *always* lose information going from RAW to a standard 8BPC truecolour display.  The human eye can only see approximately 17.3 million colours.  The extra bits are purely there for data and doing exactly what the poster was asking.  If you are converting from RAW to a greater than 8BPC *linear* image, your image will be murky when viewed in a standard viewer because the data is now being stuck on a linear scale.  There is no more visible detail there, but rather non-visible.  If you are looking at a linear 16 BPC image, it might look like more detail, but you are also not properly exposed which is why everything will appear muddy / murky as you are not in a properly curved visible spectrum.  To quote Coffin's dcraw page:  > Why is 16-bit output dark / unreadable?
    If you want pretty pictures straight out of dcraw, stay with 8-bit output. 16-bit linear output is the best raw material for professional image editors such as Photoshop and CinePaint, but it's no good for most image viewers.

In short, convert to your >8BPC display and properly generate a truecolour image back in the standard 24 bit colourdepth after post processing.  If it is all too confusing, use dcraw or ufraw to get you to a properly exposed 24 bit image from your raw sources.  **Do not** leave them in 16 bits per channel linear formats.  Yikes.

Sincerely,
TJS

---

### Post by jedimasterk on 2008-05-02
> **Aphorism said:**
> Go with jcornuz's blog for the colour temp adjustments.  His blog is terrific.

As you are probably already doing -- shoot raw.  dcraw is the standard from the CLI for getting into those proprietary formats.  You *must* have access to those bits outside the visible spectrum when it comes to adjusting your exposure details etc.

ufraw has come a long way.  It builds upon the dcraw work.

Blender also has a simple and complex photosensor node in the nodal compositor.  Convert to a greater than crippling 8 bits per channel colour depth using dcraw and plug your tiff into the photosensor node.  If you wish to retain the bits per channel, export one tiff for viewing and one openexr for keeping the data intact.  Use an SVN Blender for best results.


Imagemagick is also top shelf at handling >8bpc colour depths.  In my experience, it has some of the best algorithms available.  Use 'display' to get crude access to the toolset.  Ubuntu's ImageMagick is hideously out of date, so you would want to compile your own from SVN.

Better still, use that light meter and properly expose those shots so that you are limiting the amount of twiddling you are doing in post.  The 'fix it in post'-itus is a painful and costly bit of fun.  Not to mention that if you do any digital adjusting above and beyond hue / saturation / contrast, you head down the wonderful road of degraining and regraining.

And to the misinformers out there with the 16BPC and 8BPC knowledge -- yikes.  You *always* lose information going from RAW to a standard 8BPC truecolour display.  The human eye can only see approximately 17.3 million colours.  The extra bits are purely there for data and doing exactly what the poster was asking.  If you are converting from RAW to a greater than 8BPC *linear* image, your image will be murky when viewed in a standard viewer because the data is now being stuck on a linear scale.  There is no more visible detail there, but rather non-visible.  If you are looking at a linear 16 BPC image, it might look like more detail, but you are also not properly exposed which is why everything will appear muddy / murky as you are not in a properly curved visible spectrum.  To quote Coffin's dcraw page:  

In short, convert to your >8BPC display and properly generate a truecolour image back in the standard 24 bit colourdepth after post processing.  If it is all too confusing, use dcraw or ufraw to get you to a properly exposed 24 bit image from your raw sources.  **Do not** leave them in 16 bits per channel linear formats.  Yikes.

Sincerely,
TJS



So what do we use now that Cinepaint is no longer in Ubuntu Hardy. How do we get 16 bit support?. What other alternative do we have except the dreaded Wine and Photoshop?.

---

### Post by Aphorism on 2008-05-03
> jedimasterk:  So what do we use now that Cinepaint is no longer in Ubuntu Hardy. How do we get 16 bit support?. What other alternative do we have except the dreaded Wine and Photoshop?

Ultimately it depends on what you wish to accomplish.  Your options might fall into the following categories:

[LIST=1]
[*]Manipulate RAW files into useful formats - The one and only [dcraw]("http://en.wikipedia.org/wiki/Dcraw") will do this for you.  Export to a linear TIFF or a standard 24 bit TIFF / JPG.
[*]Whole Image Adjustments / Exposure - Consider using [UFRaw]("http://en.wikipedia.org/wiki/Ufraw") or [Rawstudio]("http://en.wikipedia.org/wiki/Rawstudio").  These tools will easily manage your photos and allow you to do a number of whole image adjustments whilst remaining within the greater than eight bits per channel scale.  Once you achieve bliss, export the result to a standard eight bits per channel output in either a lossless or lossy format of your choosing.
[*]Partial or Whole Image Adjustments - [Imagemagick]("http://en.wikipedia.org/wiki/Imagemagick") will handle an extreme range of bit depths.  It offers a complete adjustment tool set from the command line.  The graphical user frontends should at least allow you to experiment with a look before diving in full force.
[*]Compositing / Image Manipulation - Once again, consider [Blender]("http://en.wikipedia.org/wiki/Blender_(software)")'s nodal editor.  Start with your basic "Image" node and "Viewer" node.  Drop in a series of adjustment nodes (including two varieties of photosensor simulators for the linear 16 bit output as obtained via dcraw) and get to where you want.
[/LIST]

IF you are choosing to do a series of masking raster operations using a lasso styled tool, [Cinepaint]("http://en.wikipedia.org/wiki/Cinepaint") is probably the only option to the best of my knowledge.  That said, Imagemagick can do the job as well, but to the best of my knowledge, a full featured GUI has yet to be created.  There are several GUIs available, but none harness the full power of Imagemagick.

GIMP has finally begun CEGL integration as of 2.5.  That *should* mean that greater bit depths are very close at hand.  However, judging from what I have read of CEGL, the architecture isn't nearly as versatile as Blender's, so you will still be trapped within a limited colour depth per channel.  Blender, aiming to be professional grade, supports an infinitely large bit depth IIRC.  Handy if you wish to experiment with 10 stop bracketing or some other HDRI techniques.

I also forgot about Krita.  It supports differing depths and is pretty solid for twiddling areas / artistic embellishments.

As always, consider compiling these apps for yourself as the repository version, by the time Ubuntu releases, are usually a little behind the curve.

PS:  Bear in mind that *16 bit* is a tad of a misnomer.  Almost every single application in Ubuntu supports images of 16 bits in terms of overall depth.  16 bits per channel is another creature, and in fact, 16 bpc is extremely limited when one starts discussing visual effect environments.  Further still, there are no professional grade cameras (to the best of my knowledge) that allow a shooter to shoot in 16 bits per channel.  Both the Canon 1D and 1Ds as well as the Nikon D3 shoot at 14 bpc.

I sincerely hope this dribbling helps...
TJS

---

