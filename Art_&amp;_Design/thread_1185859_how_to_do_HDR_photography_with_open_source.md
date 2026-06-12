---
title: "how to do HDR photography with open source?"
date: 2009-06-12
forum: Art &amp; Design
---

### Post by perroazul on 2009-06-12
I have tried to do it manually with the GIMP but I'm not really satisfied with the result. Does anybody know of a program for making HDR compositions from several photographies?
tutorials?
thanks

---

### Post by Michael.Godawski on 2009-06-14
hi,

I recently wondered about the same issue. 

And found these two applications:

[LIST]
[*]**ufraw** to open raw files and
[*]**Qtpfsgui** (what a name!) for creating hdr images
[/LIST]
Both can be installed via the terminal:
```
sudo apt-get install ufraw qtpfsgui
```

Just started with digital photography (Nikon D40 ;)), so I am not that much into it by now.

---

### Post by perroazul on 2009-06-15
thanks Michael
Qtpfsgui's interface has improved a lot since the last time I tried using it (about a year ago). This time I was able to produce an interesting looking results with a few clicks while the last time I couldn't get it to work. I will definitely explore its many options :)

---

### Post by unutbu on 2009-06-15
According to this page, the pano-stitcher Hugin can also do HDR:
[http://wiki.panotools.org/Hugin_Stitcher_tab](http://wiki.panotools.org/Hugin_Stitcher_tab)

I know hugin has an option to create multi-layer tiffs. You can then load it into GIMP and manually create layer masks to blend the images. According to the webpage above, Hugin also has options to attempt this automatically.

The hugin package is in the official repos.

I've never used qtpfsgui, so I don't know how the results compare.

---

### Post by cubeist on 2009-06-16
It's hard to get good results in gtpfsgui.  To improve on the default tonemapping options you can try the Fattal plus Drago method.

There is a full tutorial on this somewhere on the web, but in short...
 - First tonemap using default Fattal settings, then create second tonemap using Dragal.
 - Second, open both images in gimp as layers, put Drago on the bottom, then overlay the Fattal image on top at about 70% (or however you like it).
 - Third, merge your visible layers back into one image, or save as an xcf to preserve the two layers.

Post your results if you get a good one.  I have yet do make a great HDR on linux...

---

### Post by perroazul on 2009-06-27
@cubeist: thanks for the instructions. I followed them, and I'm posting the result as a reference.

---

### Post by tgalati4 on 2009-06-27
Hugin works great for stitching photos.  I have gotten good results with manual control points.  For exposure, Hugin has decent tools for correcting exposure across a panorama.  An HDR is a special panorama with different exposures for the same scene.  Hugin can handle 48-bit color space and has special exposure blending filters, but I haven't tried any HDR's with it.

It would be interesting to see the exposure series of the fountain so we could see the over and underexposure range.

I still find it fascinating that our eyes can capture ~18 stops of light, yet digital photography is pressed to capture 6.

Let us know what works.

---

### Post by AJB2K3 on 2009-06-28
I use qtpfsgui and gimp in the following steps.
9 out of 10 people prefer the less is more look.

1, minor colour alteration in G.I.M.P.
2, Create HDR in QTPFSGUI and save.
3, create a tone map using mathiuk formula and save.
4, create a tone map using fattel formula and save.
5, open mathiuk file in G.I.M.P.
6, Open fattel file in G.I.M.P and paste as a new layer into the mathiuk file,
7, set layer mode to Multiply.
8, merge layers
9, adjust finial colours
10, save image,
11, upload to photo bucket,
12 Post up on this forum as a thank you to everyone who helped me out.

[IMG]http://i703.photobucket.com/albums/ww40/Adam_Bryant/Building/gateuf.jpg[/IMG]

---

### Post by cubeist on 2009-06-28
> **perroazul said:**
> @cubeist: thanks for the instructions. I followed them, and I'm posting the result as a reference.

I think it is a good result, but the whites are a little bright.

@ AJB2K3:
Fattal and Mantiuk, interesting, I have never seen this combo before, but it does give a nice subtle result.  Good job.

If I can ever find more hours in the day I will write a gimp plugin for both methods.

---

### Post by AJB2K3 on 2009-06-29
> **cubeist said:**
> I think it is a good result, but the whites are a little bright.

@ AJB2K3:
Fattal and Mantiuk, interesting, I have never seen this combo before, but it does give a nice subtle result.  Good job.

If I can ever find more hours in the day I will write a gimp plugin for both methods.

Thanks, it was a tip I found on the qtpfsgui site as I couldn't get a good composition with the single filters.

---

### Post by perroazul on 2009-06-29
@ AJB2K3: thanks. I tried Fattal + Mantiuk + Multiply layer mode (first time I use a non-normal layer mode with GIMP) and got the results you can see below. 
@ cubeist: yes thank you, I'm not satisfied with those results either. 

wow! with results so different it is clear that finding a good set of options is not an easy task.
 
P.S. I'm also posting the result you get when you combine the 3 auto-bracket photographies that you obtain with a digital camera, using layers and Grayscale layer masks with GIMP: [IMG]http://www.panoramio.com/photos/medium/23446142.jpg[/IMG]

---

### Post by unutbu on 2009-06-30
perroazul, would you post the 3 auto-bracketed images so we can play with them? Down-scaled versions of the images would be fine.

---

### Post by perroazul on 2009-06-30
definitely :)

---

### Post by decoherence on 2009-06-30
The auto-bracketted pictures aren't the same size....

---

### Post by AJB2K3 on 2009-06-30
> **perroazul said:**
> @ AJB2K3: thanks. I tried Fattal + Mantiuk + Multiply layer mode (first time I use a non-normal layer mode with GIMP) and got the results you can see below. 
@ cubeist: yes thank you, I'm not satisfied with those results either. 

wow! with results so different it is clear that finding a good set of options is not an easy task.
 
P.S. I'm also posting the result you get when you combine the 3 auto-bracket photographies that you obtain with a digital camera, using layers and Grayscale layer masks with GIMP: [IMG]http://www.panoramio.com/photos/original/23446142.jpg[/IMG]

Nice try but like me you have the halo effect.
There is a solution by using th original 0ev file as a mask but I haven't worked it out.

---

### Post by mcduck on 2009-06-30
Qtpfsgui is absolutely great. :D

I've recently found HDR photographing and I definitely like the idea behind this a lot. Kind of capturing what's really there instead of what your camera can see, and producing images closer to what your eyes can see, or even taking it further for some kind of hyper-realistic look..

Now I only need to find something that's worth shooting and stays still for long enough time for me to take a couple of photos (my cheap DSLR doesn't even have auto-bracketing..)

[IMG]http://pontusschonberg.net/images/forest-2.jpg[/IMG]
This one's made with Fattal mapping, I also made a more "normal" version but in the end like this better, even though there's a some glow visible..

[IMG]http://pontusschonberg.net/images/vuokot.jpg[/IMG]
This is Fattal-mapped image layered together with one of the normal shots.

[IMG]http://pontusschonberg.net/images/sanfrancisco.jpg[/IMG]
This is actually a pseudo-HDR made from a single RAW image (I had no tripod with me). The original photo looked very dull with completely grey sky, but with some Fattal magick made it usable..

---

### Post by cubeist on 2009-06-30
> **perroazul said:**
> @ AJB2K3: thanks. I tried Fattal + Mantiuk + Multiply layer mode (first time I use a non-normal layer mode with GIMP) and got the results you can see below. 
@ cubeist: yes thank you, I'm not satisfied with those results either. 

wow! with results so different it is clear that finding a good set of options is not an easy task.
 
P.S. I'm also posting the result you get when you combine the 3 auto-bracket photographies that you obtain with a digital camera, using layers and Grayscale layer masks with GIMP: [IMG]http://www.panoramio.com/photos/original/23446142.jpg[/IMG]

This is a much, much, better result, I think I have found my new favorite.  Forget Fattal and Drago, the Fattal + Mantiuk + Multiply gives the best result.

Also @ Perroazul:  For your bracketed shots, try to have you darkest photo very dark...For example, the sky should be deep dark blue.  On a bright sunny day this is not always easy.  First try shooting at your highest shutter speed, probably 1/1000th or 1/2000th of a second for most digital cameras, if it is still fairly bright, you could buy a 1 or 2-stop filter.  These can be found dirt cheap at used camera stores and they will filter out a lot of the light.

---

### Post by AJB2K3 on 2009-06-30
> **mcduck said:**
> 
[IMG]http://pontusschonberg.net/images/sanfrancisco.jpg[/IMG]

What's the biggest resolution you can go with this one?
Although its not my style (yet) its very artistic)

Please can everyone who's been bitten by the HDR bug join [http://photography4allforum.co.uk]("http://photography4allforum.co.uk/phpbb/index.php") to show theres off.

---

### Post by mcduck on 2009-06-30
> **AJB2K3 said:**
> What's the biggest resolution you can go with this one?
Although its not my style (yet) its very artistic)


Thanks. :)

I have that one in 1536 x 1017 resolution.

It was just some random shot I took in San Fransisco, seemed like a good one to try how much turning single shot into pseudo-HDR can do.

---

### Post by AJB2K3 on 2009-06-30
Can I get a big copy and the source file emailed to me?

---

### Post by mcduck on 2009-06-30
> **AJB2K3 said:**
> Can I get a big copy and the source file emailed to me?

Sure, just send me a private message with your e-mail address (as I don't think it's possible to attach files to private messages on these forums).

Do you want the .exr or the original .nef file?

---

### Post by perroazul on 2009-06-30
> **cubeist said:**
> 
Also @ Perroazul:  For your bracketed shots, try to have you darkest photo very dark...For example, the sky should be deep dark blue.  On a bright sunny day this is not always easy.  First try shooting at your highest shutter speed, probably 1/1000th or 1/2000th of a second for most digital cameras, if it is still fairly bright, you could buy a 1 or 2-stop filter.  These can be found dirt cheap at used camera stores and they will filter out a lot of the light.

:) I love this forum so much :)

---

### Post by perroazul on 2009-06-30
> **mcduck said:**
> 
It was just some random shot I took in San Fransisco, seemed like a good one to try how much turning single shot into pseudo-HDR can do.

@mcduck: do you use a Normal layer mode or as we just discovered Multiply mode or any other layer mode?. I like the shot of the flowers also :)

> **AJB2K3 said:**
> 
Nice try but like me you have the halo effect.
There is a solution by using th original 0ev file as a mask but I haven't worked it out.

I'll try doing that and will post the results if I get anything interesting.

---

### Post by mcduck on 2009-07-01
> **perroazul said:**
> @mcduck: do you use a Normal layer mode or as we just discovered Multiply mode or any other layer mode?. I like the shot of the flowers also :)

I have absolutely no idea what layer modes and opacities I have used in which pictures, I usually just try every one that might work for the image I'm editing and then pick the one I like most.

Could be Multiply, Overlay, or possibly even Hard Light or Soft Light (Normal is not likely, but still possible)..

While having some set steps to follow when working is often helpful, I've found that all my best pictures are the ones that result from random messing around with different tools.. :D

---

### Post by mcduck on 2009-07-06
Here's one more image, my neighbors were making a lot of noise last night keeping me awake so I used the time for my benefit and took a couple of shots from my balcony..

7 exposures, with shutter times between 0,25s and 15s. I used Fattal and Mantiuk algorithms, combined them with Multiply and then added one of the original shots with Screen blending at 15% to get back some of the original lighting.

By the way, as I'm not that good with cameras I use the Aperture program of my camera, so instead of having to deal with shutter times I can just adjust the EV for different exposures..

---

### Post by AJB2K3 on 2009-07-06
ouu I like that.=D>=D>=D>

---

### Post by mcduck on 2009-07-06
Thanks. I quite like the contrast of color between orange light from sodium vapor street lights and the dark blue sky. :)

---

### Post by cubeist on 2009-07-06
@Mcduck... very nice!

Have any of you tried enfuse yet.  It is built into the latest hugin (or you can use it from the command line) and while it is not a true HDR, it does give a nice result.

Here is some info:
[http://wiki.panotools.org/Enfuse](http://wiki.panotools.org/Enfuse)

and here is a sample from a hike I took this weekend:

---

### Post by perroazul on 2009-07-06
@Mcduck: fantastic colors. it reminds me of the work of some modern painter... don't remember his name. 
 
@cubeist: lovely composition :)
I'm checking huging now to see how enfuse works

---

### Post by _sAm_ on 2009-07-07
This is strange; I wanted to try Qtpfsgui and did "sudo aptitude install qtpfsgui"(on latest Ubuntu).

Then I open the program from the menu, press "New Hdr..." > "Load Images" > "All formats" and browse to the folder with my jpg - but no pictures are shown? Nautilus can see them. 

I tried to change "All formats" to only jpeg, but still no pictures.

This is a folder with jpeg from Nikon D70 and D90, and my user owns them(and Qtpfsgui cant see my NEF files from the same folder). 

If I open the jpg files in Gimp and save them as tiff I can open them in Qtpfsgui(but then the exif data is removed).

---

### Post by AJB2K3 on 2009-07-07
> **_sAm_ said:**
> This is strange; I wanted to try Qtpfsgui and did "sudo aptitude install qtpfsgui"(on latest Ubuntu).

Then I open the program from the menu, press "New Hdr..." > "Load Images" > "All formats" and browse to the folder with my jpg - but no pictures are shown? Nautilus can see them. 

I tried to change "All formats" to only jpeg, but still no pictures.

This is a folder with jpeg from Nikon D70 and D90, and my user owns them(and Qtpfsgui cant see my NEF files from the same folder). 

If I open the jpg files in Gimp and save them as tiff I can open them in Qtpfsgui(but then the exif data is removed).

Have you reported this to the QTPFSGUI team?

btw all mine are saved as .jpg not .jpeg.

---

### Post by _sAm_ on 2009-07-07
*.jpg/jpeg is the same type. 

I have not reported it, there must be something wrong with the version for Ubuntu 64b. Are you using 32b?

---

### Post by mcduck on 2009-07-07
> **_sAm_ said:**
> This is strange; I wanted to try Qtpfsgui and did "sudo aptitude install qtpfsgui"(on latest Ubuntu).

Then I open the program from the menu, press "New Hdr..." > "Load Images" > "All formats" and browse to the folder with my jpg - but no pictures are shown? Nautilus can see them. 

I tried to change "All formats" to only jpeg, but still no pictures.

This is a folder with jpeg from Nikon D70 and D90, and my user owns them(and Qtpfsgui cant see my NEF files from the same folder). 

If I open the jpg files in Gimp and save them as tiff I can open them in Qtpfsgui(but then the exif data is removed).

Opening .NEF files in the Linux version isn't working for me either. If I need to make pseudo-hdr from single raw images I have to do it on Mac. But JPG definitely shoud work.. If your files have .jpeg extension try renaming them to .jpg.

---

### Post by mcduck on 2009-07-07
> **cubeist said:**
> @Mcduck... very nice!

Have any of you tried enfuse yet.  It is built into the latest hugin (or you can use it from the command line) and while it is not a true HDR, it does give a nice result.

Here is some info:
[http://wiki.panotools.org/Enfuse](http://wiki.panotools.org/Enfuse)

and here is a sample from a hike I took this weekend:

That looks great, I'll have to try enfuse. Actually I've never tried hugin either..

---

### Post by cubeist on 2009-07-07
> **_sAm_ said:**
> This is strange; I wanted to try Qtpfsgui and did "sudo aptitude install qtpfsgui"(on latest Ubuntu).

Then I open the program from the menu, press "New Hdr..." > "Load Images" > "All formats" and browse to the folder with my jpg - but no pictures are shown? Nautilus can see them. 

I tried to change "All formats" to only jpeg, but still no pictures.

This is a folder with jpeg from Nikon D70 and D90, and my user owns them(and Qtpfsgui cant see my NEF files from the same folder). 

If I open the jpg files in Gimp and save them as tiff I can open them in Qtpfsgui(but then the exif data is removed).

I think this is an open bug... I can't remember, but it doesn't matter, bugs are not fixed fast in qtpfsgui and there is an easy workaround.

Your camera probably names your files with .JPG , for qtpfsgui to recognize them you have to rename them to .jpg

---

### Post by _sAm_ on 2009-07-08
> **cubeist said:**
> I think this is an open bug... I can't remember, but it doesn't matter, bugs are not fixed fast in qtpfsgui and there is an easy workaround.

Your camera probably names your files with .JPG , for qtpfsgui to recognize them you have to rename them to .jpg
You are spot on; I renamed the file to .jpg and I could see and open them in qtpfsgui. Thanks! 

The same is true for my raw files, so "mcduck" if you change your *.NEF files to *.raw you can open them(at least for Nikon D79/90 nef files).

---

### Post by AJB2K3 on 2009-07-08
Hay all, I'm using 1.9.1 on 8.10 lts and all works and yes its jpg in lower case (sometimes I get this bug with photobucket.)
I can even view mcducks .NEF file. (Thanks for that)

---

### Post by cubeist on 2009-07-08
> **_sAm_ said:**
> You are spot on; I renamed the file to .jpg and I could see and open them in qtpfsgui. Thanks! 

The same is true for my raw files, so "mcduck" if you change your *.NEF files to *.raw you can open them(at least for Nikon D79/90 nef files).

I created a hack fix in the source code for this and emailed the developer, it should be fixed in the next update.

---

### Post by Michael.Godawski on 2009-07-08
One HDR Rome impression from my last trip. ;)

---

### Post by solitaire on 2009-07-08
Here's my attempt at HDR (plus a couple of filters) It was taken with a cheep Digital Camera (Sony CyberShot ). Unfortunately not Open Source program was used :( it was windows software in WINE.

---

### Post by perroazul on 2009-07-09
> **Michael.Godawski said:**
> One HDR Rome impression from my last trip. ;)

how did you make that HDR Michael? If you used qtpfsgui+GIMP, which settings did you use with those programs?
your HDR looks great by the way.

---

### Post by Michael.Godawski on 2009-07-09
> **perroazul said:**
> how did you make that HDR Michael? If you used qtpfsgui+GIMP, which settings did you use with those programs?
your HDR looks great by the way.

I used the applications you stated, that is first qtpfsgui to open the jpg (had to rename the ending from JPG to jpg, so that the program actually sees it), then created two tone-mapped images Mantiuk and Fattal, saved them and opened them with Gimp.

Set the layers to multiply and that's it. No special settings, pretty everything left on the default level, I am just starting with digital photography and such kind of things.

---

### Post by perroazul on 2009-07-09
thanks. it seems that the combination Mantiuk + Fattal + multiply layer mode is the way to go

---

### Post by tgalati4 on 2009-07-10
One technique to try (as I have yet to try it myself) it to take a panorama breaking up a landscape into 8 zones (2 x 4 panels).  Take an optimized exposure in each zone and use hugin to blend the exposures.  

One doesn't need to stick to a 2x4 layout, you could simply shoot all shadow areas with an appropriate shadow spot meter exposure, then shoot the highlights with an appropriate exposure to avoid blowout, then shoot the entire panel with an average exposure.

In hugin, you can then specify which frames get blended with which exposures.  The result should be enough detail in the shadows while preserving (compressing) the highlights.  Of course, you get a superlarge file (mine are typically 200-500 MB) but then you can gimp it to bring out details and sharpen while keeping 48-bit color and dynamic range.

I have found telephoto works well for this type of shooting, but require more frames to cover the scene.  3 basic exposures +2, 0, -2 would give you around 10 stops of dynamic range.  Enough to impress.

---

### Post by chili555 on 2009-07-14
+1 for enfuse.

If you use a tripod (shouldn't you always?), you will have but one step:```
enfuse -o result.jpg --wExposure=1 259.jpg 260.jpg 261.jpg 262.jpg
```It produces great results without the halos and cartoon-ish effects. It also does terrific focus stacks. [http://photoblog.edu-perez.com/2009/01/greater-depth-field-macro.html](http://photoblog.edu-perez.com/2009/01/greater-depth-field-macro.html)

You may have to fiddle with the parameters a bit to get the result you want.

---

### Post by zevans on 2009-07-17
I read in a similar thread that GIMP only supports 8-bit so as soon as you open a RAW format in it, you've binned most of the information - is this true? (Certainly I've done better with digikam than I have with GIMP, this might be why.)

> This is actually a pseudo-HDR made from a single RAW image (I had no tripod with me). The original photo looked very dull with completely grey sky, but with some Fattal magick made it usable..

Oo, CLEVER. I think I can guess what you did - sometimes you don't want to throw away any of the histogram, just compress some of it subtly, but you don't have enough control just playing with the curve on a RAW->JPEG. I guess you have much more control over the map in Fattal?

I hadn't heard of half the software in this thread, thanks all - is it all in Ubuntu or medibuntu somewhere?

Qtpfsgui uses hugin as an engine, doesn't it?

---

### Post by perroazul on 2009-07-17
> **zevans said:**
> 
I hadn't heard of half the software in this thread, thanks all - is it all in Ubuntu or medibuntu somewhere?

Qtpfsgui uses hugin as an engine, doesn't it?

they're all in the ubuntu repositories, and yes Qtpfsgui uses hugin for aligning the images.

---

### Post by AJB2K3 on 2009-07-20
Its is a GUI front end using QTP for the HDR Imaging tool set which is a bunch of command line tools.

---

### Post by zevans on 2009-07-29
I had a play... and now I'm stuck. I've made a couple of hyperreal images that I'm quite pleased with, but if there is a way to give better hints as to which parts of the histogram to stretch or compress I could make a much better version of one particular landscape. 

I want to stretch the sky a little, to bring the clouds out, and also stretch the dark reflections in the water, and sacrifice the midtones to "make room." So, pretty sky, pretty water, plain boring grass. These areas of the photo all seem pretty far apart in the dynamic range so I know it's doable.

Is there any way of telling qtpfsgui or enfuse to do this? Both seem to pretty much make up their own mind, and also assume you're interested in the midtones more than anything else.

---

### Post by AJB2K3 on 2009-07-30
> **zevans said:**
> I had a play... and now I'm stuck. I've made a couple of hyperreal images that I'm quite pleased with, but if there is a way to give better hints as to which parts of the histogram to stretch or compress I could make a much better version of one particular landscape. 

I want to stretch the sky a little, to bring the clouds out, and also stretch the dark reflections in the water, and sacrifice the midtones to "make room." So, pretty sky, pretty water, plain boring grass. These areas of the photo all seem pretty far apart in the dynamic range so I know it's doable.

Is there any way of telling qtpfsgui or enfuse to do this? Both seem to pretty much make up their own mind, and also assume you're interested in the midtones more than anything else.
Without seeing the original files its hard to tell
BTW as to your earlier question- yes gimp only does 8bit however qtpfsgui handles more.

You could try altering a copy of the original image reconvert to generate the 2 new images then alter the images separately before recompilation.

---

### Post by cubeist on 2009-07-30
Hey zevens,
 there are a few options in enfuse that allow you to specify which areas of the images are used more than others.  It takes some trial and error, but it might help get a better result.  Here are the commands and the description:
[http://wiki.panotools.org/Enfuse#Fusion_options]("http://wiki.panotools.org/Enfuse#Fusion_options")

Also, after enfusing your images, you can open it in Gimp and add an image with the details you want, then selectively mask and erase until your features show through.

---

### Post by zevans on 2009-07-31
> **cubeist said:**
> Hey zevens,
 there are a few options in enfuse that allow you to specify which areas of the images are used more than others.  It takes some trial and error, but it might help get a better result.  Here are the commands and the description:
[http://wiki.panotools.org/Enfuse#Fusion_options]("http://wiki.panotools.org/Enfuse#Fusion_options")

Also, after enfusing your images, you can open it in Gimp and add an image with the details you want, then selectively mask and erase until your features show through.

The sigma thing might fix it, tried an enfuse last night and then realised I'd forgotten the aligning step, so results looked encouraging but had a slight air of multiple exposures about them.

I'm now wondering if in this case I might just take the lowest and highest two and mask them together, should work in this case and there's a reasonably well defined line between the correctly-exposed regions in both photos, so should be able to do a mask with edge detection. Sky from short exposure masked onto ground from long exposure. 

Don't have an ND-grad and wouldn't have worked anyway, it's not a horizontal!

---

### Post by zevans on 2009-07-31
hugin_hdrmerge ain't gonna work, it just keeps eating all the swap and falling over!

---

### Post by upptown on 2009-08-04
> **perroazul said:**
> @Mcduck: fantastic colors. it reminds me of the work of some modern painter... don't remember his name. 
 
@cubeist: lovely composition :)
I'm checking huging now to see how enfuse works

Michael Whelan?

---

### Post by TokyoYank on 2009-08-30
Hi,

As a beginner to HDR, I must admit that I sometimes found that the steps [*kindly posted by **AJB2K3***]("http://ubuntuforums.org/showpost.php?p=7530147&postcount=8") left me with open questions.  I'm writing with hopes that we could improve it, especially for those new to photo editing in linux

> **AJB2K3 said:**
> I use qtpfsgui and gimp in the following steps.
9 out of 10 people prefer the less is more look.

1, minor colour alteration in G.I.M.P.AJB2K3, is this step critical to HDR?  Are there some alterations that work better?  I also suppose this is a batch operation so that color is consistent?

> **AJB2K3 said:**
> 2, Create HDR in QTPFSGUI and save.When I saved the *.tiff I couldn't open it in GIMP.  (looked all white)  Is saving critical, or is it only for tweaking later?  .. the fact that the *.tiff wouldn't open was confusing.

> **AJB2K3 said:**
> 
3, create a tone map using mathiuk formula and save.
4, create a tone map using fattel formula and save.typo alert: *sp Mantiuk

Also, for a beginner's how-to it might be good to mention "using the the default settings," if, in fact, we should.  There are a lot of confusing sliders.  I think most people will realize that images should be saved at largest "result size" as they need.> **AJB2K3 said:**
> 
5, open mathiuk file in G.I.M.P.
6, Open fattel file in G.I.M.P and paste as a new layer into the mathiuk file,
7, set layer mode to Multiply.
8, merge layers
9, adjust finial colours
10, save image,
11, upload to photo bucket,
12 Post up on this forum as a thank you to everyone who helped me out.



Does anyone else have suggestions?  What are common stumbling blocks?  I suppose it might be nice to list > precise > menu > selections, but these tend to change when software is updated..



Side topic:

I got disappointing results using this procedure, for an auto-bracketed set with blue sky in the shot.  The Fattel tonemap had sand-paper like grain appear in the sky.  Was that due to default settings in Fattel or a known problem?  ... guess I could fix it by hand, but I was hoping for something more automated

---

### Post by Michael.Godawski on 2009-08-31
> Side topic:

I got disappointing results using this procedure, for an auto-bracketed set with blue sky in the shot. The Fattel tonemap had sand-paper like grain appear in the sky. Was that due to default settings in Fattel or a known problem? ... guess I could fix it by hand, but I was hoping for something more automated

I guess there is a noise reduction somewhere on the fattel setting panel.

---

### Post by AJB2K3 on 2009-08-31
> **TokyoYank said:**
> Hi,

As a beginner to HDR, I must admit that I sometimes found that the steps [*kindly posted by **AJB2K3***]("http://ubuntuforums.org/showpost.php?p=7530147&postcount=8") left me with open questions.  I'm writing with hopes that we could improve it, especially for those new to photo editing in linux

AJB2K3, is this step critical to HDR?  Are there some alterations that work better?  I also suppose this is a batch operation so that color is consistent?

When I saved the *.tiff I couldn't open it in GIMP.  (looked all white)  Is saving critical, or is it only for tweaking later?  .. the fact that the *.tiff wouldn't open was confusing.

typo alert: *sp Mantiuk

Also, for a beginner's how-to it might be good to mention "using the the default settings," if, in fact, we should.  There are a lot of confusing sliders.  I think most people will realize that images should be saved at largest "result size" as they need.



Does anyone else have suggestions?  What are common stumbling blocks?  I suppose it might be nice to list > precise > menu > selections, but these tend to change when software is updated..



Side topic:

I got disappointing results using this procedure, for an auto-bracketed set with blue sky in the shot.  The Fattel tonemap had sand-paper like grain appear in the sky.  Was that due to default settings in Fattel or a known problem?  ... guess I could fix it by hand, but I was hoping for something more automated

Thanks for your feedback as it will help to improve the master guide.

Issue 1 - Entirly subjective, the alterations here effect the outcome. If the source file looks bad then the end result will look bad however it will take time and experience to work out how alterations effect the end product.
Issue 2 - Don't know I work in the jpg work space.
Issue 3 - :confused: opps My Mistake.
Issue 4 - Good point and noted.
Issue 5 - Please give feedback !!!
Issue 6 - I think its down to noise in the image but I'm not pro but there is a smothing setting to help clean this up.
Yes it is know as I've had several bad renders.
> **Michael.Godawski said:**
> I guess there is a noise reduction somewhere on the fattel setting panel.
On the bottom of the fattel setting pannel is a smoothing slider. Increase this to increase smoothing.

---

### Post by TokyoYank on 2009-09-01
I should have mentioned before, here are the versions I'm using:[LIST]
[*]ubuntu 9.04, 2.6.28-15-generic
[*]gimp 2.6.6-0ubuntu1
[*]qtpfsgui 1.9.1-1build2
[/LIST]

> **AJB2K3 said:**
> Issue 1 - Entirly subjective, the alterations here effect the outcome. If the source file looks bad then the end result will look bad however it will take time and experience to work out how alterations effect the end product.OK, I understand now.  For the sake of other beginners, I would request a bit more comments--at least mention it is optional--in the How To.  

For a new topic to discuss, it is hard for me to imagine the effect of certain changes--color curve--to one frame but not others.  ... Perhaps anyone would care to write an "Intermediate HDR in open source How-To"?> **AJB2K3 said:**
> Issue 2 - Don't know I work in the jpg work space.OK, so you don't "Save Hdr" but instead do "File > Save Hdr Preview"?  Is this for a backup?  (if so, again a "optional" comment would be nice).. I am still learning, if you open one of these files to change a different tonemap later, is there a difference for *.tiff vs *.jpg? > **AJB2K3 said:**
> On the bottom of the fattel setting pannel is a smoothing slider. Increase this to increase smoothing.

Yes, I tried it, but there was no effect on my sky sand-paper.  ??

---

### Post by Michael.Godawski on 2009-09-01
I have created a very rudimentary howto on single hdr image create in Ubuntu. Would be nice to hear some feedback:


[LIST]
[*][http://shootingubuntu.blog.com/index.php/2009/09/single-hdr-image-creation-in-ubuntu/](http://shootingubuntu.blog.com/index.php/2009/09/single-hdr-image-creation-in-ubuntu/)
[/LIST]

---

### Post by AJB2K3 on 2009-09-01
> **TokyoYank said:**
> OK, so you don't "Save Hdr" but instead do "File > Save Hdr Preview"?  Is this for a backup?  

Opps I do save all masters as file.hdr then export each step to jpg.

Never used the rienhart 02 as a layer.:(
Nice guide but I'll pick some thing you picked up on in mine.

Step 1 - enterly optional.

BTW Nice render there.
BTW1 I'm in the process of rewriting the guide so keep an eye out.
BTW2 The guide was wip'd for [http://www.photography4allforum.co.uk/phpbb/viewtopic.php?f=25&t=7500]("http://www.photography4allforum.co.uk/phpbb/viewtopic.php?f=25&t=7500")and that version makes more sense.

---

### Post by AJB2K3 on 2009-09-02
OK sat down and tryed out your 3 Phase guide
[IMG]http://i703.photobucket.com/albums/ww40/Adam_Bryant/HDR/blashfordlakes_3_phase.jpg[/IMG]
Quite an intersting render.

Its a bit more complicated then my method but its a good method.

---

### Post by Michael.Godawski on 2009-09-03
Nice one.

Currently I am experimenting with black and white photography.
New Thread? :)

---

### Post by AJB2K3 on 2009-09-03
> **Michael.Godawski said:**
> Nice one.

Currently I am experimenting with black and white photography.
New Thread? :)
Agreed !
Maybe titled HDR Tutorial Discussion?

---

### Post by TokyoYank on 2009-09-05
_For both Michael and Adam_:  Do either of you have experience using your procedures for traditional multiple-exposure HDR photography?  ... The title and OP of this thread led motivated me to break out the tripod and play with my bracket button.  

_Does anyone reading_ have experience with how Qtpfsgui processes the initial HDR when multiple exposures are selected/opened/combined?  Does that have impact on subsequent tonemap steps/options?

... I'm still gathering a few representative shots (both single and multiple exposure) to try these steps on.  But on the off-chance that Adam's how-to is best suited for single-exposure pseudo-hdr, again it would be a nice side note to mention


_Last question:_  How do I "do this the hard way."  Are there any good how-to's for manual HDR creation from multiple exposures in GIMP?  I will also try Hugin, but I'm guessing creative GIMP layer transparency mapping would allow the most control.


Thanks!

---

### Post by Rodney9 on 2009-11-03
> **Michael.Godawski said:**
> I have created a very rudimentary howto on single hdr image create in Ubuntu. Would be nice to hear some feedback:


[LIST]
[*][http://shootingubuntu.blog.com/index.php/2009/09/single-hdr-image-creation-in-ubuntu/](http://shootingubuntu.blog.com/index.php/2009/09/single-hdr-image-creation-in-ubuntu/)
[/LIST]

Thank You So Much, very good of You.

Rodney

---

### Post by TokyoYank on 2009-11-03
> **Michael.Godawski said:**
> I have created a very rudimentary howto on single hdr image create in Ubuntu. Would be nice to hear some feedback:
it's a good how-to, a very clean description of the various scattered topics in this thread

but:  your example has a halo effect in the sky near the clouds, and in my test image that was _always_ the location of gritty noise.  Am I the only one who dislikes this?  

searching found a related link, May 2009
[http://www.cambridgeincolour.com/forums/thread1625.htm](http://www.cambridgeincolour.com/forums/thread1625.htm)

A key point mentioned is that noise reduction should be adjusted depending on beta; specific parameter ranges are listed.  Once I get a chance I'll experiment with beta = 0.6 and 0.25<NR<0.5   ...  I can't recall what the default Fattal parameters on my version of the qtpfsgui package

---

### Post by treesurf on 2010-05-23
Just wanted to dig this older thread up and say a big thanks to all who have given such good advice here.  :)

---

### Post by earlycj5 on 2010-05-24
Since this thread was resurrected, I'll chime in here as well.

I do like the tonemapping effect on some images, but for many that I shoot I'm just not a fan.

Enfuse does a nice job of exposure blending without the tonemapping so you get very realistic looking results by using it.

There's an older bash script in this forum for using a single RAW to do exposure blending with seven exposures.  I modified it a bit to work with the latest UFRAW.

```


#!/bin/bash

if [ ! "$1" ]
then
	echo "Please specify filename."
	exit 1
fi

if [ ! -f "$1" ]
then
	echo "Error: file does not exist"
	exit 1
fi

# extract the filename without extension
filename=`basename "$1" | sed 's/\.\([^\/\.]*$\)//'`

# check lower limit param
if [ $2 ]
then
	lower_limit="$2"
else
	lower_limit=-3
fi

# check upper limit param
if [ $3 ]
then
	upper_limit="$3"
else
	upper_limit=3
fi

# make sure lower limit < upper limit
if [ $upper_limit -le $lower_limit ]
then
	echo "Error: upper limit is smaller than lower limit."
	exit 1
fi

echo "Processing from $lower_limit to $upper_limit."

file_list=""

# should we use -3 exposure from RAW
if [ $lower_limit -lt -2 ]
then
	if [ ! -f "${filename}_N3.tiff" ]
	then
		ufraw-batch  --wb=camera --exposure=-3 --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_N3.tiff "$1"
	fi
	file_list="${filename}_N3.tiff"
fi

# should we use -2 exposure from RAW
if [ $lower_limit -le -2 -a $upper_limit -ge -2 ]
then
	if [ ! -f ${filename}_N2.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=-2  --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_N2.tiff "$1"
	fi
	file_list="${file_list} ${filename}_N2.tiff"
fi

# should we use -1 exposure from RAW
if [ $lower_limit -le -1 -a $upper_limit -ge -1 ]
then
	if [ ! -f ${filename}_N1.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=-1 --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_N1.tiff "$1"
	fi
	file_list="${file_list} ${filename}_N1.tiff"
fi

# should we use 0 exposure from RAW
if [ $lower_limit -le 0 -a $upper_limit -ge 0 ]
then
	if [ ! -f ${filename}_0.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=0 --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_0.tiff "$1"
	fi
	file_list="${file_list} ${filename}_0.tiff"
fi

# should we use +1 exposure from RAW
if [ $lower_limit -le 1 -a $upper_limit -ge 1 ]
then
	if [ ! -f ${filename}_P1.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=1  --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_P1.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P1.tiff"
fi

# should we use +2 exposure from RAW
if [ $lower_limit -le 2 -a $upper_limit -ge 2 ]
then
	if [ ! -f ${filename}_P2.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=2  --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_P2.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P2.tiff"
fi

# should we use +3 exposure from RAW
if [ $upper_limit -gt 2 ]
then
	if [ ! -f ${filename}_P3.tiff ]
	then
		ufraw-batch  --wb=camera --exposure=3  --saturation=1.25 --black-point=auto --out-type=tiff --out-depth=8 --output=${filename}_P3.tiff "$1"
	fi
	file_list="${file_list} ${filename}_P3.tiff"
fi

# run enfuse with default parameter, edit this line for more advance enfuse options
enfuse ${file_list} -o ${filename}_enfused.tiff $4 $5 $6 $7 $8 $9

# uncomment the next line to auto clean up, else just leave the temp files to experiment more
rm ${file_list}

echo "Done: final output file is ${filename}_enfused.tiff"

gimp ${filename}_enfused.tiff

exit 0

```

Batch processes my Nikon RAW image and then opens it in the Gimp. Modify as needed.

Examples of photos I've used this technique with: [http://www.flickr.com/photos/earlycj5/tags/enfuse/](http://www.flickr.com/photos/earlycj5/tags/enfuse/)


Enfuse is part of Hugin and in the Ubuntu repositories.

---

### Post by frdrx on 2010-05-25
I'd say, forget about digital HDR "photography"; the results are usually hideous and not worth the effort. Instead, shoot some negative film, get it processed by a lab, and use the saved time to play with free software. :P

---

### Post by earlycj5 on 2010-05-25
> **frdrx said:**
> I'd say, forget about digital HDR "photography"; the results are usually hideous and not worth the effort. Instead, shoot some negative film, get it processed by a lab, and use the saved time to play with free software. :P

Clearly, they're hideous and not worth the effort, that Enfuse program I mentioned costs so much to install from the repositories.  :-s

By the time I shoot the film, and then get it developed and back home, I could've done a several HDRs the same day I shot them.

---

