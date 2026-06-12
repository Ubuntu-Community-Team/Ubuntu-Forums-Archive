---
title: "seeking advice on exposure blending"
date: 2010-04-20
forum: Art &amp; Design
---

### Post by jessel on 2010-04-20
I am looking for a way to enhance images by blending. I've tried the exposure blending plugin for gimp, and enfuse (command line and the digikam plugin).

My best results thus far have been to use a technique similar to the gimp plugin, but to manually edit the mask and so far I have done well with just two exposures. I'd be happy with this but I have to align manually, and I don't have a tripod. Is there a way to align exposures so that I can then import them into gimp as layers? 

All my work thus far with enfuse leaves me with muddy washed out images as well. I especially like the way digikam works and the exposure blending tool, BUT I'm not getting good results with it. The auto alignment is very cool, but no matter how I adjust the exposure, saturation, and contrast I'm not happy...

My background: I'm fairly new to digital photography and becoming more interested in digital editing. I've read grokking the gimp and I'm ok with gimp. I have started shooting raw and can work with raw files pretty well. Honestly I shoot raw + jpg, and most of the time I don't  mess with the raw files. I've started using hugin with pretty good results. I've used with HDR via pfstools, with very poor results that look cartoonish. All I'm after is good color compsition in the foreground and a nice blue sky...

If anyone wants examples I can can post some. Oh and for what its worth I only use ubuntu, as much as it may suit my needs I just won't be installing windows. The task at hand for me is to best use what is at hand (ubuntu).

Thanks!

---

### Post by guine on 2010-04-22
I don't know of any auto aligning tools, but you could change the exposure of the raw once its on a computer.  I know a some people prefer using multiple exposures rather than a single raw for making hdrs, but you can still get fairly realistic looking pictures from a single raw.

Whenever I make hdrs I use qtpfsgui(I think its offically luminance now) which is decent for a free program that works in linux.  Its not as good as some of the commercial stuff available for windows and mac but if youre willing to play around with it some it can make pretty good hdrs.(I prefer the mantiuk operator for tonemapping, most of the other operators aren't realistic)

This won't work for most of your photos you take since you said you were wanted this for outdoor photos, but an easy way to get around not having a tripod inside sometimes is if you have a lamp that has a lampshade on it is take the lampshade off and the screw that holds it up is usually the right size for a camera so you can use the lamp as a tripod.

---

### Post by cubeist on 2010-04-23
i'm too tired to post much of a reply, but for aligning, there is align_image_stack  I have used it a lot and the results are great (but your original images should be tripod takes)

there are also a few other command line tools... a good place to start is to install hugin from source... this will give you a graphical interface that can do some decent exposure blends, but also includes some other cli tools.

once you have a stack of aligned images there are many decent cli tools/algorithms which will give you various blended results, from mild to full hdr: enfuse (which you know about) pfstmo_mantiuk06, pfstmo_fattal (these require pfstmo tools)... don't forget to read the man pages for all the options..


sorry if this isn't making any sense...


lastly, taking one raw and the exposing it a few times and then blending together is not really exposure blending (in a pinch you can get ok results this way)...but if you want great shots, you need to take several images with different shutter speeds at the same f-stop.  (and yes there is a technical difference, but it requires a ton of complicated explanation, most of which is way over my head!)

---

### Post by jessel on 2010-04-23
Everyone, thanks for posting. I appreciate the feedback. All I'm looking to do is exposure blending, so if anyone reading feels like they get good results using hugin, enfuse, the digikam expo tool, qtpfs, or something else let me know. I just want to learn how. I'm partial of course to the simplest method, but want a good result.

guine:
+Yeah, I've installed qtpsftools and not had good results. I'm sure the program works well, but there are many variables and I haven't found a good source on how to use it. So, the times that I've sat down to use it I end up wasting a lot of time, on a random trial and error process (that ends with a photo looking like a cartoon). How did you learn to use it? Do you know something about digital imaging and tonemapping, or did you just try some different settings? Oh, and are you combining two outputs in gimp (or is there some other way)?
+I've used qtpfstools where I'm tonemapping a single raw file and multiple exposures.
+I'll try luminance, but its probably about the same (as qtpfstools).
+I use rawtherapee and I know how to create change the exposure setting. In practice, I generally get better color from the original jpgs (camera is set to raw + jpg). Also, I just realized that the jpgs that I create (3898X2594) are dimensionally different from the jpgs the camera generates (3888X2592).
+As far as indoor photography, I use my 50mm/f1.8 if I can get away with it. Otherwise (with a slower lens), I can still do pretty well in low light at ISO 1600.
+I really want to combine mulitiple exposures though. One raw does have more exposure latitude, but generally speaking it isn't enough...

cubeist:
+ I've only used align_image_stack via digikam's exposure blend tool and hugin. I can put bracketed handheld shots into hugin, but the aligned outputs I get are always blended in such a way that each of the ouput has adjusted exposure.
+ Your post makes sense to me. I just can't seem to get the stack of aligned images that has not been enfused or blended. That is, when I take three bracketed shots load them in to hugin, they are aligned, then I go to the "stitcher tab" and select "remapped images", but each of my three output images looks "enfused" as they don't look nearly the same as the three input jpgs.
+Why do i want to install hugin from source? I installed the package from the ubuntu repository. I could install from source, but will there be any difference?

---

### Post by guine on 2010-04-23
I did a fair amount of guessing and testing, but also a good number of the pictures in this pool have the settings that people used to make them listed with the picture, so you can see what other people have done.
[http://www.flickr.com/groups/qtpfsgui/](http://www.flickr.com/groups/qtpfsgui/)
Unfortunately I don't think as many people are displaying the settings they used as they used to so it'll take a little more looking through the pool to see what other people used than it did when I first started using the program.

---

### Post by mcduck on 2010-04-23
Even the Qtpfsgui's developer only says about the settings that describing how the different algorithms work would be far too complicated, so the best way really is to just play with the settings and see what effect they have on your image. The actual values depend much on the image itself and it's resolution, setting that looks good on a large image will give very different result on smaller version of the same image.

Anyway, don't be afraid of unnatural looking results, many of the algorithms will not only change the image's local contrast but also the saturation and colors. As a result you'll pretty much always to do some editing in Gimp afterwards, at least to adjust levels and colors. And you can always blend the tonemapped images together, and even with one of the original images, to adjust the result to your liking. Try different blending settings as well, for example if you got otherwise nice HDR image but the colors are wrong, you could add the original image as a layer with "Color" blending. Multiply and Overlay are often useful as well.

Personally, I almost always create a couple of  versions using both Fattal and Mantiuk algorithms, and then take all those images and the best of the original photographs to Gimp as layers. Also it's useful to have the original image somewhere visible, so you can compare the colors etc. with it as you work with your HDR image.

You might also want to check the old HDR thread for more helpful ideas: [http://ubuntuforums.org/showthread.php?t=1185859]("http://ubuntuforums.org/showthread.php?t=1185859")

one more tip for nice images: tonemapping is pretty much a tradeoff between local contrast and contrast over the whole image area. On the other hand the key to a good (normal) photograph is the shadows and lights over the whole image area, so going too far with tonemapping will result in flat image. If you want the image to look good you'll need to have some kind of contrast over larger areas as well, in some cases the contrast of colors in your image is enough for that (blue sky versus green ground or sand dunes, for example), or contrast in the amount of details in different regions of the image, but if you don't have such image then blending the HDR together with the original image will help to bring back some of the image's original shadow and light regions, giving you back some of the large-area contrast while still having most of the details of the tonemapped image.

---

### Post by jessel on 2010-04-28
cubeist:
 I didn't initially realize that align_image_stack was a command line tool, though looking at the command line it looked to me like it should be. Anyway, long story short, I have finally figured out how to use it and it is the solution that I was looking for. Though the man page doesn't specify I get errors unless the input files are 16 bit tiff...

mcduck & mcduck:
I've started using pfstools for a variety of images. Thanks for the flickr reference, it been really helpful to see the setting people use to create various images. I definitely feeling like I'm getting some better results.


I've attached a photo as processed using pfstools mantiuk operator (from a single raw) and the camera generated jpg. It still looks a little animated, but in the original jpg you can't even see the black dog.

---

### Post by finite9 on 2010-09-16
Does anyone know of any good tutorials for using the exposure blend plugin?  I have found tutorials on the web (main one being from Instructables that pertains to Gimp 2.4 I think) which describe how to make a HDR manually using Gimp layers, and I have used the Exposure blend plugin (just selected 3 images and hit the "process" button, but they give poor results in themselves.

I downloaded HDRsofts Photomatix Pro to compare, and used one of their sample images and it turned out great.  It really was choose and click to create a good HDR, but they had a Tone Mapping step that I think im missing in Gimp.  I then ran their sample image through Exposure Blend and it was washed out in comparison and still dark in the shadows with little detail.

I have seen images in the HDR pool on Flickr that were created with Gimp+exposure blend that look great so obviously im missing something...

I feel that there is a lot of post processing involved even if you use Exposure Blend in Gimp, but I have no idea how to proceed.

If anyone can point to a good step by step tutorial for Gimp 2.6 with Exposure blend I would be very thankful.

---

### Post by jessel on 2010-09-17
[finite9]("http://ubuntuforums.org/member.php?u=87087"):

gimp exposure blend is a completely different animal from photomatix altogether. if you read the descriptions of each you will see why, and part of this is that tonemapping is not something you are missing in gimp's exposure blend, it is not there, because exposure blend "doesn't work that way".

i have not achieved good results with gimp-exposure blend, though i see other have. combining exposures is generally tough, and i haven't easily achieved good results using any method.

another manual method that worked ok for me was to manually use layer-align tool from hugin, then mask the layers like in the gimp plugin. i.e. sky layer + foreground layer...

you are right (in my opinion) post-processing is a big part of it, and honestly i can only do so much. you really need to spend a lot of time photo editing to get good result, my way getting around this is to pay the guy at the photo store to work on the images that i just can't quite get myself! its not incredibly expensive, and there is no short way to gain enough experience without doing a lot work.

---

### Post by psoulocybe on 2010-09-17
I do a lot of exposure blending in my landscape shots.  I do it manually.  Tripod shots, manually aligned, then dodge and burn the layers.  
It's not an automatic process, but it gives me EXACTLY the results I want every time, though can be time consuming.

---

### Post by finite9 on 2010-09-17
Thanks for the replies.  I'm a real amateur when it comes to photo editing, so I feel i've reached the limits of my ability to go further with this, but it was interesting to try.  What puzzles me the most is that people on Flickr are adamant that they have created their HDRs with Gimp and Exposure Blend, however on the forums, I have read one post that says "if they claim they did it in Gimp, they're lying".  However, I cannot think why someone would lie about which program they created an image in.

---

### Post by jessel on 2010-09-19
> **psoulocybe said:**
> I do a lot of exposure blending in my landscape shots.  I do it manually.  Tripod shots, manually aligned,

why not use align_image_stack? It does a great job of aligning images. The rest of the process is still very time consuming of course, but I really like the align_image_stack tool...

---

### Post by mcduck on 2010-09-19
> **finite9 said:**
> Thanks for the replies.  I'm a real amateur when it comes to photo editing, so I feel i've reached the limits of my ability to go further with this, but it was interesting to try.  What puzzles me the most is that people on Flickr are adamant that they have created their HDRs with Gimp and Exposure Blend, however on the forums, I have read one post that says "if they claim they did it in Gimp, they're lying".  However, I cannot think why someone would lie about which program they created an image in.

That probably just means that those people haven't really understood the difference between blending different exposures in a photo editor and creating a HDR/DRI image. If you just blend different images together you never actually have the step where you have a HDR photograph, and tonemapping works quite differently than using layer blending.

The images you see on web are not the actual HDR images, they are *images tonemapped from HDR image file, sometimes called DRI images ("Dynamic Range Incresed) *. You can't actually view the HDR file itself or print it or anything like that, it contains far higher dynamic range than any display or print media is able to display. They ares till very useful in computer graphics & animation, though. And of course you can select a certain range from the HDR image or tonemap it to get a picture you can view.

---

