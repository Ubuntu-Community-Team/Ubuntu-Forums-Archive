---
title: "Possible to do this in The GIMP?"
date: 2006-07-18
forum: Art &amp; Design
---

### Post by Kimm on 2006-07-18
I was recently at a friends house helping him to design a poster, he is using Photoshop CS.

We based the poser on an initial draft that I had made. And we decided to completely copy one part of it.
Thats where we ran into trubble. My poser was tiny compared to the one we where working on, so when we dragged the copied area out... to fit the new poster, it was extremely pixelated. But aparently this wasnt a problem.
My friend just pressed a button in Photoshop and suddenly the picture was sharp again :S

I think this is a pretty interesting feature... and I am woundering if it can be done in The GIMP?

---

### Post by Pyro MX on 2006-07-18
I hope I understand you problem right. Did you streteched out the image to make it bigger/smaller? If that's the case, to kinda "fix" the problem you had,when you stretch stuff, there's an option called "interpolation", put it to "cubic", you should get better results.

---

### Post by Kimm on 2006-07-18
I'm not sure what you mean...

As a mather of fact... I'm not completely sure to how I would go about stretching objects in the Gimp at all...

---

### Post by shortbus on 2006-07-18
> **Kimm said:**
> I'm not sure what you mean...

As a mather of fact... I'm not completely sure to how I would go about stretching objects in the Gimp at all...

I have an idea of what he's talking about. When I get back to my ubuntu box I'll get some screen shots.. Sorry I don't have them now, in my VoIP class and not paying attention.

---

### Post by shortbus on 2006-07-19
heres the best i could come up with.. Scaling is great.

[IMG]http://www.geocities.com/nicaboker18/Screenshot.png[/IMG]
Above is the original image I started with. Nothing done to it.
[IMG]http://www.geocities.com/nicaboker18/Screenshot-1.png[/IMG]
Above I am in the process of scaling the image down. So far I have not seen any pixalation going in either direction. (up or down)
[IMG]http://www.geocities.com/nicaboker18/Screenshot-2.png[/IMG]
And this is the final image.

if you need a more detailed explaination, let me know.

---

### Post by commodore on 2006-07-19
Lol he scaled the image bigger but he lost the quality because of that (of course). In Photoshop CS there's a button that fixes it a bit because Photoshop is better than GIMP. And no there's no button like that in GIMP. You can try sharpen and unsharp mask filters but they are not the same.

---

### Post by Kimm on 2006-07-19
> **commodore said:**
> Lol he scaled the image bigger but he lost the quality because of that (of course). In Photoshop CS there's a button that fixes it a bit because Photoshop is better than GIMP. And no there's no button like that in GIMP. You can try sharpen and unsharp mask filters but they are not the same.

Well thats exactly what I wanted to know, to bad it cant be done in The GIMP though. Although I supose someone might create a plugin or something like that in the future.

---

### Post by N8K99 on 2006-07-19
You can also scale individual layers as well as the whole image in GIMP. 

Not sure that it really matters but Photoshop CS, the CS stands for Creative Suite and comes bundled with several other apps and costs a mighty pretty penny.

---

### Post by sakke on 2006-07-20
Could you ask your friend what exactly the button was (that he/she pressed to get picture sharp again)?

Was your work done with vectors? Maybe it was just that your friend scaled vector image bigger, it got pixelated and he had to press some button to tell Photoshop to render the vector image again.

When you are scaling bitmap images (in GIMP or some other software) it's always a good idea to experiment with interpolation settings. Sometimes you can get good results with so called stair interpolation. It basically means that you don't scale straight to for example 200% but do it in many small increments, like 110% seven times and then to the final size.

However, bitmap images are not well suited for scaling as you probably knew. It can not be helped with software if the source image has too low resolution. Not even if the software is used by professionals and costs a lot. I think GIMP performs here just as well as Photoshop.

You question if this can be done in GIMP: first we have to know what exactly was done and then, I guess, the answer is yes.

---

### Post by Aelfric5578 on 2006-07-20
There's no button in GIMP that will fix a pixelated image--at least not that I'm aware of.  However, as sakke pointed out, if you click Image -> Scale Image or Layer -> Scale Layer there is a pull-down box that lets you change the interpolation settings.  If you set interpolation to Cubic, you will get the least amount of pixelation.  I'm using Windows at the moment, but I think the interface is the same, so I've attached a screenshot of the dialog.

@sakke Is there actually a way to choose star interpolation as an option somewhere, or do you have to manually resize the image in small increments?

---

### Post by sakke on 2006-07-21
> **Aelfric5578 said:**
> 
@sakke Is there actually a way to choose star interpolation as an option somewhere, or do you have to manually resize the image in small increments?

No, there isn't, but I think it's not too hard to write a script to do stair interpolation. I will be away from computer until tomorrow, but I will try writing the script when I get back home.

When I was still using Windows and Corel, I wrote a script for Corel to do stair interpolation. I didn't use it much, but it was nice to do some experiments with it.

---

### Post by graigsmith on 2006-07-22
ok. no program can do it. They can blow it up, but it's not adding quality pixels.  it's just blowing it up.  gimp does this, just use the scale tool.  if you blow something very small up to very large, it will look pixelated until you finish the scale operation. once you hit scale, it adds the new pixels into the blown up image, and makes a best guess as to what those pixels colors are.  If the details weren't there before. photoshop, or gimp, or any other raster graphics editor will not be able to find any details between the squares of a pixel.  all they see is the square.  and the best they can do, is to guess the color of the pixels inbetween.

---

### Post by DirtDawg on 2006-07-24
> **commodore said:**
> In Photoshop CS there's a button that fixes it a bit because Photoshop is better than GIMP. 

LOL. A magic button! Sounds like an lazy-hack button to me.

---

### Post by miked2 on 2006-07-26
Hello, 
Gimp gives us a large collection of very good tools. Usually, it's possible to do this sort of thing by combining the tools. If I understand the problem correctly, an image resolution is increased to get more pixels, and then when you zoom in on the 'enhanced' image, you can still see the shape of the original pixels.  
There are probably several ways to get around this in Gimp, one way that works well with line art type images is to use a combination of blur and threshold tools.  
To test this out, I took a 420x300 image (just a white background with some hand-written text in black using the pencil tool) and scaled it to 3360x2400, then applied gaussian blur (29%) so that the edges were lost in the numerous shades of grey.  I then used the threshold to map all pixels to either black or white (adjusted manually to get an acceptible line thickness).
The result gives nice smooth edges.

---

### Post by Lew on 2006-07-28
I wonder if it would be possible to use an algorithm such as [2xSaI](http://en.wikipedia.org/wiki/2xSaI), [hq2x](http://www.hiend3d.com/hq2x.html), [hq3x](http://www.hiend3d.com/hq3x.html) or [hq4x](http://www.hiend3d.com/hq4x.html) as a filter in GIMP.  For certain types of image this could possibly produce some good results.

---

### Post by miked2 on 2006-07-28
Hello again, 
I just had a quick look at the hq2x code (written in C++ with some assembler) but I think that Gimp requires plug-ins to be written in C (not 100% sure - the plug-in writing tutorial is all in C, and this is as far as I've got) so if someone writes this plug in, they'll probably need to rework the algorithm code a bit.  
If I've got this right, the hqnx algorithms appear to concentrate pixel averaging (filtering) in the Y channel.  So I had a quick go at doing this (don't get too excited, the results are not that good).  I decomposed the image into its Y Cb Cr components (Image - Mode - Decompose) then did a quick blur and sharpen on each channel with more blurring / sharpening on the Y channel before composing the channels back into an RGB image again.  I reckon with a bit of practice the results could be improved, then perhaps a script_fu could be written to cut out the mouse clicks?

---

### Post by miked2 on 2006-07-29
Right, now I have some good news - 
There is already a stair interpolation script:
[http://registry.gimp.org/plugin?id=6775](http://registry.gimp.org/plugin?id=6775)
Drag it into your 'scripts' folder & you will have a new menu option:
Script-Fu - Eg - Stair Interpolation.  
I had a go at using it to increase the resolution of some simple graphics earlier & the results are pretty good.  Using it is very easy too, it gives a slider control to adjust the factor by which the resolution is to be increased.  See the example.

---

