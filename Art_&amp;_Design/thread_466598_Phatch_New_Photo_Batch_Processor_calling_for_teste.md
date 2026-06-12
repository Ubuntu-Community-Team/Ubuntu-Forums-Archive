---
title: "Phatch: New Photo Batch Processor calling for testers"
date: 2007-06-06
forum: Art &amp; Design
---

### Post by stani on 2007-06-06
Phatch = Photo & Batch! ([http://photobatch.stani.be](http://photobatch.stani.be))

Phatch is a simple to use cross-platform GUI Photo Batch Processor which handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, rename, ... and much more [actions]("http://photobatch.wikidot.com/actions") in minutes instead of hours or days if you do it manually. [Get Started!]("http://photobatch.wikidot.com/getting-started")

* You can download Phatch at the main website [http://photobatch.stani.be](http://photobatch.stani.be) > free download (ubuntu deb installer available). 
* If you want improved exif support, please download this [installer]("http://packages.ubuntu.com/hardy/python/python-pyexiv2"). 
* If you want seemless integration with Nautilus, install: sudo apt-get install python-nautilus

Phatch has already pretty good [documentation wiki]("http://photobatch.wikidot.com"), but it could still be improved a lot with your helping hands (screenshots, text, ...). You can find a tutorial here.

If you want to know what users are saying: read [this]("http://photobatch.wikidot.com/reviews").

I am also looking for help to write documentation (screenshots, ...), translation of phatch in other languages, extending phatch with plugins (only knowledge of python & pil required), etc...

Translate phatch in your language! Every word counts, go here: [https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

Phatch currently can perform the following actions:
    * Auto Contrast - Maximize image contrast
    * Border - Crop or add border to all sides
    * Brightness - Adjust brightness from black to white
    * Canvas - Crop the image or enlarge canvas without resizing the image
    * Colorize - Colorize grayscale image
    * Common - Copies the most common pixel value
    * Contrast - Adjust from grey to black & white
    * Convert Mode - Convert the color mode of an image (grayscale, RGB, RGBA or CMYK)
    * Effect - Blur, Sharpen, Emboss, Smooth, &#8230;
    * Equalize - Equalize the image histogram
    * Fit - Downsize and crop image with fixed ratio
    * Grayscale - Fade all colours to gray
    * Invert - Invert the colors of the image (negative)
    * Maximum - Copies the maximum pixel value
    * Median - Copies the median pixel value
    * Minimum - Copies the minimum pixel value
    * Offset - Offset by distance and wrap around
    * Posterize - Reduce the number of bits of colour channel
    * Rank - Copies the rank'th pixel value
    * Rotate - Rotate with random angle
    * Round - Round or crossed corners with variable radius and corners
    * Saturation - Adjust saturation from grayscale to high
    * Save - Save an image with variable compression in different types
    * Scale - Scale an image with different resample filters.
    * Shadow - Drop a blurred shadow under a photo with variable position, blur and color
    * Solarize - Invert all pixel values above threshold
    * Text - Write text at a given position
    * Transpose - Flip or rotate an image by 90 degrees
    * Watermark - Apply a watermark image with variable placement (offset, scaling, tiling) and opacity

Combining this, you can easily achieve this if you follow this [tutorial]("http://photobatch.wikidot.com/tutorial-round-3d-reflect"):

[IMG]http://photobatch.wikidot.com/local--files/tutorial-round-3d-reflect/thumb.jpg[/IMG]
Thanks for testing,

Stani
--
PS Some screenshots to whet your appetite...

[IMG]http://photobatch.wikidot.com/local--files/getting-started/actions-scale.png[/IMG]
[IMG]http://photobatch.wikidot.com/local--files/getting-started/scale-round-shadow.png[/IMG]
[IMG]http://photobatch.wikidot.com/local--files/image-inspector/image_inspector_exif.png[/IMG]

---

### Post by stani on 2007-06-06
Some more screenshots...

Screenshot 1: drag and drop:
You can drag and drop any files or folder on the Phatch window from Nautilus, F-spot, digiKam, ... Phatch will open an options window (eg. do you want to include subfolders of these folders and which file types in these folders). You can also minimize Phatch (View>Droplet) to a droplet which is handy if you have a preconfigured action list.

Screenshot 2: shadow

Screenshot 3: shadow + rounded corners

Screenshot 4: shadow + rounded corners + watermark (by offset)

Screenshot 5: shadow + rounded corners + watermark (tile)

---

### Post by aktiwers on 2007-06-06
Looks pretty cool!
Im gonna install it this weekend :)

---

### Post by PartisanEntity on 2007-06-07
Hello stani, I have installed it and am testing, have already filed one minor bug report.

---

### Post by Garyu on 2007-06-07
One thing I've been missing for photo batch jobs is some tool to edit the tags. For example, I use gthumb to rename my photos according to date and time they were shot. This is great, 'cause I can sort the photos correctly even if I go and edit them later on.

My problem is that one of my cameras actually save the time information in the "last changed" tag of pictures rather than the original date. So I want to copy the info from that tag to the other one. And of course, there are other tag operations that might be helpful at other times.

Very good initiative though. :)

---

### Post by Stone123 on 2007-06-07
UI isn't really user friendly . If program is about editing images , then add "add new image" or "open existing project" menus.

But a good idea for the project.

---

### Post by stani on 2007-06-07
> **Stone123 said:**
> UI isn't really user friendly . If program is about editing images , then add "add new image" or "open existing project" menus.
I think you misunderstood the concept and probably should use a program like GIMP. The program is not about editing programs but about batching image collections. Right now phatch only works with local image folders as a collection. Later collection might come from various sources, such as:
- the internet (flickr, ...)
- ftp
- ...

For phatch a file is an action list, not an image. You can create, edit and save action lists. You can apply this action list to a number of images. Compare it to the automate batch function in Photoshop, but as a stand alone program.

---

### Post by stani on 2007-06-07
> **Garyu said:**
> My problem is that one of my cameras actually save the time information in the "last changed" tag of pictures rather than the original date. So I want to copy the info from that tag to the other one. And of course, there are other tag operations that might be helpful at other times.

Exif support is on my todo-list and once implemented you could easily do what you ask for. Please subscribe yourself to the exif blueprint on launchpad. If possible, add your example as a comment:
[https://blueprints.launchpad.net/phatch/](https://blueprints.launchpad.net/phatch/)

---

### Post by PartisanEntity on 2007-06-07
Nice work stani, I have filed  a couple bug reports but phatch works nicely, I wish I had it a week ago after I came back from a trip to Paris. I had to manually edit tons of photos, what a pain that was.

---

### Post by PartisanEntity on 2007-06-07
It would be nice if I could apply actions to only certain photos inside a folder.

Also it would be nice if I could see small thumbnails of photos inside a folder and then select individual photos in order to apply an action.

Rationale:

Lets imagine I have 100 photos in a folder. At the moment in phatch I would have to move all the photos that I want rotated 90 degrees to a new folder to apply the Transpose action.

Lets say I also have some photos that need to be resized and others that need to be inverted, I have to select those that need to be resized and place them in a new folder and do the same for those that need to be inverted.

But if I would see thumbnails from inside phatch and if I would apply actions by selecting images then i could speed up the process.

Here is what I mean, made with GIMP:

---

### Post by stani on 2007-06-08
> **PartisanEntity said:**
> It would be nice if I could apply actions to only certain photos inside a folder.

Also it would be nice if I could see small thumbnails of photos inside a folder and then select individual photos in order to apply an action.

Rationale:

Lets imagine I have 100 photos in a folder. At the moment in phatch I would have to move all the photos that I want rotated 90 degrees to a new folder to apply the Transpose action.

Lets say I also have some photos that need to be resized and others that need to be inverted, I have to select those that need to be resized and place them in a new folder and do the same for those that need to be inverted.

But if I would see thumbnails from inside phatch and if I would apply actions by selecting images then i could speed up the process.
Of course I have this kind of functionality in my mind too. But first I want to tackle:
- lazyness: when you are batching thousands of files (as I do some times), it would be nice that you can quit phatch and resume later without having to restart from the beginning.
- internationalisation: allow users to translate phatch in their local language (through e.g. rosetta)

However I recognize that selecting individual files is important, so i might provide a temporary solution with a file select dialog or drag&drop. In longer term I have a special UI in it for my mind.

Stani

---

### Post by stani on 2007-06-08
> **PartisanEntity said:**
> It would be nice if I could apply actions to only certain photos inside a folder.
I've uploaded a temporary solution as promised with a file select dialog box. You can not see all the images as thumbnails at the same time (at least not in Gnome, but maybe in KDE it is possible). However by Ctrl clicking you can select individual images and have a preview for the last clicked image. Later I'll work on a real thumbnail pane.

---

### Post by durand on 2007-06-09
Love your program, i've filed 2 bugs.

---

### Post by PartisanEntity on 2007-06-09
> **stani said:**
> I've uploaded a temporary solution as promised with a file select dialog box. You can not see all the images as thumbnails at the same time (at least not in Gnome, but maybe in KDE it is possible). However by Ctrl clicking you can select individual images and have a preview for the last clicked image. Later I'll work on a real thumbnail pane.

Very nice stani thanks.

---

### Post by stani on 2007-06-10
> **durand said:**
> Love your program,
Spread the word wherever you can!

>  i've filed 2 bugs.
Thanks for reporting, they are both fixed.

---

### Post by stani on 2007-06-11
I've added a new feature: drag and drop. This (almost) takes away the need to implement a thumbnail manager.

For more info and screenshots, read my second post of this thread:
[http://ubuntuforums.org/showthread.php?p=2796343#2](http://ubuntuforums.org/showthread.php?p=2796343#2)

---

### Post by durand on 2007-06-11
Cool ;)

---

### Post by PartisanEntity on 2007-06-11
I am not quite sure how the droplet feature is supposed to work, I have posted a question concerning it:
[https://answers.launchpad.net/phatch/+question/7991](https://answers.launchpad.net/phatch/+question/7991)

---

### Post by stani on 2007-06-14
> **PartisanEntity said:**
> I am not quite sure how the droplet feature is supposed to work, I have posted a question concerning it:
[https://answers.launchpad.net/phatch/+question/7991](https://answers.launchpad.net/phatch/+question/7991)

I've fixed it. Just drag & drop any amount of pictures from nautilus, f-spot, konqueror, ... and it will batch process these photos.

---

### Post by PartisanEntity on 2007-06-14
> **stani said:**
> I've fixed it. Just drag & drop any amount of pictures from nautilus, f-spot, konqueror, ... and it will batch process these photos.

I noticed thanks, but I was a little busy the past week, I can confirm though that the droplet is working now, a great feature.

The translation into German is progressing too ;)

---

### Post by stani on 2007-06-16
> **PartisanEntity said:**
> The translation into German is progressing too ;)

Great! Any idea when it will be ready?

I've been developping at high speed. A lot of refactoring and also some new features. Right now Phatch supports the following actions: image scaling or downsizing, rotating, mirroring, converting, shadows, rounded corners, watermark, ...

You can watermark your images by an offset, by tiling or scaling. The watermark can have any transparency you want.

I've put some new screenshots in the second post of this thread: [http://ubuntuforums.org/showthread.php?p=2796343#2](http://ubuntuforums.org/showthread.php?p=2796343#2)

---

### Post by durand on 2007-06-17
wow, you are really developing this fast!

---

### Post by PartisanEntity on 2007-06-17
> **stani said:**
> Great! Any idea when it will be ready?

I've been developping at high speed. A lot of refactoring and also some new features. Right now Phatch supports the following actions: image scaling or downsizing, rotating, mirroring, converting, shadows, rounded corners, watermark, ...

You can watermark your images by an offset, by tiling or scaling. The watermark can have any transparency you want.

I've put some new screenshots in the second post of this thread: [http://ubuntuforums.org/showthread.php?p=2796343#2](http://ubuntuforums.org/showthread.php?p=2796343#2)

Hi stani,

I must admit that I have not been doing any testing or translating lately, I am a bit swamped time-management wise at the moment.

I will keep you up to date though, I have started translating however I am not far yet, perhaps 20 words at most currently.

However I am very impressed with the work you have put into Phatch, it really is great and I am spreading the news about it.

Cheers :)

---

### Post by handaxe on 2007-06-18
Hi,

This looks very promising indeed. Thanks.

How about a renaming mask - ie batch rename by inserting fixed text into the original file name, or the date? This can serve both with other transformation modules and as a standalone function.

HA

---

### Post by stani on 2007-06-18
> **handaxe said:**
> How about a renaming mask - ie batch rename by inserting fixed text into the original file name, or the date?

Good suggestion, I was expecting already someone to ask for it. Could you please register a new blueprint 'rename' with some different scenarios/possibilities of what you would like to have implemented?

Do it here: [http://www.launchpad.net/phatch](http://www.launchpad.net/phatch)

Stani

---

### Post by handaxe on 2007-06-18
will do.

Forgot me password (sigh :() and waiting for reset email....

HA

---

### Post by PartisanEntity on 2007-06-19
Just to show I have not stopped helping out, I will try to do some translation this weekend.

---

### Post by handaxe on 2007-06-20
> **stani said:**
> Good suggestion, I was expecting already someone to ask for it. Could you please register a new blueprint 'rename' with some different scenarios/possibilities of what you would like to have implemented?

Do it here: [http://www.launchpad.net/phatch](http://www.launchpad.net/phatch)

Stani

Done.

HA

---

### Post by stani on 2007-06-20
> **PartisanEntity said:**
> Just to show I have not stopped helping out, I will try to do some translation this weekend.
Great! Please send me as soon as possible the .po file you have till now. I can upload it than to Rosetta, so more people can collaborate on it:
[https://translations.launchpad.net/phatch/](https://translations.launchpad.net/phatch/)

Afterwards you can continue on Rosetta.

Anyone reading this message with a different language than English or Dutch is kindly invited to translate Phatch.

Stani

---

### Post by jackmc on 2007-06-21
thanks,you just saved me (actually my dad) a lot of manual work! One little possible feature request - batch file size changes.. maybe through standardising dimensions? 

eg:

I had about 50 product images that needed to be formatted for a website. they ranged from ~ 750*450 to about three times that size.

If I could make them all the same dimensions, then apply a quality filter, it would be one-click perfection!

Thanks for the app, it worked excellent here. No bugs to report :)

---

### Post by stani on 2007-06-21
> **jackmc said:**
> thanks,you just saved me (actually my dad) a lot of manual work!That was why it was developed!> **jackmc said:**
> One little possible feature request - batch file size changes.. maybe through standardising dimensions? 

eg:

I had about 50 product images that needed to be formatted for a website. they ranged from ~ 750*450 to about three times that size.

If I could make them all the same dimensions,Can you specify more? Phatch can give you a fixed dimension by the action "Image size". Just set the width and the height to the dimension you want (of course don't use '%').> **jackmc said:**
>  then apply a quality filter, it would be one-click perfection!What do you mean with a quality filter?!> **jackmc said:**
> Thanks for the app, it worked excellent here. No bugs to report :)Great!

---

### Post by jackmc on 2007-06-21
> **stani said:**
> Can you specify more? Phatch can give you a fixed dimension by the action "Image size". Just set the width and the height to the dimension you want (of course don't use '%').

Ahh, that was what I was after! Maybe you could add a dropdown for the user to choose between pixels/percent (maybe later add cm/inches/etc - not really necessary at the moment I guess). What I'm saying is I didn't realise it was an option!

Regarding the "quality' thing, I was just referring to using the feature that is already implemented in the saving part (sorry about my un-technical talk!).

Basically, it is perfect. Does everything *I* will ever need from it :)

Just then I found a bug - if you click on "height", and delete the value, then click to something else, things go crazy.

Great work, thanks a lot :)

---

### Post by stani on 2007-06-21
> **jackmc said:**
> Maybe you could add a dropdown for the user to choose between pixels/percent Good suggestion! In order to do a little for phatch, please register a blueprint at launchpad: [https://blueprints.launchpad.net/phatch/](https://blueprints.launchpad.net/phatch/) I'll take care of the implementation ;-)> **jackmc said:**
> (maybe later add cm/inches/etc - not really necessary at the moment I guess). But Phatch already supports cm & inch!> **jackmc said:**
> 

Just then I found a bug - if you click on "height", and delete the value, then click to something else, things go crazy.Please report this bug at [https://bugs.launchpad.net/phatch/](https://bugs.launchpad.net/phatch/) and I'll look at it.

Stani

---

### Post by PartisanEntity on 2007-06-21
@ stani,

I have sent you what I have so far of the German translation

---

### Post by stani on 2007-06-21
> **PartisanEntity said:**
> @ stani,

I have sent you what I have so far of the German translationThanks a lot! Now, do not work on the translation until I have uploaded it to Rosetta. Afterwards you can conitnue to translate here:
[https://translations.launchpad.net/phatch/](https://translations.launchpad.net/phatch/)

Stani

---

### Post by stani on 2007-06-21
I have a made a deb installer for those want to try it out. It installs Phatch nicely in your application menu. Please email or pm me if you want to receive it.

---

### Post by Nicram on 2007-06-21
Where is a deb file? Couldn't you link it here?

---

### Post by stani on 2007-06-21
> **Nicram said:**
> Where is a deb file? Couldn't you link it here?At this point I don't want to put it yet for public download. Anyone can get it by emailing me.  (I've sent already to a couple of people.) It will be later available from the internet.
Thanks for your patience!
Stani

---

### Post by PartisanEntity on 2007-06-21
@ stani,

Please send me a .deb file, even though I have it under /dev in /home at the mo.

I love the way it is developing, I played around with it today and found no bugs.

Keep up the good work, and thank you for your time and effort.

---

### Post by stani on 2007-06-21
> **PartisanEntity said:**
> @ stani,

Please send me a .deb file, even though I have it under /dev in /home at the mo.I've sent it to your gmail address.> **PartisanEntity said:**
> 

I love the way it is developing, I played around with it today and found no bugs.

Keep up the good work, and thank you for your time and effort.Thanks!

---

### Post by jackmc on 2007-06-21
wow, you are very quick at bug fixing! Loving the new dropdowns :)

Thanks heaps

I've sent you a PM regarding the deb :)

---

### Post by durand on 2007-06-22
How did you make the deb? Checkinstall or dpkg-buildpackage?

---

### Post by stani on 2007-06-22
> **durand said:**
> How did you make the deb? Checkinstall or dpkg-buildpackage?I've used dh_make, pycentral & dpkg-buildpackage.

---

### Post by Ubuntuud on 2007-07-13
This is exactly what I'm looking for!

It could use some impromvement though...
Anyway, keep up the good work!

---

### Post by digitalis_vulgaris on 2007-07-13
Sorry for interrupting this exiting creative process, but I have a question: is this program free to use ? I need some stuff like this one for everyday commercial purposes.

---

### Post by digitalis_vulgaris on 2007-07-13
Newer mind... I just find suitable GUI solution for batch conversion. Just kind of software I were looking for. Still supporting your efford. Wish you very best...

---

### Post by stani on 2007-07-14
> **digitalis_vulgaris said:**
> is this program free to use ? I need some stuff like this one for everyday commercial purposes.This program is 100% free to use as it is licensed under the GPL v3. You can use it for commercial purposes.

---

### Post by digitalis_vulgaris on 2007-07-14
Do you need some graphic files to be made ? Icon, splash screen... ?

---

### Post by stani on 2007-07-14
> **digitalis_vulgaris said:**
> Do you need some graphic files to be made ? Icon, splash screen... ?Sure, that always saves me some work. I've looked up your posts and your round logo for compiz was quite neat. BTW, phatch supports CMYK as well. 
Please send me an email with some illustration work you did, so I have a better idea of my work. You can get my email through launchpad or by sending me a private message.
Thanks for the offer,
Stani

---

### Post by stani on 2007-07-14
> **Ubuntuud said:**
> This is exactly what I'm looking for!It is my pleasure.> It could use some impromvement though...What do you mean? Would you mind to register them as blueprints on launchpad?
Stani

---

### Post by digitalis_vulgaris on 2007-07-15
48 x 48 px is so small resolution! Don't allow me to do much... Here you go, I make some icon for Patch.

I must think about splash screen. Maybe I make some kind of 3d maskot. I try to do something till the end of the week.

About Python Editor,  I'm not in the mood for making logo. Maybe next time when I have some free time...

P.S. : mr. X == Kekeljevic Igor

---

### Post by digitalis_vulgaris on 2007-07-16
I try to make a splash screen for Stani's Patch. I wanted to create a mascot of robot who handling tools for picture editing. Here is a sketch. What do You think about it ? Any sugestions ?

---

### Post by motin on 2007-07-16
> **Garyu said:**
> One thing I've been missing for photo batch jobs is some tool to edit the tags. For example, I use gthumb to rename my photos according to date and time they were shot. This is great, 'cause I can sort the photos correctly even if I go and edit them later on.

My problem is that one of my cameras actually save the time information in the "last changed" tag of pictures rather than the original date. So I want to copy the info from that tag to the other one. And of course, there are other tag operations that might be helpful at other times.

Very good initiative though. :)

Check out Gnome-Commander - you can rename files using many different tags: [http://www.nongnu.org/gcmd/tags.html](http://www.nongnu.org/gcmd/tags.html)

> **stani said:**
> Good suggestion, I was expecting already someone to ask for it. Could you please register a new blueprint 'rename' with some different scenarios/possibilities of what you would like to have implemented?

Do it here: [http://www.launchpad.net/phatch](http://www.launchpad.net/phatch)

Stani

Remember the philosophy of having separate apps for separate tasks. There are already a lot of good batch renaming apps. Maybe you can integrate Gnome Commanders rename features into Phatch?

> **digitalis_vulgaris said:**
> I try to make a splash screen for Stani's Patch. I wanted to create a mascot of robot who handling tools for picture editing. Here is a sketch. What do You think about it ? Any sugestions ?

Hehe cool!

---

### Post by stani on 2007-07-17
> **digitalis_vulgaris said:**
> I try to make a splash screen for Stani's Patch. I wanted to create a mascot of robot who handling tools for picture editing. Here is a sketch. What do You think about it ? Any sugestions ?
Hi Igor,
Wow, I turn my back some days and I am pleasantly surprised! I like the concept of the splash screen much better than the logo. It is funny and original, which I miss in the logo (gears are soo much used for batching). What is the green: a bread toaster? I actually quite like the idea of the bread toaster a lot. Probably for the logo you could make a bread toaster filled with breads (and maybe one bread jumping out), but without the robot under it. For the splash screen you can keep it like it is, as it can be different. I just would like it to be a more glossy/glassy/shiny as the logo. But I guess that is why you called it a sketch.
Technically I need both the logo and the splash screen in svg vector format. In Ubuntu you can use e.g. inkscape for that. 
I am targeting phatch to be ready for Gutsy. But anyone can get already now a working .deb for Feisty if they private message me. People are translating in a lot of languages already: Dutch, French,  Italian, Chinese and Spanish. There is still some work to do on these or other languages, so it would be nice if more people could translate. Wow, it looks like phatch is getting popular even without being published officially yet. This is open source in live in action.
So Igor I am very happy with your participation. Great work, thanks!
Stani

---

### Post by motin on 2007-07-17
> **stani said:**
> People are translating in a lot of languages already: Dutch, French,  Italian, Chinese and Spanish. There is still some work to do on these or other languages, so it would be nice if more people could translate. Wow, it looks like phatch is getting popular even without being published officially yet. This is open source in live in action.

I'll make an attempt on the Swedish version if you like. PM me or attach necessary files to this thread.

Cheers!

---

### Post by stani on 2007-07-17
> **motin said:**
> I'll make an attempt on the Swedish version if you like. PM me or attach necessary files to this thread.

Cheers!
The beauty of launchpad is that you just need to log in and you can start translating right away. So get a launchpad account, login and go to:
[https://translations.launchpad.net/phatch/](https://translations.launchpad.net/phatch/)

I am looking forward to the Swedish translation. 

Thanks a lot!

Stani

---

### Post by motin on 2007-07-18
> **stani said:**
> The beauty of launchpad is that you just need to log in and you can start translating right away. So get a launchpad account, login and go to:
[https://translations.launchpad.net/phatch/](https://translations.launchpad.net/phatch/)

I am looking forward to the Swedish translation. 

Thanks a lot!

Stani

Cool! I have used rosetta before but by an earlier message in this thread I got the perception that a .po-file needed to be uploaded. I am on it!

---

### Post by rax_m on 2007-07-18
It works !!! Just to need to figure the ins and outs now.. 

I've been needing an app like this .. so thanks to all the people who've put effort into it :)

---

### Post by digitalis_vulgaris on 2007-07-18
I just install Blender and started with modeling robo character for phatch. I was so happy with results of the tests that I just have to share my thrill with someone...

For **Stani**: Splash screen will be .png (raster picture), becouse I'm planning to use Blender. Which dimensions would you like ? About an icon, still have no inspiration. Default size for icon is 48x48. I must make something what looks good as small picture, but I'll make .svg , as you requested. I'm still open for sugestions. Idea about toster don't looking to me as a optimal solution...

---

### Post by salehid on 2007-07-18
Really Pretty Cool!!! Thanks.

---

### Post by durand on 2007-07-19
> **digitalis_vulgaris said:**
> 
For **Stani**: Splash screen will be .png (raster picture), becouse I'm planning to use Blender. Which dimensions would you like ?

I'm probably interfering but wouldn't a blender sized splash screen be the right size?

---

### Post by digitalis_vulgaris on 2007-07-20
Not over yet, still need to add some tools for picture editing...

---

### Post by durand on 2007-07-20
Nice work though I think that you need to increase the hardness of the box bit. It seems like it is reflecting a lot, making it look a bit distorted. Apart from that, good job.

---

### Post by digitalis_vulgaris on 2007-07-21
This is the newest render for mascot. Still planning to put some items inside robot's basket, but allmost done. I'm looking for an idea for phatch logo (something can be used for icon)...

---

### Post by durand on 2007-07-21
Wow, that cools awesome, good work!

---

### Post by stani on 2007-07-21
> **digitalis_vulgaris said:**
> I just install Blender and started with modeling robo character for phatch. I was so happy with results of the tests that I just have to share my thrill with someone...You are completely right to be proud. It looks very awesome. One comment: In the splash screen I really want a reference to a photo camera. Maybe in the basket? Cool you did it in Blender, so maybe later we can animate it for a promotion shot or screencasts on youtube. I need to have the Blender sources as well. If they are not to big, I want to distribute it with phatch so that the artwork is also 'open source'.
> For **Stani**: Splash screen will be .png (raster picture), becouse I'm planning to use Blender. Which dimensions would you like ?As you notice with the current version of Phatch, the splash screen is a bitmap with a custom size and the splash screen is drawn in the main frame when no actions are added. The default phatch frame is 400x440 px including window borders, toolbars, etc... So I would put the maximum dimension of the splash screen to 300px width and the height a bit lower. You can experiment yourself by taking a screenshot (Alt+PrtScr) of Phatch and pasting your image in it. Maybe it is more nice when the splash screen is a bit smaller and has more white space around.
>  About an icon, still have no inspiration. Default size for icon is 48x48. I must make something what looks good as small picture, but I'll make .svg , as you requested. I'm still open for sugestions. Idea about toster don't looking to me as a optimal solution...Well, I still like the toaster. Also note that the icon will be used from sizes,like 16x16 for the frame title, and a bit bigger for in the start menu.

Thank you very much!
Stani

---

### Post by digitalis_vulgaris on 2007-07-23
I made icon for Phatch. It looks very good in all sizes. Any comments ?

---

### Post by durand on 2007-07-23
I like that one! Nice colours but maybe you should lighten the greys so they stand out more when the icon is small.

---

### Post by digitalis_vulgaris on 2007-07-23
Durand, you remind me on my wife. Nothing misses your sharp and merciless eyes...

---

### Post by salehid on 2007-07-23
nice work ... thanks :)

---

### Post by aktiwers on 2007-07-24
I can help you out with Danish translation if you like. Its just missing in launchpad.
Edit: Nevermind.. added it my self.

---

### Post by digitalis_vulgaris on 2007-07-28
I made wallpaper for Phatch. I hope that Stani likes it ... That from me for now. Have some job to finish...

Greetings to all

---

### Post by durand on 2007-07-29
good work ;)

---

### Post by stani on 2007-07-31
> **digitalis_vulgaris said:**
> I made wallpaper for Phatch. I hope that Stani likes it ...Yes, I like it. It could almost be already be a nice layout for the frontpage of the phatch website. Right now, I don't have easy access to internet, but in the end of the week I will get back to you to discuss the artwork further and to other people who asked for  a deb installer. Good luck with your work!
Stani

---

### Post by digitalis_vulgaris on 2007-08-01
Ok, Stani. I still have some job to finish, but prepare me technical sketch to see what You need, and I will do it in a free time.

---

### Post by motin on 2007-08-02
Seems like launchpad is buggy atm - can't submit translation strings. For later then...

---

### Post by PartisanEntity on 2007-08-15
Is the latest version of Phatch working for anyone? In my case nothing is happening when I click on 'execute' or when I drag a file/folder over the droplet.

---

### Post by stani on 2007-08-15
> **PartisanEntity said:**
> Is the latest version of Phatch working for anyone? In my case nothing is happening when I click on 'execute' or when I drag a file/folder over the droplet.
Confirmed. Thanks for the bug report. Follow here:
[https://bugs.launchpad.net/phatch/+bug/132649](https://bugs.launchpad.net/phatch/+bug/132649)

I hope I have time soon to fix it.

Stani

---

### Post by stani on 2007-08-15
> **stani said:**
> I hope I have time soon to fix it. I've committed a fix.

---

### Post by digitalis_vulgaris on 2007-08-16
I tried Phatch, and I was realy pleasanty supprised. You have my compliments Stani. This is very good tool. But, I have some suggestions how to make Phatch even better...

**1. Installation with .deb file**
I'm beginer in using Ubuntu. I like install new application by using .deb file. I just download it from internet, select file and press enter. Ubuntu finish the rest of a job. You have my vote for .deb.

**2. Adding application launcher during installation**
It would be nice if Phatch add his launcher with icon in Main Menu, in Graphics.

**3. Folder listed Actions like PhotoShop**
I read some comments how you could make Phatch more like gThumb. Infact, I like how Phatch working, I wouldn't add image browser in it. There is no need. Drag and drop from Nautilus is realy practical. Great work, Stani!
It would be great if user gets list of all Actions earlier defineded when he starts Phatch. Actions should have open/close arrow and be listed in folders for easear use, like in PhotoShop. Actions would be executed by drag and drop.

**4. Better file rename**
User must have freedom to rename his files. I often use batch for arange files numericly (001.png, 002.png, 003.png ...). This is essential tool in animation. I must find ease way for this job. Gthumb have great solution for this: # (enumerator), %f(original filename), %d(image date), %s (image size), %e(original extension).

**5. Buttons**
Keep user interface as simplest as possible. I see need only for these buttons:
New Action
Duplicate Action
New Script
New Action Folder
Trash (drag and drop to delete action, script or action folder or select and press trash icon)
Refresh (if user add plugin, script or action in determined Phatch Action Folder)
Configuration (for language chooser and folder paths for action lists, plugins...)
Help

With these buttons user can easy finish any job... Renaming actions and action folders can be done with F2. All items can be moved by drag and drop (no need for orange arrows). Use standard controls for selecting items (click, shift, control...) . User can delete item by pressing Delete on keyboard.

If user want to import some action he can easy add it to defined Phatch Action Folder using Nautilus.

---

### Post by durand on 2007-08-16
I think Stani will have a deb file for the stable release

---

### Post by stani on 2007-08-16
> **digitalis_vulgaris said:**
> I tried Phatch, and I was realy pleasanty supprised. You have my compliments Stani. This is very good tool. But, I have some suggestions how to make Phatch even better...
Glad you finally tried it.
> 
**1. Installation with .deb file**
I'm beginer in using Ubuntu. I like install new application by using .deb file. I just download it from internet, select file and press enter. Ubuntu finish the rest of a job. You have my vote for .deb.

**2. Adding application launcher during installation**
It would be nice if Phatch add his launcher with icon in Main Menu, in Graphics.
Ha, this is all implemented already! For now still with the old artwork. When I have all your final images they will be replaced.

> 
**3. Folder listed Actions like PhotoShop**
I read some comments how you could make Phatch more like gThumb. Infact, I like how Phatch working, I wouldn't add image browser in it. There is no need. 
Drag and drop from Nautilus is realy practical. Great work, Stani!
Me too, thinking about the idea of the browser, I rejected it and found a droplet a better way as it prevents reinventing the wheel and everybody can use it favorite tools.
> 
It would be great if user gets list of all Actions earlier defineded when he starts Phatch. 
What do you mean?
> Actions should have open/close arrow They have this, no? > and be listed in folders for easear use, like in PhotoShop. Actions would be executed by drag and drop.Well of course from the beginning I had organisation in my mind. I am not such a big fan of folders but more of tags. The mechanism for the tags is already partially there but not exposed yet. First I want to release Phatch with a minimal set of powerful actions and later I want to extend it. Probably also creating an extension repository like firefox. I consider the set for a first release quite complete. Maybe I'll add a reflection plugin and/or a perspective plugin to be able to make nice thumbnails like this: [http://macslow.thepimp.net/shots/gl-gst-player-4.png](http://macslow.thepimp.net/shots/gl-gst-player-4.png)
> 
**4. Better file rename**
User must have freedom to rename his files. I often use batch for arange files numericly (001.png, 002.png, 003.png ...). This is essential tool in animation. I must find ease way for this job. Gthumb have great solution for this: # (enumerator), %f(original filename), %d(image date), %s (image size), %e(original extension).

Please add this on the blueprint which is opened for rename on the phatch launchpad site.
> 
**5. Buttons**
Keep user interface as simplest as possible. I see need only for these buttons:
New Action
Duplicate Action
New Script
New Action Folder
Trash (drag and drop to delete action, script or action folder or select and press trash icon)
Refresh (if user add plugin, script or action in determined Phatch Action Folder)
Configuration (for language chooser and folder paths for action lists, plugins...)
Help

With these buttons user can easy finish any job... Renaming actions and action folders can be done with F2. All items can be moved by drag and drop (no need for orange arrows). Use standard controls for selecting items (click, shift, control...) . User can delete item by pressing Delete on keyboard.

If user want to import some action he can easy add it to defined Phatch Action Folder using Nautilus.
Please add this as a blueprint. I need more time to think about this.

Thanks for the feedback,
Stani

---

### Post by digitalis_vulgaris on 2007-08-17
1 picture speaks more than 1000 words. Especially words of bad spokesman of english language as I am.

---

### Post by stani on 2007-08-20
> **digitalis_vulgaris said:**
> 1 picture speaks more than 1000 words. Especially words of bad spokesman of english language as I am.
Thanks for the image and feedback. For the first release of Phatch, I want to keep the program as simple as possible and to keep it 100% bug free is my top priority, in which I succeeded till now.  If you are manipulating thousands of images to screw up. In a later version I plan to make it more sophisticated. In this indeed a folder/list of actions can be imported as if it were a single action as well. This will allow end users to define new actions without programming, but just some drag & drop. This will require quite some time to implement it, so I have to postpone it.

Also first other things have to be done. For example a website needs to be created. If any of you is good in website design (or knows someone), please contact me. Of course I first will like to see some of your previous work.

But actually I wanted to post this because Igor send me his artwork. It has a big 'wow'-factor (a real one), so I wanted to share this joy with you. You can get it by pulling the latest release of bazaar. If you are more lazy, just send me your email in a private message and I will send you a one click deb installer.

Igor, your credits now appear in the about box as they should do now. Do you let me know if they are as you want (name, website, ...).

I am quite overwhelmed how hard people are working on translations. It is going great, but more help is needed. This is the status so far:

```
Danish 69.53% new, 30.47% untranslated
Dutch 100.0% published
Finnish 7.17% new, 92.83% untranslated
French 	55.91% new, 44.09% untranslated
German 	3.94% new, 96.06% untranslated
Italian 91.4% new, 8.6% untranslated
Romanian 4.3% new, 95.7% untranslated
Simplified Chinese 7.17% new, 92.83% untranslated
Spanish 36.2% new, 63.8% untranslated
Swedish 15.05% new, 84.95% untranslated
```

Participating is very easy, just surf to:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

And if you translate, just let me know, so I can mention your name in the credits.

Thanks in advance!
Stani

---

### Post by motin on 2007-08-21
> **stani said:**
> I am quite overwhelmed how hard people are working on translations. It is going great, but more help is needed. This is the status so far:

```
Danish 69.53% new, 30.47% untranslated
Dutch 100.0% published
Finnish 7.17% new, 92.83% untranslated
French 	55.91% new, 44.09% untranslated
German 	3.94% new, 96.06% untranslated
Italian 91.4% new, 8.6% untranslated
Romanian 4.3% new, 95.7% untranslated
Simplified Chinese 7.17% new, 92.83% untranslated
Spanish 36.2% new, 63.8% untranslated
Swedish 15.05% new, 84.95% untranslated
```

Participating is very easy, just surf to:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

And if you translate, just let me know, so I can mention your name in the credits.

Thanks in advance!
Stani

I come back now and then to work on some translations, but the last weeks I have encountered a lot of these errors when trying to save a batch of translations:
> 
Timeout error

Sorry, something just went wrong in Launchpad. We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.

Trying again in a couple of minutes might work. If it doesn’t, and this is blocking your work, let us know on the launchpad-users mailing list (requires subscription). Include the error ID OOPS-598A915 in your message.


..which puts me off somewhat in my motivation to translate since I risk to have to redo the translations I try to add. 

This time it went through the second time I tried which is ok. Earlier I have tried 5-6 times without coming through.

I'll continue trying, but this may be something general that slows down the process for all of us.

---

### Post by PartisanEntity on 2007-08-21
Ever since I sent you those German files I must say that I have been quite a slacker when it comes to translations, but since I did help you with quite a number of the early bugs I hope I can redeem myself stani :)

Will try to help with the translations on the weekend, although I must say I found the 'home' method easier or more convenient than the web-based on Launchpad, but I do see the benefits.

I can help with a website, both graphics and layout although I am better in layout than making nice icons, you can view my site which is linked in my signature, it's yet another blog (based on Wordpress but I made my own theme and coded it from the ground up in HTML and CSS).

---

### Post by Swarms on 2007-08-21
I must admit you made a great job Stani doing this project, I take pictures daily, and when I want to resize it, this program makes it a breeze. ;)

---

### Post by stani on 2007-08-21
> **motin said:**
> I come back now and then to work on some translations, but the last weeks I have encountered a lot of these errors when trying to save a batch of translations:


..which puts me off somewhat in my motivation to translate since I risk to have to redo the translations I try to add. 

This time it went through the second time I tried which is ok. Earlier I have tried 5-6 times without coming through.

I'll continue trying, but this may be something general that slows down the process for all of us.

Sorry to hear that, but please don't give up. From time to time I also had problems updating with launchpad, but luckily I kept on trying. Launchpad is a great platform which is in full development. This might be a disadvantage sometimes, but I prefer that much more than sites like sourceforge or berlios who don't really change for years.

In case someone of you promises to translate whole phatch by himself in a language in a short time (some weeks). I can provide an offline solution. If you only do a part, launchpad is the way to go.

---

### Post by stani on 2007-08-21
> **PartisanEntity said:**
> I can help with a website, both graphics and layout although I am better in layout than making nice icons, you can view my site which is linked in my signature, it's yet another blog (based on Wordpress but I made my own theme and coded it from the ground up in HTML and CSS).
Hi Partisan,

Contact me by email if you have some time to work on the layout. Your blog has a nice palette of colours. Don't worry about graphics and icons, Igor made a wonderfull job. I have the logo and title available as svg and the rendering on big format. Also I have a whole collection of icons which I use for the actions in Phatch. Probably they can be used for the website as well. (Unless Igor finds them ugly and has enough time to provide an alternative.)

Also I will build the backend in python & django. One of the things I want is that everything goes automatic: packaging, screenshots, download, news, documentation, ... I'll take care of this. If you make a nice template with html and css (for welcome page, news, downloads, screenshots, ...), I can integrate it in the site.

I have some instructions for the website. For example, I want to use this reflection js for certain images:
[http://cow.neondragon.net/index.php/383-Reflectionjs-Demo](http://cow.neondragon.net/index.php/383-Reflectionjs-Demo)

So if you email me, I can send you the artwork and we can discuss things together. I prefer you help me with this rather than translating for now.

Thanks in advance,
Stani

---

### Post by stani on 2007-08-21
> **Swarms said:**
> I must admit you made a great job Stani doing this project, I take pictures daily, and when I want to resize it, this program makes it a breeze. ;)
Haha, that will be a nice user quote on the website.
Stani

---

### Post by digitalis_vulgaris on 2007-08-21
:lol: Hahahahahahahahahahahaha

I see you liked icons I made for Admiror site. You are killing me with your persistency ! Hhahahahahaha

You are such a character. 

Hahahahahahahahah:lol::lol::lol::lol::lol:

I really like to work with you and I let you now if I find some time for a site. But, I can't promise you anything. If I have time I would rather help on development some new graphic tools.

Greetings...

---

### Post by stani on 2007-08-22
> **digitalis_vulgaris said:**
> Hahahahahahahahah:lol::lol::lol::lol::lol:
You got the point :)

I have  uploaded all the translations to bazaar. So now you should be able to check if the translations so far are working correctly. German is a special case because I still had an offline translation to upload first. Afterwards I will also upload the translations from launchpad.

---

### Post by stani on 2007-08-29
Time for some updates...

I recommend everyone to update from bazaar as some important issues are fixed, such as:
- moving actions up or down (drag and drop, toolbar, ...)
- better error message for invalid paths
- wxPython2.6 issues

People who got a deb installer from me, are better of requesting a new one. Just get it from the attachments of the first post.

I made already a design for the frontpage. I only tested it in Firefox and Opera. Too lazy to start up Internet Explorer now ... I've attached a screenshot to hopefully find some enthousiastic people who want to help. It is not finished yet. The menu will be upper right and some adsense down left to cover some expenses. 

But everyone should help me in finding a good slogan. (e.g. jokosher: "...audio production made simple") Right now I have: "Manipulate thousands photos with one click in a few minutes instead of hours!" But that is not very sexy. Does somebody has a better (preferably shorter) suggestion. It might be with humour. Maybe: "One click is worth more than thousand photos."

Also for those who know python & PIL, I wrote a developer manual to write your own actions to integrate in Phatch. I'll post it on the first post. Also I will publish the latest deb in the first post. But use it at your won risk!

I saw some people already blogging about Phatch and recommending it on this forum. This a good way to support the project: spread the word as much as you can. (Search anywhere for "batch photos" and recommend phatch.)

That is all for now.

Thanks for your support!

Stani

PS. And keep on translating...

---

### Post by durand on 2007-08-29
That image you attached is great! Is that the website frontpage or just another image?

PS: this might help: [http://browsershots.org/](http://browsershots.org/)

---

### Post by rulus on 2007-08-29
> **stani said:**
> I've used dh_make, pycentral & dpkg-buildpackage.
Can you point me to a some sort of guide? I have a bzr branch with Python code, and I'm looking for the most efficient way to create .deb's out of it. Thanks.

---

### Post by stani on 2007-08-29
> **durand said:**
> That image you attached is great! Is that the website frontpage or just another image?

PS: this might help: [http://browsershots.org/](http://browsershots.org/)
That is the website frontpage. Reflection, perspective, ... is all done with javascript and css. ([http://www.netzgesta.de/reflex/](http://www.netzgesta.de/reflex/)) 
Thanks for the link. I knew it existed, but forgot to bookmark it. However the site is not publicly available yet, so I can't test it right now.

---

### Post by stani on 2007-08-29
> **rulus said:**
> Can you point me to a some sort of guide? I have a bzr branch with Python code, and I'm looking for the most efficient way to create .deb's out of it. Thanks.
I had the same problem and I consider myself far from an expert. But this is what got me started:
- [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)
- [http://crysol.inf-cr.uclm.es/node/325](http://crysol.inf-cr.uclm.es/node/325) (in spanish which I don't understand, but with google translate and the code I got it slowly)
- [http://www.linux.com/articles/60383](http://www.linux.com/articles/60383)

I studied the structure of some projects on launchpad such as Jokosher. That is the best way to learn. Find similar projects and study them. The file structure of your project is really important. For example do not mix images and python code.

Also by hanging around on #ubuntu-motu on irc, you'll learn a lot. I am afraid this is all I can help you.

Good luck,
Stani

---

### Post by javierfh on 2007-09-04
> **stani said:**
> I had the same problem and I consider myself far from an expert. But this is what got me started:
- [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)
- [http://crysol.inf-cr.uclm.es/node/325](http://crysol.inf-cr.uclm.es/node/325) (in spanish which I don't understand, but with google translate and the code I got it slowly)
- [http://www.linux.com/articles/60383](http://www.linux.com/articles/60383)

I studied the structure of some projects on launchpad such as Jokosher. That is the best way to learn. Find similar projects and study them. The file structure of your project is really important. For example do not mix images and python code.

Also by hanging around on #ubuntu-motu on irc, you'll learn a lot. I am afraid this is all I can help you.

Good luck,

Stani


Hello Stani, 

I sent you a question through the notepad, but dont know if you got it. 
I have tried your application and works nicely, but i seem to have problems with the exif data. Im not sure if destroys it or modifies the exif data, but i cant use that info anymore using for example gthumb or jalbum.

Can you tell me if it is a known problem or if you need more help or debugging,i will be glad to help in all i can.

Javi

---

### Post by stani on 2007-09-04
> **javierfh said:**
> Hello Stani, 

I sent you a question through the notepad, but dont know if you got it. 
What is notepad?
> 
I have tried your application and works nicely, but i seem to have problems with the exif data. Im not sure if destroys it or modifies the exif data, but i cant use that info anymore using for example gthumb or jalbum.

Can you tell me if it is a known problem or if you need more help or debugging,i will be glad to help in all i can.

Javi
Phatch uses PIL (Python Image Library) for loading and saving images. So if you can point me to the way how to save the exif info with PIL, I'll be happy to implement it. This means that if you don't know PIL and python you won't be able to help on it. But I hope you do ;-)
Stani

---

### Post by javierfh on 2007-09-04
> **stani said:**
> What is notepad?

Phatch uses PIL (Python Image Library) for loading and saving images. So if you can point me to the way how to save the exif info with PIL, I'll be happy to implement it. This means that if you don't know PIL and python you won't be able to help on it. But I hope you do ;-)
Stani

Ups sorry...i meaned launchpad ( too long playing with the phone :D )
Ill send you a link as private message to the place where the question was writen, i added there some links where you can see the problem i am reffering.
i dont know about python but maybe it is a good moment to try to start looking into it :)  but dont hold your breath :D

Anyway i hope that you let me know if i can help in any way.

Javi

P.S. thanks for nice application.

---

### Post by stani on 2007-09-05
I've answered you in launchpad.

Stani

---

### Post by stani on 2007-09-17
Finally I've found some time to put the frontpage online:
[http://photobatch.stani.be](http://photobatch.stani.be)

There is a download link for the deb installer at the bottom.

---

### Post by Nuafite on 2007-09-18
This looks exactly what I've been looking for - I came across your comment on 
[http://ubuntu-tutorials.com](http://ubuntu-tutorials.com). It looks georgeous too - a big plus. 

However when I downloaded and tried to launch I got this error:
Dependency is not satisfiable: python-central. 

I have python-central installed, and I re-installed it but got the same message. I'm not an expert in this so I presume I've gone about opening it in a naieve way?
Any pointers would be appreciated. Thanks, and good luck with this. It's badly needed.

---

### Post by stani on 2007-09-18
> **Nuafite said:**
> This looks exactly what I've been looking for - I came across your comment on 
[http://ubuntu-tutorials.com](http://ubuntu-tutorials.com). It looks georgeous too - a big plus. Thanks> However when I downloaded and tried to launch I got this error:
Dependency is not satisfiable: python-central. 

I have python-central installed, and I re-installed it but got the same message. I'm not an expert in this so I presume I've gone about opening it in a naieve way?
Any pointers would be appreciated. Thanks, and good luck with this. It's badly needed.
Can you try this: ```
sudo dpkg -i phatch.deb
```
and report back the output? (of course replace phatch.deb with the real name of the package.) What version of Ubuntu are you using?

Stani

---

### Post by Nuafite on 2007-09-19
Thank you very much for the quick response and the solution. I obviously have an outdated version of python-central on Ubuntu Edgy Eft. 

When I ran your suggested code I got

> Selecting previously deselected package phatch.
(Reading database ... 139539 files and directories currently installed.)
Unpacking phatch (from phatch_0.0.0.bzr.20070829.0-1_all.deb) ...
dpkg: dependency problems prevent configuration of phatch:
 phatch depends on python-central (>= 0.5.8); however:
  Version of python-central on system is 0.5.6ubuntu2.
dpkg: error processing phatch (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phatch

I presume it's a matter of updating the repositories, and I'll work that one out -- though I'm a bit low in diskspace and probably need to see to that first.
Many thanks again. I look forward to using Phatch and will mention it  on my Ubuntu Learner blog when I get a moment.

---

### Post by ernz on 2007-09-19
Remarkable. Not the most intuitive UI ever but I can really see this project going places. Superb! Keep up the very good work mate. P.S - correct usage of the phrase would be "whet your appetite" ;)

Thanks!

---

### Post by Nuafite on 2007-09-19
It seems I have the latest python-central for Ubuntu Edgy Eft. 

> python-central is already the newest version.

which would suggest I need to upgrade Ubuntu before I can use Phatch. Alas, that won't be till November. Will keep an eye on progress in the meantime and I've put a link from my blog [Ubuntu Learner]("http://ubuntu.philipcasey.com/")

---

### Post by stani on 2007-09-19
> **Nuafite said:**
> It seems I have the latest python-central for Ubuntu Edgy Eft. 



which would suggest I need to upgrade Ubuntu before I can use Phatch. Alas, that won't be till November. Will keep an eye on progress in the meantime and I've put a link from my blog [Ubuntu Learner]("http://ubuntu.philipcasey.com/")

Probably I could lower the required version. In fact my target was edgy & feisty. Could you send me a pm with your email. Than I send you a test .deb which you might try of course on your own risk.

Stani

---

### Post by stani on 2007-09-19
> **ernz said:**
> correct usage of the phrase would be "whet your appetite" ;)
Thanks, I fixed that.

---

### Post by Nuafite on 2007-09-20
Pardon my ignorance, but what is a pm?

It's very kind of you to make such an offer. It's generosity like this which drew me to Ubuntu in the first place. 

However, I'd suggest you keep the requirement you have. If someone like me really wants it (and I do) it will encourage us to upgrade to the newest Ubuntu, which I will in November. 

But many thanks. It's much appreciated.

---

### Post by digitalis_vulgaris on 2007-09-20
Site is looking very nice. You should put bigger download link, something like donation button.
I send you a blueprint with request for xcf support. What can I say... I become pain in the ... backyard. I also bombarding blender and gimp with demands ;)

Greetings...

---

### Post by stani on 2007-09-20
> **Nuafite said:**
> Pardon my ignorance, but what is a pm?private message> 

It's very kind of you to make such an offer. It's generosity like this which drew me to Ubuntu in the first place. 

However, I'd suggest you keep the requirement you have. If someone like me really wants it (and I do) it will encourage us to upgrade to the newest Ubuntu, which I will in November. 

But many thanks. It's much appreciated.In November you should upgrade to gutsy, not to feisty ;-) Seriously send me a private message with your email and we will make it work on edgy.

---

### Post by stani on 2007-09-20
> **digitalis_vulgaris said:**
> Site is looking very nice. You should put bigger download link, something like donation button.This is just a temporary page. It needs more work when I find the time.
> I send you a blueprint with request for xcf support. What can I say... I become pain in the ... backyard. I also bombarding blender and gimp with demands ;)

Greetings...
You are always free to ask. However not everything is possible. Phatch uses PIL and can only support file formats known by PIL. Unfortunately PIL doesn't support xcf, so phatch also doesn't. See the bottom of this page:
[http://www.pythonware.com/library/pil/handbook/index.htm](http://www.pythonware.com/library/pil/handbook/index.htm)

So you should put this request rather at the PIL developpers, but I doubt if they have time to implement it. I will have to cancel your blueprint request.

---

### Post by digitalis_vulgaris on 2007-09-21
I really thing site is OK. There is no need for world best site design.

I must say that I using Phatch every day and it's working like a dream. I can't wait new release with approved blueprints.

Can you add some effects (filters) like old photo, blink-blink flares, watercolor effect ... ? I like to help you with creating these effects.

---

### Post by stani on 2007-09-22
> **digitalis_vulgaris said:**
> I really thing site is OK. There is no need for world best site design.

I must say that I using Phatch every day and it's working like a dream. I can't wait new release with approved blueprints.Nice to hear!> Can you add some effects (filters) like old photo, blink-blink flares, watercolor effect ... ? I like to help you with creating these effects.For the first release I want to provide only basic actions. As the API is not stable yet, it could be much work to keep more actions updated. I'd like to see it like firefox: only the essential actions (such as resize, rotate, ...) and to offer the others for download through a community site.
But to answer your question... You need to be able to translate the concepts of this filter in python with PIL. PIL is very easy to learn, even if you don't know python. Otherwise, if you find on the web pil recipes, it is fairly easy for me to turn them in filter. So or get started with python & pil, or start googling for recipees...

Stani

---

### Post by dougleduck on 2007-09-22
This program sounds pretty good, does or will it have gamma correction on photos? I'm not sure if this fits with what you're doing as its a for batch photos but most apps dont have them. 

But then an auto gamma correction could be implemented I suppose it could be used for batch jobs. Probably not suitable but thought I'd suggest it.

---

### Post by SreckoMicic on 2007-09-23
Great piece of software.
Thank you so much for this!

---

### Post by stani on 2007-09-23
> **dougleduck said:**
> This program sounds pretty good, does or will it have gamma correction on photos? I'm not sure if this fits with what you're doing as its a for batch photos but most apps dont have them. 

But then an auto gamma correction could be implemented I suppose it could be used for batch jobs. Probably not suitable but thought I'd suggest it.There are no limits to what actions could be provided as long as they are achievable by python and pil. So if you are able to write a gamma correction plugin with python and pil, contact me, otherwise you have to find someone to do it for you.

---

### Post by dougleduck on 2007-09-23
My programming skills don't go that far I'm afraid. Good luck with the project. I look forward to trying it when you release it.

---

### Post by stani on 2007-09-23
@ SreckoMicic: Thanks!

> **dougleduck said:**
> My programming skills don't go that far I'm afraid. Good luck with the project. I look forward to trying it when you release it.

It is already released for ubuntu. Just go to the homepage [http://photobatch.stani.be](http://photobatch.stani.be) and press the 'free download' link.

---

### Post by stani on 2007-09-25
Hi,
I just wanted to mention that there has been a new release 0.0.bzr157. Phatch has been backported to be compatible with Edgy as well thanks to the patience of Philip Casey. New is that Phatch now has keyboard shortcuts and some small bugfixes. Also the website, which is hosted by zindep, has been extended with a download page. And usual websites are a project under construction...
Enjoy!
Stani

---

### Post by dougleduck on 2007-09-26
I obiously misread and thought you hadn't released it. Installed now and its a great little package, quickest I've seen for actually rotating images.

---

### Post by stani on 2007-10-02
> **dougleduck said:**
> I obiously misread and thought you hadn't released it. Installed now and its a great little package, quickest I've seen for actually rotating images.Thanks,
Stani

---

### Post by stani on 2007-10-23
Does anyone has problems on Gutsy? For me it works fine. Thanks for translating!
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

Italian, russian and danish are quite far. Maybe time for a last push, so Phatch completely supports dutch, french, italian russian and danish?

Thanks,
Stani

---

### Post by durand on 2007-10-23
I've been using it on gutsy from the start, no problems :)

---

### Post by PartisanEntity on 2007-10-24
I shall have to install it on Gutsy. Unfortunately I have been very busy lately and have not been able to help with translations at all.

---

### Post by bvanaerde on 2007-10-26
Installing it on Gutsy as I speak.
I'll let you know if it works :)

edit: no problems so far. Install went smoothly, and I just did a resize & save batch without a problem.

---

### Post by The Pinny Parlour on 2007-10-28
I just installed it.  Not impressed much by it as I can't understand how to use it.

No instructions, can't work out how to resize an image, (resize a canvas yes).  It has many nice features to be sure, "where's the resize an image" button????

Have install Nautilus add-on, works a treat.  

To the producer of the program, needs more work into making it easier to understand and use.  I still can't work out how to resize an image using your program.

Regards,

---

### Post by stani on 2007-10-28
> **The Pinny Parlour said:**
> I just installed it.  Not impressed much by it as I can't understand how to use it.

Yes documentation sucks at the moment. I am sorry for that. As phatch has now some enthusiastic users, maybe some want to help with documentation so I can focus on developping it further? I accept all kinds of documentation (openoffice, html, whatever...) preferably with screenshots. This is your opportunity to contribute back to phatch! A lot of you have already done so with translations, but documentation is now also getting important. Please contact me before you start with what you want to do so I can coordinate better.
However Pinny Parlour, I gave some short instructions in the first post:
With + you can add actions, be sure to include a save action in the end. (Save as '<filename>_phatch' means: the manipulated version of 'image.jpg' will be saved as 'image_phath.jpg'. This is also true for '<folder>_phatch' etc...) You can drag and drop actions to order them. To change values select an item and do a second single mouse click on the value. To disable an action, select it and single click (the v will become a x). You can execute your action list on any number of files or folder by pressing Execute (second button on toolbar or under menu tools)

> **The Pinny Parlour said:**
> No instructions, can't work out how to resize an image, (resize a canvas yes).  It has many nice features to be sure, "where's the resize an image" button????
What you need is "image scale" followed by a "save" action. ("scale canvas" will crop or add a border.) Afterwards drag and drop some files and/or folders on phatch, and phatch will start its job! The advantage of phatch to the nautilus extension is you can define a whole list at once instead of just one action. For example you can resize your pictures, add rounded corners and drop a shadow behind it. With nautilus or imagemagick, it is either not possible or you have to do it step by step. Please be a bit patient. Your current frustration, which I respect, is due to a lack of documentation. Once you understand phatch, you will love it.

For me as an open source developper it is extremely important to get as many people contribute as possible. See for example:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)
Only this can launch a new application well. If a project stays the work of one person, development will be very slow and will demotivate the developper. (I actually develop some other open source stuff as well.) 

So how about you? Would you be willing to make some documentation (text+screenshots, just a little bit would be nice already) if I answer all your questions? 

Please anyone who enjoyed using phatch, let's do everybody a little bit to get nice documentation!

---

### Post by durand on 2007-10-28
I'll try to work on some documentation, maybe as a mediawiki? I've got a lot of homework from school at the moment, but I'll do what I can during weekends.

---

### Post by stani on 2007-10-28
> **durand said:**
> I'll try to work on some documentation, maybe as a mediawiki? I've got a lot of homework from school at the moment, but I'll do what I can during weekends.
Great! Please send me a private message with your email. (I always have difficulty to match forum names with emails.) I don't have such good experience with wiki. Most of the time it took me more work than what it saved me. I review all text to be sure no mistakes are made. Also I prefer to choose something like asciidoc which makes generating it in different languages and formats easy. However you don't have to bother about that. Just send me it in the way it is most convenient for you. But please email me which docs or tutorial you want to make.

---

### Post by richardjennings on 2007-11-02
I am very impressed!

I found myself needing to batch resize over 800 high res jpegs.

I thought this was going to be difficult and time consuming.

Google search. 
Gave Phatch a try

Initially slightly puzzled by the UI.
Used the file / open option to try and select the folder containing the images.

Hit the + button. Selected image size. 
Changed values to 25%

Still a little confused how to add the images, so I decided to use the execute option to see what happens.

Tells me I need to add a save action. Told me phatch would do this for me. *yay*

Now I get the option to choose the folder containing the jpgs.

I select the folder & watch as the app starts to resize my images.

I was concerned that the resized images might be saved somewhere unintuative, as the save filter didnt seem easy to configure (i left it default)

Found pics where in a folder named copy_ 

They were all exactly how I wanted them.

Phatch took around about 4mins on my machine to process 500mb of images.

Job Done!

Very impressed.

All in all took me around 10mins to search for, install, use the app and marval at the finished result.

What a brilliant application!

---

### Post by nebriv on 2007-11-07
Ok I am very interested in this but I am unable to install it!? I am kind of new to ubuntu, but am familiar with .deb packages. 

I downloaded the .deb and it says it can't find certain dependencies, I ran it in the terminal so I could copy and paste the output.

ben@ben-desktop:~/Desktop$ sudo dpkg -i phatch_0.0.bzr157-1_all.deb
Selecting previously deselected package phatch.
(Reading database ... 132306 files and directories currently installed.)
Unpacking phatch (from phatch_0.0.bzr157-1_all.deb) ...
dpkg: dependency problems prevent configuration of phatch:
 phatch depends on python-wxgtk2.8 | python-wxgtk2.6; however:
  Package python-wxgtk2.8 is not installed.
  Package python-wxgtk2.6 is not installed.
 phatch depends on python-wxversion; however:
  Package python-wxversion is not installed.
dpkg: error processing phatch (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phatch

I looked snayptic for python-wxgtk2.8 but I couldn't find it. Oh by the way I just did a clean install onto gusty.

Please help me!


EDIT:

fixed useing this bit of code

[http://openpaste.org/en/3734/inline/](http://openpaste.org/en/3734/inline/)

---

### Post by durand on 2007-11-08
You could have just done sudo apt-get -f install on its own....oh and use gdebi to install it. Double click on the deb file and it will open the "installer" which works really well.

---

### Post by stani on 2007-11-08
> **nebriv said:**
> Ok I am very interested in this but I am unable to install it!? I am kind of new to ubuntu, but am familiar with .deb packages. 

I downloaded the .deb and it says it can't find certain dependencies, I ran it in the terminal so I could copy and paste the output.

ben@ben-desktop:~/Desktop$ sudo dpkg -i phatch_0.0.bzr157-1_all.deb
Selecting previously deselected package phatch.
(Reading database ... 132306 files and directories currently installed.)
Unpacking phatch (from phatch_0.0.bzr157-1_all.deb) ...
dpkg: dependency problems prevent configuration of phatch:
 phatch depends on python-wxgtk2.8 | python-wxgtk2.6; however:
  Package python-wxgtk2.8 is not installed.
  Package python-wxgtk2.6 is not installed.
 phatch depends on python-wxversion; however:
  Package python-wxversion is not installed.
dpkg: error processing phatch (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phatch

I looked snayptic for python-wxgtk2.8 but I couldn't find it. Oh by the way I just did a clean install onto gusty.

Please help me!


EDIT:

fixed useing this bit of code

[http://openpaste.org/en/3734/inline/](http://openpaste.org/en/3734/inline/)

You need to have the universe repositories enabled. 
See System>Administration>Software Sources

Your fix of code is not recommended as you won't get updates.

---

### Post by kikke on 2007-11-08
Excellent app!

---

### Post by PartisanEntity on 2007-11-11
stani, Phatch just gets better and better, great work.

---

### Post by kikke on 2007-11-14
I have a problem with Phatch. After adding watermark to the list, it doesn't appear. 

```

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/gui.py", line 217, in on_menu_edit_add
    self.tree.append_form_by_label_to_selected(label)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 209, in append_form_by_label_to_selected
    return self.append_form_by_label(item,label)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 113, in append_form_by_label
    return self.append_form(self.form_factory[label](),item)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 103, in append_form
    self.import_form(item,form)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 156, in import_form
    self.treeLabel(label,value_as_string))
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 88, in treeLabel
    self.CtrlMixin._to_local(value)]) 
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 0: ordinal not in range(128)

```

If I add another item, like invert, the watermark is appear in the list.
But it's unusable because it says when I try to browse the watermark:
```

/usr/lib/python2.5/site-packages/phatch/core/translation.py:41: UnicodeWarning: Unicode unequal comparison failed to convert both arguments to Unicode - interpreting them as being unequal
  if x != _x:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/popup.py", line 220, in OnBrowse
    wildcard        = self.GetWildcard(),
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/popup.py", line 246, in GetWildcard
    self._all_files+'|*'])
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)

```

I want to use an utf-8 .mo file for hungarian translation, I made it from nl translation.

---

### Post by kikke on 2007-11-14
[SIZE="2"]I've found a patch for phatch![/SIZE]
:)

If you found a bug like I wrote in my previous post, use the following patch. 

Insert the following lines (with red) into app.py, after the import section

```

[COLOR="Silver"]
# -*- coding: UTF-8 -*-
#License: latest GPL

import gettext, locale, os, optparse, sys
from data.info import INFO[/COLOR]

[COLOR="Red"]reload(sys)
sys.setdefaultencoding('utf-8')[/COLOR]

```

This solve the internationalization problem. I hope this help!

---

### Post by stani on 2007-11-21
> **kikke said:**
> [SIZE="2"]I've found a patch for phatch![/SIZE]
:)

If you found a bug like I wrote in my previous post, use the following patch. 

Insert the following lines (with red) into app.py, after the import section

```

[COLOR="Silver"]
# -*- coding: UTF-8 -*-
#License: latest GPL

import gettext, locale, os, optparse, sys
from data.info import INFO[/COLOR]

[COLOR="Red"]reload(sys)
sys.setdefaultencoding('utf-8')[/COLOR]

```

This solve the internationalization problem. I hope this help!

Hmmm, this might work but is not a recommended solution. Phatch should be fixed in a better way. I try to keep Phatch 100% bug free. So please file a bug on launchpad and attach the .mo file you are using. I'll try to reproduce it and fix it on my system.

---

### Post by arigram on 2007-11-25
Can I use an image as a Watermark and if yes, how so?
I can't seem to figure that part out. Clicking and highlighting the Mark option of the Action doesn't seem to give me any indication of what I should do.

A basic manual is very much needed, indeed.

Since this is professionally important to me, I will make you a deal:
explain me how and I will do the greek translation. :)

---

### Post by stani on 2007-11-26
> **arigram said:**
> Can I use an image as a Watermark and if yes, how so?
I can't seem to figure that part out. Clicking and highlighting the Mark option of the Action doesn't seem to give me any indication of what I should do.

A basic manual is very much needed, indeed.

Since this is professionally important to me, I will make you a deal:
explain me how and I will do the greek translation. :)

Quite some people start blogging already about phatch. All together these blogs form already a nice manual. Unfortunately no one contacted me to give some docs back. I count on the users for sending me a manual, translations, ... which I can distribute. OK, as you will do the greek translation, I explain you the watermarking in detail:

* Press the + button and choose watermark.
- Select the first field, where you can specify a filename by typing or by pressing left on the browse button
- Select field 2: Here you can select the method: by offset, scale or tiling. If you give a positive offset it is taken from left, a negative for right. Same for top and bottom. (These you can set in filed 3 and 4) When you choose tile, the photo will be covered all over with multiple watermarks.
- Select last field: here you can select the opacity from 0(completely transparent)-100(completely opaque).

* Press the + button and choose "save image".

Then drag and drop a folder and/or files on phatch... and there you go. You can save your watermark action list by File>Save or the save button. You can use View>Droplet for drag & drop operations which takes less space if you prefer. That's all.

So when you will finish the greek translation ;-) ? If you do a lot of translation, I recommend you use poedit which is faster. Launchpad is more convenient to do small amounts of translation.

---

### Post by stani on 2007-11-26
> **kikke said:**
> I have a problem with Phatch. After adding watermark to the list, it doesn't appear. 

```

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/gui.py", line 217, in on_menu_edit_add
    self.tree.append_form_by_label_to_selected(label)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 209, in append_form_by_label_to_selected
    return self.append_form_by_label(item,label)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 113, in append_form_by_label
    return self.append_form(self.form_factory[label](),item)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 103, in append_form
    self.import_form(item,form)
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 156, in import_form
    self.treeLabel(label,value_as_string))
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/treeEdit.py", line 88, in treeLabel
    self.CtrlMixin._to_local(value)]) 
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 0: ordinal not in range(128)

```

If I add another item, like invert, the watermark is appear in the list.
But it's unusable because it says when I try to browse the watermark:
```

/usr/lib/python2.5/site-packages/phatch/core/translation.py:41: UnicodeWarning: Unicode unequal comparison failed to convert both arguments to Unicode - interpreting them as being unequal
  if x != _x:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/popup.py", line 220, in OnBrowse
    wildcard        = self.GetWildcard(),
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/lib/popup.py", line 246, in GetWildcard
    self._all_files+'|*'])
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)

```

I want to use an utf-8 .mo file for hungarian translation, I made it from nl translation.

This was an important bug as it affected every language with non-ascii characters. I have released a fix for this in bazaar. (rev 161) I will make a deb installer soon. Fore more info see: [https://bugs.launchpad.net/bugs/165208](https://bugs.launchpad.net/bugs/165208)

I think it is best to start a translation from the pot source file. Email me if you need help.

---

### Post by arigram on 2007-11-26
> **stani said:**
> 
* Press the + button and choose watermark.
- Select the first field, where you can specify a filename by typing or by pressing left on the browse button

Thank you for the reply.
My problem is with the above first field which doesn't give me a button to press or display anything by clicking and typing on it:

[IMG]http://i184.photobucket.com/albums/x247/arigram/Screenshot-UnsavedActionList-Phatch.png[/IMG]

I will start working on the translation ASAP. It will be my first, so don't hold your breath for too long. ;)

---

### Post by stani on 2007-11-26
> **arigram said:**
> Thank you for the reply.
My problem is with the above first field which doesn't give me a button to press or display anything by clicking and typing on it:

Strange. Which version of ubuntu, phatch, etc.. are you using? Could you start phatch in a terminal and paste me the output?

---

### Post by arigram on 2007-11-26
> **stani said:**
> Strange. Which version of ubuntu, phatch, etc.. are you using? Could you start phatch in a terminal and paste me the output?

I am using Ubuntu 7.10 Gutsy Gibbon amd64 with the latest nvidia drivers, compiz version, etc through the "official channels". I also have customized the GUI a bit through Appearance.
Phatch is version 0.0.bzr156   (a most bizarre version number!)
I notice that when I click on the said action field, a small part of the button appears while it remains clickable but not operational:

[IMG]http://i184.photobucket.com/albums/x247/arigram/Screenshot-UnsavedActionList-Pha-1.png[/IMG]

If I start phatch via the CLI, I just get the GUI immediately with no text output even when I close it. As I am a n00b, that's all I can do for now.

---

### Post by stani on 2007-11-26
> **arigram said:**
> I am using Ubuntu 7.10 Gutsy Gibbon amd64 with the latest nvidia drivers, compiz version, etc through the "official channels". I also have customized the GUI a bit through Appearance.
Can you try to switch to the default appereance and see what happens?
> 
Phatch is version 0.0.bzr156   (a most bizarre version number!)
I notice that when I click on the said action field, a small part of the button appears while it remains clickable but not operational:What happens when you maximize the phatch window?
> 
If I start phatch via the CLI, I just get the GUI immediately with no text output even when I close it. This is a good sign. It means there are no errors. Maybe it is due to your appearance settings. In that case I need to have all the files to reconstruct your appearance on my computer here.
> As I am a n00b, that's all I can do for now.No problem. Let's see how far we go.

---

### Post by arigram on 2007-11-26
I tried the Human and Clearlooks themes through the Appearance dialog, yet the problem persists. I am not sure what else to try as everything else seems normal.

---

### Post by stani on 2007-11-27
> **arigram said:**
> I tried the Human and Clearlooks themes through the Appearance dialog, yet the problem persists. I am not sure what else to try as everything else seems normal.
What happens when you maximize phatch?
Which version of python-wxgtk do you have installed? (look in system>administration>synaptic)?

---

### Post by arigram on 2007-11-27
> **stani said:**
> What happens when you maximize phatch?
Which version of python-wxgtk do you have installed? (look in system>administration>synaptic)?

Ok Stani, problem has been solved!
I had the earlier (2.6) version of the python-wxgtk library instead of the current 2.8 one and was a click away to install it through Synaptic.
If you didn't mention it, it would have taken me some time to figure out the problem as I am not yet completely accustomed to the Linux way of thinking (even though it is logical).
Damn it and was forced to do the translation!
Which btw is almost done, I just have to find and review certain terms, especially highly technical and mathematical ones. I just have to take a look in the greek Gimp translation.
The irony of it all is that I have always run my computers in english and find the greek terminology alien and confusing...

---

### Post by stani on 2007-11-27
> **arigram said:**
> Ok Stani, problem has been solved!
I had the earlier (2.6) version of the python-wxgtk library instead of the current 2.8 one and was a click away to install it through Synaptic.
If you didn't mention it, it would have taken me some time to figure out the problem as I am not yet completely accustomed to the Linux way of thinking (even though it is logical).
Nice it works for you!> 
Damn it and was forced to do the translation!
Which btw is almost done, 
Wow! You are as fast as batching your photos ;-)> I just have to find and review certain terms, especially highly technical and mathematical ones. I just have to take a look in the greek Gimp translation. Feel free to ask me here if you don't understand something. It might be usefull for other translators as well.
> 
The irony of it all is that I have always run my computers in english and find the greek terminology alien and confusing...For sure the rest of Greece will love you!

---

### Post by stani on 2007-11-27
> **arigram said:**
> 
Damn it and was forced to do the translation!
Which btw is almost done, I just have to find and review certain terms, especially highly technical and mathematical ones. I just have to take a look in the greek Gimp translation.

I checked what you couldn't translate:

- invalid literal: it means when someone entered a wrong formula for example 120.5 pixels, as pixels only can be integer numbers

- integer: integer number such as 1,2,3,...

- float: numbers with floating point such as 3.1415

I hope this helps you and make greek complete!

---

### Post by stani on 2007-11-27
I have updated the first post and added also some links to the most extensive reviews of phatch. I am very impressed with the translation work of arigram who added greek almost complete in one day! Italian and German are also almost finished. Any volunteers to complete it? If you don't understand some phrases, don't be afraid to ask. I'll gladly explain.

---

### Post by arigram on 2007-11-27
> **stani said:**
> I checked what you couldn't translate:

- invalid literal: it means when someone entered a wrong formula for example 120.5 pixels, as pixels only can be integer numbers

- integer: integer number such as 1,2,3,...

- float: numbers with floating point such as 3.1415

I hope this helps you and make greek complete!

Thank you for taking the time to check on the translation.
I still need to go back and change a few things I have
written as their meaning changes when seen in context
and not as single words. One reason I mentioned Gimp was
to see what words they have used for translation as one
term could be described differently and often not literally.
There needs to be a common standard so terms wouldn't
change with every application and be confusing. Some
are quite silly or ugly sounding, some of the reasons I prefer
my desktop in english.
The terms you mentioned is an example of the trouble I had,
as I am not a mathematician or programmer so I don't know
their greek equivalents and can't trust online dictionaries.
I think Gimp's translation will be all I will need.

As far as being a greek national hero, well, I heard they are
preparing a parade tomorrow where the president is gonna
be giving me honors and medals and a large harem.

I think you have done a marvelous job with Phatch and although it
could definitely grow further, I think it might become an important
and popular tool. I am a photographer and needed a tool to help me 
display my work on my website. I still haven't had time to play much with it
and I was planning to report after I had some experience, but
there are things I could propose, including new actions if you
are interested and not busy enough.

---

### Post by arigram on 2007-11-29
I have reviewed the translation and corrected quite a few strings.
The problem with translation is that not all languages work similarly and words are not always transferable one-by-one. A lot of content is only applicable to certain situations and then often a term is subject to its surrounding syntax, translator's aesthetics and language structure such as word gender, plurality, conjugation, etc. For example, I had trouble translating the words Batch, Action and List which are basic terms of Phatch, yet can be translated in more than one ways and there is not a present standard of translation at the moment it seems. Even Gimp is only half translated and questionably if you ask me. I have asked three friends of mine to review my translation which save for some "bugs" is complete.
Btw, what does "Apply for future errors " mean, as I can't find a reference to it inside the Phatch application?

But enough of translation talk, that is subject of a different thread.
Want to hear of some suggestions specific to Phatch?

---

### Post by stani on 2007-12-05
> **arigram said:**
> 
Btw, what does "Apply for future errors " mean, as I can't find a reference to it inside the Phatch application?Normally you shouldn't get this message. When an error occurs (phatch bug, bad image, ...) you will get a message that an error occur with the option to ignore, skip or abort. Your choice can be applied to future errors.
> **arigram said:**
> 
But enough of translation talk, that is subject of a different thread.
Want to hear of some suggestions specific to Phatch? Of course, but I do not make any promises to implement them. Feature requests can be asked as a blueprint on launchpad.

---

### Post by stani on 2007-12-05
There is a new version for phatch to download (0.0.bzr164). It fixes an important bug for non-english languages. It is built on gutsy, so I don't know if the deb installer will still work on feisty.
A lot of people did great translations. Anyone who translated and is not listed in the help about dialog box should contact me so I can add him or her. All translations till now ship with this version of phatch. A special thanks to Marcos for translating phatch 100% in galician! I'd like to see more completed languages...spanish, german and italian is almost there. 
I am in contact with Debian developpers who might package phatch, which could mean by consequence that phatch becomes available in next ubuntu release (hardy).
So please test if phatch works ok in your local language. I don't want any bug to survive in phatch!
Stani

---

### Post by stani on 2007-12-06
Phatch will land in the universe. I am working together with the Debian PAPT team to bring Phatch in debian Unstable. After that it will be imported in the ubuntu universe repostories so installing phatch will be as simple as:
```
sudo apt-get install phatch
```
But we are not there yet. If you want to keep updated, subscribe yourself here:
[https://bugs.launchpad.net/ubuntu/+bug/145193](https://bugs.launchpad.net/ubuntu/+bug/145193)

---

### Post by stani on 2007-12-07
For the diggers among you, give phatch an extra boost and digg it:
[http://digg.com/linux_unix/Phatch_batch_photo_power_without_bash_hassle_2](http://digg.com/linux_unix/Phatch_batch_photo_power_without_bash_hassle_2)

---

### Post by arigram on 2007-12-09
**Workflow.**
As a professional photographer and graphic artist I maintain a website with my work.
My workflow is such:

Film Photographs:
1) Print with analog enlarger.
2) Scan.
3) Adjust Image with Gimp (Tonallity, Brightness, Crop, Perspective, etc) while retaining  original analog print characteristics (no extra manipulation).
4) Save as Tiff for the archive.
5) Rescale and save as a Jpeg copy for the website.
6) Place each jpeg on folders according to the website category (subject matter).
7) Upload each jpeg via the Website Frontend.
8) Name each with english and greek titles and place them in corresponding gallery categories via the Website Frontend.
With Digital Artwork its the same same workflow from number 4 unless its digital photographs that almost always need some adjustment with the Gimp.
I don't do digital printing but I can imaging the need for a workflow that automatically processes images that will end up being printed.

Anything to save me time and effort and free me from repetition is very much appreciated.
Batch processing is an important aspect of a digital imaging workflow and has to be comprehensive and easy to use.
Phatch has all the potential to be the very best Batch Processor.

_**General**_

**- Scheduling.**
Schedule execution of a single or multiple action lists. Able to run multiple schedules.Schedule by every boot, date, time, new files.
New files meaning to watch one or more directories for new files added. Set the number of files as a threshold by value number. For example, if value is 1, the batch process begins everytime a new file is added to the watched directory, but if the value is 10, then wait until 10 files are placed before doing anything.
Useful when you have a routine workflow such updating a website, preparing images for presentation or print, updating the database or portfolio, etc.
**- Action Value Presets.**
Ability to save values of Actions as presets to be selected in future Actions by name and/or value.
E.g. a set of preset values of color adjustments for a certain type of film or digital sensor, a variety of watermarks, different frames, blurring presets, often used colors, etc
**- Tabs.**
So you can load multiple action lists, which you can select by tab press.
When in droplet mode, you can tell the action list by either a number displayed at one corner or an action list's name under the icon. By clicking on the number or the name, you can change the action list. Also able to do so by means of a pull-down context menu.
Useful when you have different kinds of batch processes to execute, such as processing the same images for printing and for web display. Saves a bit of time and organises the workflow better.
**- Add Actions.**
Keep the Add Actions dialog open and add Actions by means of doubleclicking and/or drag and dropping.

_**Present Actions &#8211; New Features**_
**- Rotate.**
Free Rotation by value.
Useful when you know that all the images are titled by a cretain amount due to scanning, etc.
**- Watermark**.
Add border to watermark, adjust edges (sharp/rounded), color of border.
**- Save.**
Folder Arrangement: Save images to different folders based on their characteristics (type, size, colors, etc) and/or comment tags (camera, lens, subject matter, etc). If folder doesn't exist, create one.

_**New Actions - General**_

**- Include/Exclude Files.**
Automatically include and/or exclude files from the set directory(ies) by:
name, type, color space, date modified, size, exif information, tag/comment.
By placing this Action in the beginning of the List you can include/exclude or images, but by placing it once or multiple times among the List, you can limit certain Actions to certain files even after they were processed by other Actions. For example you can adjust the brightness to all files but limit the resizing to only the jpeg files.
**- Comment Editor.**
Edit and create comment and Exif tags to add to the files, such as photographer, camera, film, subject type, etc. 
Able to add a Gnome Nautilus Emblem.
Useful when working with images that do not contain exif information (film photos, computer graphics, etc) but also able to add more information when exif is present.
**- FTP Transfer.**
Transfer files to another location by ftp.
**- Print.**
Send processed batch to a printer to be printed en masse.
**- PDF Creator.**
Create a PDF file from the image batch. You can choose how many images a page would fit, background color, offset and alignment, text above or below (image label from filename or custom) and compression/quality.
Useful for building quick portfolios, draft indexes, printing tests, etc.

**_New Actions &#8211; Adjustment_**

**- Brightness, Contrast, Saturation.**
**- Cropping.**
Screen Edge Values, Offset.
**- Color Adjustment.**
RGB/CMYK. Hue, Saturation, Brightness.
[B]- Sharpening.
- Blur.[/B]
**- Lens Distortion.**
Fix or exaggerate distortions made by the camera lens.
Barrel or pinch, offset.
Useful when you know that a certain lens or focal legth creates distortion (eg. cheap zoom lenses) and which you have used in the past a lot or keep using.

**_New Actions &#8211; Effects._**
[B]
- Digital Noise/Film Grain.[/B]
Film Grain is different from Digital Noise. Its size and crystalic structure is relevant to the film type and ISO speed set. It is also only visible in non pure white-black tones.
**- Colorization.**
Colorize whole image by selected color from a palette. Limit the  colorization to dark/gray/white values. This way one can simulate chemical toners (sepia, gold, selenium, etc) that can limit their effect in certain values. By combining these actions one can simulate split toning effects (combining two or more chemical toners to achieve special colors and effects).
**- Frame.**
Add a frame around the image. Simple line with control on thickness and color or use a graphic file with transparency which will form the frame. Choose inside/directly/outside placement and transparency. 
&#8220;Destructive&#8221; option: subtract from the main image using the frame so you can create tear and cut effects (or darkroom printing). 
**- Combine Images.**
Combine images vertically, horizontally (to create panorama) or by rows/columns (to create index/contact sheet).


That's it for now. Its quite a lot!
Of course the reason I made the list public is in hopes not just to increase your workload but to attract others to create Actions and develop the application.
After all this is Open Source world.

---

### Post by stani on 2007-12-19
> **arigram said:**
> 
_**General**_

**- Scheduling.**
Schedule execution of a single or multiple action lists. I was also thinking of scheduling. Therefore you'll need to wait for Phatch 0.2, which will hopefully supply a phatch command line interface. However scheduling will not be a task for Phatch. Linux has a great tool for that: cron. No way I can beat that. If you want a nice GUI for it, try:
```
sudo apt-get install gnome-schedule
```
[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)> 
**- Action Value Presets.**
Ability to save values of Actions as presets to be selected in future Actions by name and/or value.
E.g. a set of preset values of color adjustments for a certain type of film or digital sensor, a variety of watermarks, different frames, blurring presets, often used colors, etcI agree with this. Please file a blueprint for presets. My idea is that you can use saved action list as an action itself. This can contain some locked attributes while others could still be changed.> 
**- Tabs.**
So you can load multiple action lists, which you can select by tab press.
When in droplet mode, you can tell the action list by either a number displayed at one corner or an action list's name under the icon. By clicking on the number or the name, you can change the action list. Also able to do so by means of a pull-down context menu.
Useful when you have different kinds of batch processes to execute, such as processing the same images for printing and for web display. Saves a bit of time and organises the workflow better.I doubt about this one. You should see Phatch as a tool to create action lists. For professional execution you will use the console version. Also it only makes sense if the opened action lists in Phatch needs to be applied simultaneously.In that sense people will mostly work with one action list and the notebook interface only adds clutter.> 
**- Add Actions.**
Keep the Add Actions dialog open and add Actions by means of doubleclicking and/or drag and dropping.File a blueprint for this one. I have to think about it. > 

_**Present Actions – New Features**_
**- Rotate.**
Free Rotation by value.
Useful when you know that all the images are titled by a cretain amount due to scanning, etc.File a blueprint for it. If the image rotates should the size follow the bounding box?> 
**- Watermark**.
Add border to watermark, adjust edges (sharp/rounded), color of border.Can you give visual examples? It would any way only be possible to add a rectangular border.> 
**- Save.**
Folder Arrangement: Save images to different folders based on their characteristics (type, size, colors, etc) and/or comment tags (camera, lens, subject matter, etc). If folder doesn't exist, create one.This is already possible. Just use any <variable>. For more info see: [http://photobatch.wikidot.com/variables](http://photobatch.wikidot.com/variables)> 

_**New Actions - General**_

**- Include/Exclude Files.**
Automatically include and/or exclude files from the set directory(ies) by:
name, type, color space, date modified, size, exif information, tag/comment.
By placing this Action in the beginning of the List you can include/exclude or images, but by placing it once or multiple times among the List, you can limit certain Actions to certain files even after they were processed by other Actions. For example you can adjust the brightness to all files but limit the resizing to only the jpeg files.File as blueprint.> 
**- Comment Editor.**
Edit and create comment and Exif tags to add to the files, such as photographer, camera, film, subject type, etc. 
Able to add a Gnome Nautilus Emblem.
Useful when working with images that do not contain exif information (film photos, computer graphics, etc) but also able to add more information when exif is present.I still need to find the right python exif library which is cross platform. Especially writing is tricky, read-only will be more easy.> 
**- FTP Transfer.**
Transfer files to another location by ftp.File as a blue print.> 
**- Print.**
Send processed batch to a printer to be printed en masse.File as a blueprint.> 
**- PDF Creator.**
Create a PDF file from the image batch. You can choose how many images a page would fit, background color, offset and alignment, text above or below (image label from filename or custom) and compression/quality.
Useful for building quick portfolios, draft indexes, printing tests, etc.
Phatch can only deal with single images. This would be another software. Maybe you can try:
```
sudo apt-get install photoprint
```> 

**_New Actions – Adjustment_**

**- Brightness, Contrast, Saturation.**File as a blue print> 
**- Cropping.**The action "canvas size" can already do this.> 
Screen Edge Values, Offset.What do you mean with that?> 
**- Color Adjustment.**
RGB/CMYK. Hue, Saturation, Brightness.
[B]- Sharpening.
- Blur.[/B]File blueprint.> 
**- Lens Distortion.**
Fix or exaggerate distortions made by the camera lens.
Barrel or pinch, offset.
Useful when you know that a certain lens or focal legth creates distortion (eg. cheap zoom lenses) and which you have used in the past a lot or keep using.
You can file it as a blueprint but I don't know how to do this in PIL.> 
**_New Actions – Effects._**
[B]
- Digital Noise/Film Grain.[/B]
Film Grain is different from Digital Noise. Its size and crystalic structure is relevant to the film type and ISO speed set. It is also only visible in non pure white-black tones.
**- Colorization.**
Colorize whole image by selected color from a palette. Limit the  colorization to dark/gray/white values. This way one can simulate chemical toners (sepia, gold, selenium, etc) that can limit their effect in certain values. By combining these actions one can simulate split toning effects (combining two or more chemical toners to achieve special colors and effects).
**- Frame.**
Add a frame around the image. Simple line with control on thickness and color or use a graphic file with transparency which will form the frame. Choose inside/directly/outside placement and transparency. 
“Destructive” option: subtract from the main image using the frame so you can create tear and cut effects (or darkroom printing). File them all seperately as a blueprint.> 
**- Combine Images.**
Combine images vertically, horizontally (to create panorama) or by rows/columns (to create index/contact sheet).Same comment as earlier. Phatch is only for single images. Look at photoprint... and bug its author ;-)
> 


That's it for now. Its quite a lot!Haha, you realize. No problem, you can always ask, but no promises. Of course it would be nice if you would help me with the documentation. This discussion goes quite detailed and I prefer strongly if you would use the brand new Phatch forums for that:
[http://photobatch.wikidot.com/forum:start](http://photobatch.wikidot.com/forum:start)

Just get yourself a wikidot account and you can help me with the documentation right away. A lot of actions still need their own page. Just click on Actions and you will be able to create the page. As an example look at the Watermark Action.

> 
Of course the reason I made the list public is in hopes not just to increase your workload but to attract others to create Actions and develop the application.
After all this is Open Source world.
To extract more developers. Phatch needs more exposure and good documentation and structure. There is still a lot where you can help. Developers might follow...

---

### Post by digitalis_vulgaris on 2007-12-20
Hi Stani,
I just do some tests with tif rgb to tif cmyk conversion, using Phatch 0.0.156
I create tif image 1x1cm, 300 dpi, RGB and try to convert this file into tif CMYK image. Results were very funny. Now I have tif CMYK, 4x4cm, 72 dpi, with totally mess up colors. :lolflag:

---

### Post by stani on 2007-12-20
> **digitalis_vulgaris said:**
> Hi Stani,
I just do some tests with tif rgb to tif cmyk conversion, using Phatch 0.0.156
I create tif image 1x1cm, 300 dpi, RGB and try to convert this file into tif CMYK image. Results were very funny. Now I have tif CMYK, 4x4cm, 72 dpi, with totally mess up colors. :lolflag:

In that case you should file a bug report on launchpad. In the new phatch 0.1.bzr184 there is a menu entry for it under help. In the bug report you need to attach your image and the action list. Also mention the program with which you checked it afterwards.

---

### Post by digitalis_vulgaris on 2007-12-20
Anyway, this is a great application, great idea. Whan pass puberty it's gone a be essential application on every linux...

---

### Post by stani on 2007-12-20
> **digitalis_vulgaris said:**
> Anyway, this is a great application, great idea. Whan pass puberty it's gone a be essential application on every linux... Luckily the logo is already passed puberty ;-) Can you still file a bug report so I can reproduce your problem? 
Also Phatch is refused at the moment for Ubuntu/Debian because of its actions icons which are not released under the gpl. Is there someone willing to create 9 icons of one fixed size? Or does someone have a good suggestion to replace them? I need other ones, otherwise Phatch can not be part of Ubuntu Hardy.

These are the actions:

Color Actions
    * Convert Mode - Convert the color mode of an image.
      (greyscale, RGB, RGBA or CMYK)
    * Invert - Invert the colors of the image (negative).

Effect Actions
    * Round - Round or crossed corners with variable radius and corners.
    * Shadow - Drop a blurred shadow under a photo with variable position, blur and color.
    * Watermark - Apply a watermark image with variable placement (offset, scaling, tiling) and opacity.

File Actions
    * Save - Save an image with variable compression in different types.

Image Actions
    * Canvas Size - Crop the image or put it on a bigger canvas without resizing the image.
    * Image Size - Scale an image with different resample filters.
    * Transpose - Flip or rotate an image by 90 degrees.

More info at [http://photobatch.wikidot.com/actions](http://photobatch.wikidot.com/actions)

Thanks in advance,
Stani

---

### Post by digitalis_vulgaris on 2007-12-20
How did you remember that you need icons when I submit my post?! Hahahahahaha
Ok, if you can wait a little, I could help you with this problem. I don't have a time this mount, but maybe I could do it in january.

---

### Post by digitalis_vulgaris on 2007-12-20
I propose to SITE MODERATORS that make this topic sticky. There isn't more important subject for Ubuntu Community than development of great applications. Great applications are real value of Ubuntu, and best way of fight against kapitalistic and monopolistic tendentions.

---

### Post by kgriffin on 2008-01-04
I just used it to make all my wedding photos usable on the internet.

Truly wonderful, I wanted a batch program to just resize etc from photographer quality to internet friendly, and that's exactly what I got.

No muss no fuss.

I was done in 5 mins.

so erm... keep up the great work!

---

### Post by califman831 on 2008-01-05
not loading under kubuntu, bug report filed.

---

### Post by stani on 2008-01-06
> **kgriffin said:**
> I just used it to make all my wedding photos usable on the internet.

Truly wonderful, I wanted a batch program to just resize etc from photographer quality to internet friendly, and that's exactly what I got.

No muss no fuss.

I was done in 5 mins.

so erm... keep up the great work!

Thanks, quote added to the phatch website (see documentation>reviews).

---

### Post by stani on 2008-01-06
> **califman831 said:**
> not loading under kubuntu, bug report filed.

Thanks, bug is already fixed in the repository. If you know how to work with bazaar please test it. Otherwise you can trust me that it works ;-) and wait for the release.

---

### Post by stani on 2008-01-06
> **digitalis_vulgaris said:**
> How did you remember that you need icons when I submit my post?! Hahahahahaha
Ok, if you can wait a little, I could help you with this problem. I don't have a time this mount, but maybe I could do it in january.

Of course I didn't remember your graphic skills by accident :-) You are great icon master. 

Anyway, I had to proceed as we are in a hurry to get this in time in Ubuntu Hardy. So I used some icons from the Open Clip Art Library. I've attached a screenshot (in Dutch) below. 

If you dislike some icons, feel free to provide me with some new ones under the GPL license. I can't use icons of which the origin is unclear due to licensing issues.

Happy newyear to everyone!

Stani

---

### Post by julian67 on 2008-01-06
I'm really impressed with Phatch, thank you!  It's nice that it can upscale images as I found that gthumb's resizer can't do this essential task :(

One important thing lacking is retaining the exif data. All my resized Phatched images are fine, correct dimensions and dpi etc.  but no exif data. Do you have a plan to include this feature? Or maybe I missed something?

Also I have a question about the resampling algorithms. Simply, which is highest quality? I notice new version of Gimp offers Sinc (Lanczos3) as best quality.  How does this compare with those available in Phatch?

---

### Post by stani on 2008-01-06
> **julian67 said:**
> I'm really impressed with Phatch, thank you!  It's nice that it can upscale images as I found that gthumb's resizer can't do this essential task :(Thanks!> 

One important thing lacking is retaining the exif data. All my resized Phatched images are fine, correct dimensions and dpi etc.  but no exif data. Do you have a plan to include this feature? Or maybe I missed something?This is a higly requested feature. If someone can point me to a cross platform (linux, windows, mac) exif python library, I would be happy to include it. > 

Also I have a question about the resampling algorithms. Simply, which is highest quality? I notice new version of Gimp offers Sinc (Lanczos3) as best quality.  How does this compare with those available in Phatch?
I use Gimp myself and sinc is not yet fully operational as far as I read somewhere. Antialias is the best downsampling filter and the others are more or less like Gimp. So the best upsampling filter is Bicubic. More info:

> The filter argument can be one of NEAREST (use nearest neighbour), BILINEAR (linear interpolation in a 2x2 environment), BICUBIC (cubic spline interpolation in a 4x4 environment), or ANTIALIAS (a high-quality downsampling filter).
[http://www.pythonware.com/library/pil/handbook/image.htm](http://www.pythonware.com/library/pil/handbook/image.htm)

---

### Post by julian67 on 2008-01-06
Thanks for the reply...and on a Sunday evening too! :)

I appreciate the info about resampling, it's something I'd not seen clearly spelt out before. As for Exif, the solution is easy.....build for Gnu based systems only and let Windows and Mac users use their own tools :lolflag:  But seriously Windows users have the choice of many excellent  (financially) free and paid tools that can do these things (I don't know about Mac except Photoshop could easily do all this stuff with custom actions last time I used it) but Gnu based systems really have lacked a good batch converter for images for so long ( forever????). Why not just make it as good as possible for *this* environment? I think the exif data will be something that makes the difference between many people using this tool or choosing to run IrfanView or similar under wine.  I'm going to keep using your tool as the last step in preparing my photos for printing, but it would useful in so many other ways if exif data was retained. It's really something special, great interface, easy to set up an action, works beautifully....could become an essential.  It would be a perfect extension for other full editors/managers such as F-Spot.  Thanks again.

edit: Gimp 2.4 has sinc (Lanczos3) running, it seems all ok to me as a user, though it has to explicitly chosen, it isn't the default.

---

### Post by califman831 on 2008-01-06
> **stani said:**
> Thanks, bug is already fixed in the repository. If you know how to work with bazaar please test it. Otherwise you can trust me that it works ;-) and wait for the release.

Am gonna have to wait for the .deb update.  A side note, a download now graphic would be a good change to the homepage.  The link at the bottom is not as user friendly.  Anyways keep up the good work :)

---

### Post by stani on 2008-01-06
> **julian67 said:**
> Thanks for the reply...and on a Sunday evening too! :)

I appreciate the info about resampling, it's something I'd not seen clearly spelt out before.Ha, probably you wanted something like:
[http://photobatch.wikidot.com/action-image-size](http://photobatch.wikidot.com/action-image-size)

Now you know phatch a little, why not help out a little on the documentation? It is a wiki, so anyone can contribute. Some actions have no explanation yet. Don't worry about mistakes, I'll correct them. Only creating screenshots would already be useful, but wait for the next deb release as all action icons are replaced.
>  As for Exif, the solution is easy.....build for Gnu based systems only and let Windows and Mac users use their own tools :lolflag:  Would you say the same about Firefox versus Internet Explorer? Cross platform applications help invite other users to Linux. I would prefer to see the Phatch community as big as possible. So far I still have to do too many things on my own (website, documentation, icons, ... not to speak about developing it.)

---

### Post by stani on 2008-01-06
> **califman831 said:**
> Am gonna have to wait for the .deb update.  A side note, a download now graphic would be a good change to the homepage.  The link at the bottom is not as user friendly.  Anyways keep up the good work :)

If you send me a private message on the ubuntu forums with your email I'll send you an updated deb for testing.

---

### Post by julian67 on 2008-01-06
> **stani said:**
> Ha, probably you wanted something like:
[http://photobatch.wikidot.com/action-image-size](http://photobatch.wikidot.com/action-image-size)

Now you know phatch a little, why not help out a little on the documentation? It is a wiki, so anyone can contribute. Some actions have no explanation yet. Don't worry about mistakes, I'll correct them. Only creating screenshots would already be useful, but wait for the next deb release as all action icons are replaced.
Would you say the same about Firefox versus Internet Explorer? Cross platform applications help invite other users to Linux. I would prefer to see the Phatch community as big as possible. So far I still have to do too many things on my own (website, documentation, icons, ... not to speak about developing it.)

I'll use it a little more first. So far I only did resizing (which is what i needed). But I can see some areas I know about from other applications which I might be able to help with in the wiki docs once I have tried them in Phatch. I like the wiki btw, very well laid out and the info which is there is good.

---

### Post by arigram on 2008-01-06
Hello Stani.
Forgive my disappearance of late, but I was drowning inside a puddle of holidays, personal and health problems and couldn't find the time.
I will definitely soon work with the proposed blueprints and possibly even make you a temporary icon set to use. I am still learning how to use my new tools and clean interfaces is something I haven't done yet, so don't expect much. But it will be better than nothing or those pretty but out of context icons.

---

### Post by califman831 on 2008-01-06
phatch now has its own forum, and am very happy to say I was first to post.  Never had the pleasure of doing that, so now I can walk around all snob like. 

:lolflag:



[http://photobatch.wikidot.com/forum/start](http://photobatch.wikidot.com/forum/start)

---

### Post by stani on 2008-01-07
> **arigram said:**
> Hello Stani.
Forgive my disappearance of late, but I was drowning inside a puddle of holidays, personal and health problems and couldn't find the time.
I will definitely soon work with the proposed blueprints and possibly even make you a temporary icon set to use. I am still learning how to use my new tools and clean interfaces is something I haven't done yet, so don't expect much. But it will be better than nothing or those pretty but out of context icons.
Welcome back! Thanks for your offer to help. I need icons both as 48x48px png and as svg format.

---

### Post by stani on 2008-01-07
> **califman831 said:**
> phatch now has its own forum, and am very happy to say I was first to post.  Never had the pleasure of doing that, so now I can walk around all snob like. 

:lolflag:



[http://photobatch.wikidot.com/forum/start](http://photobatch.wikidot.com/forum/start)

Congratulations!!! You have received an answer already.

---

### Post by arigram on 2008-01-07
Maybe you can ask Djaany to make you some icons, you don't need many and its gonna be part of Hardy anyway.
I am a big fan of his work. His icons are beautiful, humorous, imaginative, original and very well drawn,

[http://www.gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201&PHPSESSID=4455d27aadfc421af1433b7c62fc2207](http://www.gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201&PHPSESSID=4455d27aadfc421af1433b7c62fc2207)

---

### Post by stani on 2008-01-07
> **arigram said:**
> Maybe you can ask Djaany to make you some icons, you don't need many and its gonna be part of Hardy anyway.
I am a big fan of his work. His icons are beautiful, humorous, imaginative, original and very well drawn,

[http://www.gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201&PHPSESSID=4455d27aadfc421af1433b7c62fc2207](http://www.gnome-look.org/content/show.php/BuuF-Deuce-iconset?content=46201&PHPSESSID=4455d27aadfc421af1433b7c62fc2207)

Hmmm this style is a bit too specific. Also I prefer more the style of the old icons in Phatch. I also don't want to be too dependent on one person.

---

### Post by stani on 2008-01-08
Good news... a new release and user documentation! 

I just released a new version of Phatch (0.1.bzr200):
- bug fix: opacity of canvas size was being interpreted as transparency
- bug fix: compatibility with wxpython 2.6
- languages: updates and new languages added
- improved dutch translation (thanks to balaam)
- improved help menu (especially write plugin)
- images are now processed alfabetically
- better distinction between "scale image" and "canvas size"
- action code refactoring to make writing plugins with pil even more simple
- includes all source material for the images (svg and blender files)
- improved gradient for gtk clearlooks

Get the new release at [http://photobatch.stani.be](http://photobatch.stani.be) > free download!

I have also worked a lot on a nice user manual online:
[http://photobatch.wikidot.com](http://photobatch.wikidot.com)

Igor is hopefully polishing up the icons, give him an applause ;-)

Please improve it as much as you can, it is a wiki after all. You only need to register with wikidot.com I need some volunteers to update the screenshots as the icons have changed. Anyone?

Thanks in advance!

Stani

---

### Post by Samhain13 on 2008-01-08
Stani, you're a blessing! I was looking for an app like this one. I just downloaded it and it pretty much does what I need. Thanks! :)

I'll see to some screen shots, just let me sleep for a few hours.

[edit]
Screenshots:

---

### Post by stani on 2008-01-09
> **Samhain13 said:**
> Stani, you're a blessing! I was looking for an app like this one. I just downloaded it and it pretty much does what I need. Thanks! :)

I'll see to some screen shots, just let me sleep for a few hours.

[edit]
Screenshots:

Thanks for thanking me on the forums! You are the first to do so.

Could you add the screenshots on the wiki (just get a wikidot.com account)? I am too busy implementing new exciting features on Phatch ;-) You will probably see them soon. (Igor has some already. Hopefully he finds time to work on the icons.)

---

### Post by staticvoid on 2008-01-09
can I just say:

**I LOVE PHATCH!!**


:)

---

### Post by stani on 2008-01-09
> **staticvoid said:**
> can I just say:

**I LOVE PHATCH!!**


:)

Haha, with thanking I was referring to:

> The Following User Says Thank You to stani For This Useful Post:

I never saw this before and I noticed I got one thank on my profile now.

Thanks for sharing your love :lolflag:

---

### Post by michaelzap on 2008-01-09
Very useful little app. Thanks for creating and sharing it. I had to read the documentation to understand how to use it, but once I did that it makes total sense to me.

---

### Post by Samhain13 on 2008-01-09
> Could you add the screenshots on the wiki (just get a wikidot.com account)?

I've uploaded three new screenshots in the Wiki-- not the ones I have on my last post because they don't match the text. Also contributed the Filipino translation in Launchpad, I hope that helps too. :)

I'll see what more I can do later, cheers! I have work to do now.

---

### Post by stani on 2008-01-11
> **Samhain13 said:**
> I've uploaded three new screenshots in the Wiki-- not the ones I have on my last post because they don't match the text. Also contributed the Filipino translation in Launchpad, I hope that helps too. :)

I'll see what more I can do later, cheers! I have work to do now.

Thanks a lot for the translation!! Soon I will release a new version of Phatch with tons of new features. (I count on all of you to test the new features as they will go in Hardy!) It would be nice if you could update the translations afterwards. 

Igor made already nice icons for the currrent actions. As there will be new icons added, maybe it is better to wait with the screenshots until things are more stable.

---

### Post by PartisanEntity on 2008-01-11
Looking forward to help test again. I actually used Phatch for my internship the other day in order to resize several photos from a conference. Worked perfectly.

---

### Post by jan quark on 2008-01-11
stani
I'd like to invite you to join my linklist called Ubuntu Enthusiast
I am hosting a page dealing with Gimp art and tutorials for gimp
and I like your application much and appreaciate your work

have a look at my site (see signature) and tell me what you think
on the partners page is enough room for your logo and a description

ragards
Jan Quark

---

### Post by stani on 2008-01-11
> **jan quark said:**
> stani
I'd like to invite you to join my linklist called Ubuntu Enthusiast
I am hosting a page dealing with Gimp art and tutorials for gimp
and I like your application much and appreaciate your work

have a look at my site (see signature) and tell me what you think
on the partners page is enough room for your logo and a description

ragards
Jan Quark

Hi Jan,
Thanks for the invitation!! Links to phatch are always welcome if they consist of the phatch logo and only link to [http://photobatch.stani.be](http://photobatch.stani.be) (all other urls are temporary and might change any moment).
Concerning joining your linklist or posting tutorials... I certainly like when people make publicity, blog, promote phatch. However concerning documentation and tutorials I prefer to keep things central. I notice that quite some people post Phatch tutorials (and they basically do all the same thing) on the internet. I think Phatch users are much more helped if there is one good documentation site centrally. It would have been nicer if people would contribute their Phatch tutorials to me, so that instead of making all the same tutorial we would now have some different ones. I personally will review and polish every tutorial which is sent to me.
Note that this is a general remark and not related to you. I just want to say, if you plan to make a tutorial about phatch, let's add it to the phatch website and put a link (with a summary/excerpt) for it. Moreover you get full credits both on the site and in the phatch application (about dialog).
In case you are thinking to help me out and write a tutorial, wait for the next version of Phatch which will have much more toys to play with.
Thanks again for your interest in Phatch,
Stani

---

### Post by jan quark on 2008-01-11
stani
you may now see your link on my partners page:)

---

### Post by stani on 2008-01-11
> **jan quark said:**
> stani
you may now see your link on my partners page:)
Thanks a lot!

---

### Post by jan quark on 2008-01-11
Don't mention it!

---

### Post by stani on 2008-01-11
Big news! After some hard work, I just released the new Phatch version (0.1.bzr212), which you can grab at the usual place:
[http://photobatch.stani.be](http://photobatch.stani.be) > free download

There are tons of new features:
    * Auto Contrast - Maximize image contrast
    * Border - Crop or add border to all sides
    * Brightness - Adjust brightness from black to white
    * Canvas - Crop the image or enlarge canvas without resizing the image
    * Colorize - Colorize grayscale image
    * Common - Copies the most common pixel value
    * Contrast - Adjust from grey to black & white
    * Convert Mode - Convert the color mode of an image
      (greyscale, RGB, RGBA or CMYK)
    * Effect - Blur, Sharpen, Emboss, Smooth, …
    * Equalize - Equalize the image histogram
    * Fit - Downsize and crop image with fixed ratio
    * Grayscale - Fade all colours to gray
    * Invert - Invert the colors of the image (negative)
    * Maximum - Copies the maximum pixel value
    * Median - Copies the median pixel value
    * Minimum - Copies the minimum pixel value
    * Offset - Offset by distance and wrap around
    * Posterize - Reduce the number of bits of colour channel
    * Rank - Copies the rank'th pixel value
    * Rotate - Rotate with random angle
    * Round - Round or crossed corners with variable radius and corners
    * Saturation - Adjust saturation from grayscale to high
    * Save - Save an image with variable compression in different types
    * Scale - Scale an image with different resample filters.
    * Shadow - Drop a blurred shadow under a photo with variable position, blur and color
    * Solarize - Invert all pixel values above threshold
    * Transpose - Flip or rotate an image by 90 degrees
    * Watermark - Apply a watermark image with variable placement (offset, scaling, tiling) and opacity

These icons were designed by Igor: canvas, convert, invert, rotate, round, save, scale, solarize & watermark. Give him a big applause. I really like them. If anyone has time to contribute icons for the other actions in the same style, please do!

I really need your help now. Please test as much as you can and afterwards, help with the documentation at:
[http://photobatch.wikidot.com](http://photobatch.wikidot.com)

and especially at:
[http://photobatch.wikidot.com/actions](http://photobatch.wikidot.com/actions)

Writing documentation is easy. You just get an [http://www.wikidot.com](http://www.wikidot.com) account and you can start writing right away.

Who is willing to help?

---

### Post by Samhain13 on 2008-01-11
^I guess I'll be updating the screenshots in the Wiki. I'll do it over the weekend. :)

---

### Post by stani on 2008-01-11
> **Samhain13 said:**
> ^I guess I'll be updating the screenshots in the Wiki. I'll do it over the weekend. :)

Great! It is nice that I can count on you. Please follow this order:
[LIST=1]
[*] the getting started page
[*] the actions for which Igor designed the icons, as they are definite: canvas, convert, invert, rotate, round, save, scale, solarize & watermark
[*] If you have time extra, add screenshots to the other actions. The icons can change in the future, but the parameters won't. So it might be worth it
[/LIST]

Also switch your theme first to Human, so all screenshots are consistent.

BTW, I wrote documentation for **all** actions already. Let me know if some actions need more documentation. 

Thank you so much!
Stani

---

### Post by stani on 2008-01-11
For screenshots, please use the tool Accessoires>Screenshot. Choose window and the shadow effect.

As a reward I will add the text action.

Thanks,
Stani

---

### Post by Samhain13 on 2008-01-12
I think I'll just tinker with my CompizFusion settings, Window Decoration horizontal and vertical offset for the shadows.

I'll be taking screenshots tonight, I just need to get some coffee. :D

---

### Post by stani on 2008-01-12
Maybe it is better to wait. I am making some changes to the interface. I'll let you know when you can start.
Thanks anyway,
Stani

---

### Post by Samhain13 on 2008-01-12
Ok. Good night the. :D

---

### Post by arigram on 2008-01-12
Should I proceed with the translation?

---

### Post by stani on 2008-01-12
> **arigram said:**
> Should I proceed with the translation?

Yes launchpad/rosetta is a bit behind importing my files, but translations are always welcome. The change in user interface does not concern text.

---

### Post by Officer Dibble on 2008-01-12
I'll be downloading this, been looking for something like this in Linux... thank you. :)

---

### Post by stani on 2008-01-12
Ha, another new release! (Just to please Igor ;-)) 

As the deadline for Hardy is approaching, I am doing my best to add new features and polish Phatch further. As the previous release introduced so many new actions, the interface got too crowded. I always had the plan to work with tags and in fact already had it implemented already in the back of the application. Exposing it nicely in an user interface always requires some more work. 

So here it is. If you add an action you will only see the most commonly used features.  By pressing 'Select' in the top-right you can select a category. If you choose 'watermark', you will only get the actions related to watermarking. 

If you choose 'all', you will get all the actions. In this case you can filter the actions by typing some characters in the search box at the top left.

You can add an action by pressing the 'Add' button or by double clicking an action.

There is also a new requested feature:TEXT, which lets you draw your (copyright) text in all orientations on your images.

Even if you don't have too batch photos, please still try out the features for fun and report bugs. So we can get all this bugfree for when you still need it. 

Screenshots for the documentation are not high priority as I plan maybe some other changes. But keep on [translating]("https://translations.launchpad.net/phatch/trunk/+pots/phatch")!

Get Phatch at the usual place: [http://photobatch.stani.be](http://photobatch.stani.be) > free download

Enjoy!
Stani

---

### Post by Samhain13 on 2008-01-13
Good idea of grouping related actions together! :)

---

### Post by digitalis_vulgaris on 2008-01-13
Yes, I'm happier now. Your effort to organize options is truly step in right direction.

---

### Post by stani on 2008-01-13
> **digitalis_vulgaris said:**
> Yes, I'm happier now. Your effort to organize options is truly step in right direction.

Ha the master of the icons is happier!

I just released another version of phatch 0.1.bzr222 with the following features:
- improved error messaging
- Mask action which can give your images any shape you want. You can give your images an irregular border (like stamp or paint strokes) or you could even turn your images into text.

Try everything out!
Stani

---

### Post by stani on 2008-01-13
I just translated the [Getting Started!]("http://photobatch.wikidot.com/getting-started") tutorial in Dutch:
[http://photobatch.wikidot.com/getting-started-nl](http://photobatch.wikidot.com/getting-started-nl)

It would be nice if some of you could translate it in your local language. It is ok to use the english screenshots. For that you just have to add "getting-started/" in front of every image name, for example:

[[f>image thumb.jpg]]
becomes:
[[f>image getting-started/thumb.jpg]]

You can also add a link on the front page.

Contact me if you need help!

Stani

---

### Post by stani on 2008-01-20
Due to popular demand I have started implementing the first baby steps of exif and iptc tag support. I need your help to document the exif features. Please download the latest Phatch...:

[http://photobatch.stani.be](http://photobatch.stani.be) > free download (0.1.bzr229)

... also download the package python-pyexiv2 (hardy, but also works on gutsy):
[http://packages.ubuntu.com/hardy/python/python-pyexiv2](http://packages.ubuntu.com/hardy/python/python-pyexiv2)

... and read the documentation about the exif image inspector:

[http://photobatch.wikidot.com/image-inspector](http://photobatch.wikidot.com/image-inspector)

Please be patient, at the moment it is not possible yet to change or save exif tags, you can however use exif information in any text field of any action. This opens already a lot of possibilities: to save files with tag based filenames/folders or to write text watermarks on your pictures (such as timestamp, etc...) Just copy & paste the <variables> from the image inspector to the image fields. (Press the copy button or ctrl-c in image inspector).

I need to collect photos with exif information of as many different camera models as possible. I would prefer nice pictures which can be used for documentation purposes as well. Therefore you need to give me the written permission to publish them under any license I need. You can keep the copyright or transfer it to me. 

Here is a screenshot of the image inspector:

[img]http://photobatch.wikidot.com/local--files/image-inspector/image_inspector_exif.png[/img]

This is all beta and will be made more user friendly in the future. For example in the first column you will be able rename the complex exif names with a more simple one, so that you can define <iso> for <Exif.CanonSi.ISOspeed>

So I need:
- exif pictures emailed to me
- review, add & improve documentation at wikidot

Thanks for your offer,

Stani

---

### Post by stani on 2008-01-21
Update: if you install pyexiv2, you can save the metadata (both iptc & exif) in your manipulated phatch images:

[http://packages.ubuntu.com/hardy/python/python-pyexiv2](http://packages.ubuntu.com/hardy/python/python-pyexiv2)

Try out the latest version...
Thanks!
Stani

---

### Post by stani on 2008-01-21
I am continuing my monologue ;-)

I just added the copy and rename actions. So now you can copy and/or rename your files based on the exif or itpc information.

---

### Post by julian67 on 2008-01-22
After adding pyexiv2 and trying a batch scale and save I get this error
```
Error 0: Can not apply action Save on image 'IMG_0110 (Modified in GIMP Image Editor).JPG' in folder:
/home/julian/fspotx/watarun

invalid literal for int() with base 10: 'charset="Ascii"'

Action: {'fields': {'As': '<type>',
            'Filename': '<filename>',
            'In': '<folder>_copy',
            'Quality': u'100',
            'Resolution': '<dpi>',
            '__enabled__': u'true'},
 'label': 'Save'}

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/core/base.py", line 246, in apply_action
    photo   = action.apply(photo,setting,cache)
  File "/usr/lib/python2.5/site-packages/phatch/actions/save.py", line 74, in apply
    photo.save(filename, **options)
  File "/usr/lib/python2.5/site-packages/phatch/core/pil.py", line 261, in save
    self.copy_metadata(filename)
  File "/usr/lib/python2.5/site-packages/phatch/core/pil.py", line 301, in copy_metadata
    exif.copy_metadata(self._exif_source,filename)
  File "/usr/lib/python2.5/site-packages/phatch/core/lib/_pyexiv2.py", line 10, in copy_metadata
    target[key] = source[key]
  File "/usr/lib/python2.5/site-packages/pyexiv2.py", line 477, in __getitem__
    value = self.__getExifTagValue(key)
  File "/usr/lib/python2.5/site-packages/pyexiv2.py", line 337, in __getExifTagValue
    return UndefinedToString(tagValue)
  File "/usr/lib/python2.5/site-packages/pyexiv2.py", line 153, in UndefinedToString
    return ''.join(map(lambda x: chr(int(x)), undefined.rstrip().split(' ')))
  File "/usr/lib/python2.5/site-packages/pyexiv2.py", line 153, in <lambda>
    return ''.join(map(lambda x: chr(int(x)), undefined.rstrip().split(' ')))
ValueError: invalid literal for int() with base 10: 'charset="Ascii"'
*

```

---

### Post by stani on 2008-01-22
Thanks for reporting! That is why Phatch needs testers. Can you send me such an image file together with your action list so I can reproduce and debug it? Preferably on launchpad.

---

### Post by julian67 on 2008-01-22
I emailed you the actions list and sample image. Also just now reported bug on launchpad

---

### Post by stani on 2008-01-22
I will study this bug probably tomorrow. I was busy releasing another version of Phatch which includes a reflection action. In order to show off the potential, this is what you can do with it:

[IMG]http://photobatch.wikidot.com/local--files/tutorial-round-3d-reflect/thumb.jpg[/IMG]

I wrote a tutorial for it. Spread the word about Phatch and digg the tutorial:
[http://www.digg.com/linux_unix/Batch_create_sexy_round_thumbs_with_3d_reflection_on_ubuntu](http://www.digg.com/linux_unix/Batch_create_sexy_round_thumbs_with_3d_reflection_on_ubuntu)

Thanks!
Stani

---

### Post by julian67 on 2008-01-23
The bug I mentioned is fixed by your new version. I updated the launchpad bug report. Thank you.

---

### Post by stani on 2008-01-23
> **julian67 said:**
> The bug I mentioned is fixed by your new version. I updated the launchpad bug report. Thank you.
Thanks for the excellent bug report. This is always what I need an example photo and the action list. Bugs should be reported on launchpad otherwise I forget them ;-)

I am just about to release a new version of Phatch 0.1.bzr242 with the following features:
- Phatch now not only accepts your local files, but also images from the internet. So in any field or in the exif image inspector you can use [http://.](http://.).. addresses
- The exif image inspector now can show a thumbnail preview of the image and has an 'open url' button.

[IMG]http://photobatch.wikidot.com/local--files/image-inspector/image_inspector_exif.png[/IMG]

If you translate, please do not enable the option needs review. This blocks the translations. If someone stumbles on a bad translation in Phatch, he will correct it. Thanks a lot arnau, for keeping the catalan translation continuously up to date. You are amazing!

Keep on testing!
Stani

---

### Post by julian67 on 2008-01-23
This is quickly evolving into an impressive tool, and fills an important gap.  Previously I've been running IrfanView or XnView (Win32 version as Linux version is very old) under wine;  they're nice tools and offered at no financial cost in a nice spirit but they're not Free software.  It's great to have a native tool that is under a free license. If anybody wanted to easily see the benefits of the GPL, the  Free software philosophy and of the community/collaborative model Phatch is a great example.

---

### Post by imon9 on 2008-01-23
hi man,

just wanna let u know that the deb file u create is not correct!
it forgot about the dependency of  python-wxgtk2.8, thus not asking to install that, thus phatch didnt run after installation

please fix

also, how come there is so few action options? i didnt find any reflection/perspactive action...do i need to downlaod ny more plug-ins?

---

### Post by stani on 2008-01-23
> **imon9 said:**
> hi man,

just wanna let u know that the deb file u create is not correct!
it forgot about the dependency of  python-wxgtk2.8, thus not asking to install that, thus phatch didnt run after installation

please fix


Very strange, you are the first one with this problem. The deb file includes a dependency for python-wxgtk2.8 Can you check in Synaptic, for me it is listed. Does anyone else has this problem? Or could someone remove python-wxgtk2.8 from his system and install Phatch to see? I am too dependent on python-wxgtk to do that myself.
> 
also, how come there is so few action options? i didnt find any reflection/perspactive action...do i need to downlaod ny more plug-ins?
No, you need to read the manual (Help>Documentation) about Edit>Add:
[http://photobatch.wikidot.com/interface](http://photobatch.wikidot.com/interface)
I advise you to read the tutorials as well.
Stani

---

### Post by stani on 2008-01-23
> **julian67 said:**
> This is quickly evolving into an impressive tool, and fills an important gap.  Previously I've been running IrfanView or XnView (Win32 version as Linux version is very old) under wine;  they're nice tools and offered at no financial cost in a nice spirit but they're not Free software.  It's great to have a native tool that is under a free license. If anybody wanted to easily see the benefits of the GPL, the  Free software philosophy and of the community/collaborative model Phatch is a great example.
Wow, thanks for this compliment! I get a lot of help from the community with translations and also by Igor for the artwork. Unfortunately the documentation is still a one man show. It would be nice if more people write a tutorial or contribute something else. It is a wiki after all, and like now I could just use static html. But I am patient and waiting...

I just did a bug fix release: phatch 0.1.bzr 243 (242 is not working well, so please upgrade).

---

### Post by stani on 2008-01-24
> **imon9 said:**
> hi man,

just wanna let u know that the deb file u create is not correct!
it forgot about the dependency of  python-wxgtk2.8, thus not asking to install that, thus phatch didnt run after installation

please fix

As I know the deb file is correct, I guessed you had python-wxgtk2.6 installed on your system and Phatch uses that one instead of python-wxgtk2.8 This normally should not be a problem. As it was for you, I supposed python-wxgtk2.6 got broken. This was the case, so I fixed it. Support for python-wxgtk2.6 matters to me as it is the version available on Debian and on Ubuntu Edgy or lower. So with the latest version you could uninstall python-wxgtk2.8 and Phatch will still work. I would rather recommend to use wxpython 2.8

I just released a new version of Phatch with all the changes under the hood:
Phatch 0.1.bzr250

From now on you can follow the development of Phatch in your rss reader:
[http://feeds.launchpad.net/~stani/phatch/dev/branch.atom](http://feeds.launchpad.net/~stani/phatch/dev/branch.atom)

Stani

---

### Post by stani on 2008-01-25
I just did a major code rewrite and fixed some bugs (with rename & copy):
Phatch 0.1.bzr254

This doesn't add new features, but prepares new functionality for the future.

Please test!

Stani

---

### Post by stani on 2008-01-28
> **stani said:**
> This doesn't add new features, but prepares new functionality for the future.

Ha, now you can see what I am aiming at. As of Phatch 0.1.bzr271, phatch can run as a console application. This is big news, as now phatch can be used as a server application. The idea is that you prepare the action lists with the gui and that you can execute them on any server with only python-imaging installed. For example if people upload pictures to your site, you can let Phatch generate the thumbnails you want. To get the help options type:
```
$phatch --help
Usage: Phatch [options] [actionlist] [image files/folders]

Options:
  --version          show program's version number and exit
  -h, --help         show this help message and exit
  -c, --console      Run Phatch as console program without a gui
  -d, --droplet      Run Phatch as a gui droplet
  -f, --force        Ignore errors
  -i, --interactive  Interactive
  -m, --metadata     Save metadata (requires exif & iptc plugin)
  -o, --overwrite    Overwrite existing images
  -r, --recursive    Include all subfolders
  -s, --strict       Do not create missing folders
  -t, --trust        Do not check images first
  -v, --verbose      Verbose

```
Example
```
$phatch -v -r action_list.py image_file.png image_folder1 image_folder2
```
You can also invoke the man page, by typing:
```
$man phatch
```
This is not only handy for servers, but also if you want to schedule photo batch processing with a program like gnome-schedule. If you install:
```
$sudo apt-get install gnome-schedule
```
you can now for example watch folders by letting phatch process the folder for example every hour. With the action rename you can even move files. Please experiment as much as you can!

Stani
PS I am now working on the next release which will have another nice surprise.

---

### Post by Jad on 2008-02-09
I'm not able to find the deb package of phatch.

---

### Post by stani on 2008-02-09
Thanks for reporting. The download page was not updated. You can get it now at the usual place:
[http://photobatch.stani.be](http://photobatch.stani.be) > free download (link below right)

Stani

---

### Post by hidinggeryan on 2008-02-10
This sounds perfect for my needs and I'm really excited to try it.  I can't connect to your homepage or download site though.  ](*,)
------------------------------
Awesome! Back up now.  THANKS!

---

### Post by stani on 2008-02-10
> **hidinggeryan said:**
> This sounds perfect for my needs and I'm really excited to try it.  I can't connect to your homepage or download site though.  ](*,)

Thanks for reporting. It should be back online.

---

### Post by bvanaerde on 2008-02-13
Maybe a stupid question, but why is the default quality setting for saving an image set to 60? This really gives bad results.
In other programs, this is usually set to 85, which gives good results.

---

### Post by stani on 2008-02-13
> **bvanaerde said:**
> Maybe a stupid question, but why is the default quality setting for saving an image set to 60? This really gives bad results.
In other programs, this is usually set to 85, which gives good results.

This is not  a stupid question. I just took a value. In the new release I'll put it on 85.

---

### Post by Jad on 2008-02-14
Stani, 
Any plans to have CR2 to JPG converting functionality in Phatch?

---

### Post by stani on 2008-02-14
> **Jad said:**
> Stani, 
Any plans to have CR2 to JPG converting functionality in Phatch?

Anything that can be done with python can be added in Phatch. Please file a blueprint  and try to find python libraries. If you can't find any, describe which free tools are now available on Linux, Windows and/or Mac. The more you prepare and do research, the more likely it will be less work for me and I might implement it.

---

### Post by stani on 2008-02-18
Good news! Phatch will be in Ubuntu Hardy. With the help of POX, pochu and bzed I managed to rush Phatch in for feature freeze. This means that now I have to concentrate on bug fixing. 
I fixed several bugs in the latest release, especially unicode support. So now you should be able to use filenames with accents.

What also got in a while ago was a new feature called droplets. It allows you to create an icon on your desktop or any other folder. If you drag and drop files on it Phatch will get in action.

Phatch now also features integration with nautilus and thunar.

Let me know how the latest release shapes up.

Download the latest release at:
[http://photobatch.stani.be](http://photobatch.stani.be)

---

### Post by bvanaerde on 2008-02-19
This is really great news, congratulations!

---

### Post by maruchan on 2008-02-23
Thanks for your work on Phatch! I've been using the "watermark" feature to overlay titles on animation still frames that are then converted to videos :)

---

### Post by stani on 2008-02-26
> **maruchan said:**
> Thanks for your work on Phatch! I've been using the "watermark" feature to overlay titles on animation still frames that are then converted to videos :)
You are welcome! Glad to hear Phatch is useful for you. I just released a new version of Phatch which lets you select the font from a nice dropdown list with all the fonts which are present on your system (no matter where you have hidden them).

Now something important: on the 4th of march the definite version of Phatch will be handed over to Hardy. So please translate as much as possible in the coming days. (Yes if you wait a week it will be too late.) Just do an extra effort and you will enjoy it when Hardy is out.

---

### Post by stani on 2008-02-29
I am now working hard on polishing Phatch both for Linux and Windows. (There were a lot of issues in Windows and I have ironed them all out. )

But the latest release aims to improve usability a lot by providing every text input with convenient preset values in a dropdown box. It is hard to describe but very obvious if you try it. Now if you select the text option it is much more easy to select a font or to do datetime stamping.

Please download the latest release and report here back how it works: successful or not. If there are any bugs, please let me know as I can still fix them for Hardy.

Let's make Phatch the most polished new application of Hardy!!

---

### Post by jan quark on 2008-02-29
hey stani

I have raised the polish translation of Phatch from 37 % to 77 %
perhaps you can use some of my suggestions
my launchpad name is Michael Christoph Jan Godawski

keep up the good work
and I am glad I could help you

---

### Post by stani on 2008-03-01
> **jan quark said:**
> hey stani

I have raised the polish translation of Phatch from 37 % to 77 %
perhaps you can use some of my suggestions
my launchpad name is Michael Christoph Jan Godawski

keep up the good work
and I am glad I could help you

Hi Jan,
Great job! Thanks a lot. As a present back there is a new version of Phatch available today. I will update all translations in the beginning of next week. I hope you have some time by then to push it up to 100% and I will add another thank to your profile ;-)

Best regards,
Stani

---

### Post by jan quark on 2008-03-02
:popcorn: polish transaltion now at 99 % :popcorn:

and the filter does not show any untranslated terms
but there are still 7 marked as  to do
any ideas:confused:

---

### Post by stani on 2008-03-02
> **jan quark said:**
> :popcorn: polish transaltion now at 99 % :popcorn:

and the filter does not show any untranslated terms
but there are still 7 marked as  to do
any ideas:confused:

Yes sometimes it is confusing. I guess you need to select "need review" as they are considered untranslated:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch/pl/+translate?batch=10&show=need_review](https://translations.launchpad.net/phatch/trunk/+pots/phatch/pl/+translate?batch=10&show=need_review)
All your translations will be in Hardy.
Thanks a lot,
Stani

---

### Post by stani on 2008-03-03
Hi, 
I uploaded a new release with features new support for nautilus for which you have to install python-nautilus:
```
sudo apt-get install python-nautilus
```

Than Phatch will integrate automatically in the right click context menu:
- recent action lists
- image inspector
- with the Export menu you can add your own action lists to the context menu

This means 12 new strings to translate. Can you please translate them too?

Thanks,
Stani

---

### Post by Vadi on 2008-03-03
Wow, this looks like an excellent project (both the website and the program are very professionally done).

Do you think you can add, ah, something similar to picasa's "I'm feeling lucky." option? That's the only reason I use picasa really, and doing it on every photo is time consuming.

---

### Post by jan quark on 2008-03-04
> This means 12 new strings to translate. Can you please translate them too?
 
Done :)

Translation status: Polish 100%

---

### Post by stani on 2008-03-04
> **Vadi said:**
> Wow, this looks like an excellent project (both the website and the program are very professionally done).

Do you think you can add, ah, something similar to picasa's "I'm feeling lucky." option? That's the only reason I use picasa really, and doing it on every photo is time consuming.

If you can do some research on what it does *exactly*, I could maybe implemented it. It is quite difficult to implement feature "I am feeling Erps-Kwerps" from program "Haha" without details.

---

### Post by stani on 2008-03-04
> **jan quark said:**
> Done :)

Translation status: Polish 100%

Wow, great! You are leading. No one wants to compete with another language? 

I've just released a new version 0.1.bzr485 with one new translation and better locale support. (For example pt_BR was not loading, but now it does ;-))

Come on people, translate! It is the last day before it goes to Hardy. Tomorrow noon I download all translations and everything which is translated after that goes to Hardy+1 All moments are equal, but some are more equal than others. Right now there is such a moment.

(Dutch is always 100% translated by me, so do not translate dutch.)

---

### Post by Vadi on 2008-03-04
Well if it helps, there's a .deb for Picasa here ([click]("http://picasa.google.com/linux/download.html")). The tooltip for the feature says "One-click fix for lighting and color."

And here's the google help page in this ([click]("http://picasa.google.com/support/bin/answer.py?hl=en&answer=19726")).

(and it looks like they're using python for their help pages. Neat)

---

### Post by stani on 2008-03-04
> **Vadi said:**
> And here's the google help page in this ([click]("http://picasa.google.com/support/bin/answer.py?hl=en&answer=19726")).

(and it looks like they're using python for their help pages. Neat)

So it says:
> The "I'm Feeling Lucky" button enhances dark and bright colors in a photo and adjusts both color and contrast to optimal levels in one click.

This doesn't describe yet how it is done. I guess now Autocontrast is the closest in Phatch.

---

### Post by Vadi on 2008-03-04
Heh, I don't think they're going to share their secrets :)

You could try and experiment with it, maybe you'll get an idea...

---

### Post by Vadi on 2008-03-04
Okay, I looked at the Russian translation, and I think you didn't quite do everything properly. Usually, under the english string, there is the authors note descripting what is the string for and when is it used. For you, it just says this:

>  	 Located in /home/stani/sync/python/phatch/trunk/phatch/templates/action.py:56 /home/stani/sync/python/phatch/trunk/phatch/actions/copy.py:38 /home/stani/sync/python/phatch/trunk/phatch/actions/rename.py:38 /home/stani/sync/python/phatch/trunk/phatch/actions/save.py:48 /home/stani/sync/python/phatch/trunk/phatch/core/api.py:51 /home/stani/sync/python/phatch/trunk/phatch/core/message.py:88

Which is so not helpful, when one english word can be translated into different ones, depending on the context, in another language :|

---

### Post by stani on 2008-03-04
> **Vadi said:**
> Okay, I looked at the Russian translation, and I think you didn't quite do everything properly. Usually, under the english string, there is the authors note descripting what is the string for and when is it used. For you, it just says this:|
Can you point to an example on launchpad where there is the authors note? I never heard of that before. Also can you point me to documentation how to implement this in python code?

> Which is so not helpful, when one english word can be translated into different ones, depending on the context, in another language :|
Whenever you run into doubts, just ask as most people do. If you can find out the mechanism above I can add this feedback where people are doubting.

---

### Post by Vadi on 2008-03-04
I don't know how is it done, but I've seen it done properly when I was translating MojoSetup properly here ([click]("https://translations.launchpad.net/mojosetup/trunk/+pots/mojosetup/ru/+translate?start=100")). Notice the text beside the blue (i) icon.

Whereas Phatch doesn't have that (i) thing ([click]("https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+translate?batch=10&show=untranslated")).

---

### Post by Vadi on 2008-03-04
Here's what I was told on #launchpad, if it helps any:

> (10:57:48 AM) Vadi: If someone has a program written in Python, and wants them to be translated in launchpad - where would they be writing the strings that describe what a certain string means? Launchpad then puts that explanation below the strings that needs translation with an (i) attached to it
...
(10:59:03 AM) Odd_Bloke: Vadi: If it's with gettext, it's presumably in the .pot file (or wherever you'd normally put it).

---

### Post by stani on 2008-03-04
I think I figured it out. Just give me the numbers where you want remarks.

---

### Post by Vadi on 2008-03-04
All the ones starting from here really:

[https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+translate?show=untranslated&start=0](https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+translate?show=untranslated&start=0)

It looks like another translator went through your project, but left out all the ambiguous/confusing ones, so the "untranslated" filter shows them.

---

### Post by stani on 2008-03-04
> **Vadi said:**
> All the ones starting from here really:

[https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+translate?show=untranslated&start=0](https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+translate?show=untranslated&start=0)

It looks like another translator went through your project, but left out all the ambiguous/confusing ones, so the "untranslated" filter shows them.

what is ambigous about Horizontal, Image Inspector, left, right, top, middle, bottom...?

Some translations will be clear if you use Phatch.

Please try to narrow this list down as right now it is too big. It was not such a problem in other languages.

Stani

---

### Post by Vadi on 2008-03-04
That's the thing - I can't (I can, but I won't, that'll be a waste of time) go hunting down every string in the program to find where is it using the string. You should say where is it used, so that translators know.

Horizontal - some languages can prefix and suffix on words differently, depending on the case. Horizontal is always horizontal in english but in russian, you have to know _what_ is horizontal. So you should say where is the string used :)

---

### Post by stani on 2008-03-04
> **Vadi said:**
> That's the thing - I can't (I can, but I won't, that'll be a waste of time) go hunting down every string in the program to find where is it using the string. You should say where is it used, so that translators know.

Horizontal - some languages can prefix and suffix on words differently, depending on the case. Horizontal is always horizontal in english but in russian, you have to know _what_ is horizontal. So you should say where is the string used :)

Well right now I am busy  packaging Phatch and SPE for Hardy.  I don't know when I'll have time for that. Instead of working in launchpad you could download the Russian .po file from launchpad:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+export](https://translations.launchpad.net/phatch/trunk/+pots/phatch/ru/+export)

Afterward you open it in poEdit:
sudo apt-get install poedit

Than you start the latest release of Phatch and you see immediately where are the english strings. In poedit there is an search function (so there is no waste of time hunting) for translation. Once you are done, you send me the .po file.

That will be the less hassle for everyone. If I have to comment all these strings, I won't have time anymore to develop, write documentation or package Phatch, SPE and other open source projects I am working on.Luckily other languages have less problems and will be included with Phatch.

Or maybe another experienced Phatch user can step forward and add the comments. I can explain him how to do so. This is an ideal chance if you want to contribute but can't program or make graphics.

Stani

---

### Post by stani on 2008-03-04
Wooow! You are all great translators. Now Phatch is translated 100% in:
- English
- French
- German
- Greek
- Polish
- Ukrainian
- Dutch

Phatch is 99% translated in:
- Catalan
- Galician
Please clean this up and translate the last 1%. That would be so nice.

Translations for other languages are welcome too. Take the challenge and try to push it as far as you can. 100% is always nice ;-)

OK, these need some more work but are almost there:
- Czech
- Russian
With a little effort you can do it!

If you contributed seriously to the translations, please check if your name is in the Help>About>Credits of the latest release. If not, send me a private message and you will added how you like (you can also include an url to promote your website or your email).

Thank you all so much! Now Phatch can be a success in Hardy LTS!

Stani

---

### Post by stani on 2008-03-07
I just got a notice that Phatch will be included in Magasix, a Linux distribution based on Ubuntu:
[http://centros.edu.xunta.es/iesxulianmagarinos/magasi/?p=59](http://centros.edu.xunta.es/iesxulianmagarinos/magasi/?p=59)

I saw that people gave the Hungarian, italian and Spanish translations a huge boost. Please try to push it to 100%

Keep translating, I got some extra time to add it to Hardy but do not wait to get started.

There is a new version with the new translations. If you see some weird translations please change them in launchpad.

Stani

---

### Post by stani on 2008-03-16
Thanks for all your translations! Especially Czech and Spanish which are also now complete.

Are there not any active Phatch translators anymore to finish Hungarian and Italian? I heard that the Chinese population is the biggest on the internet now. I hope they also prove that by translating Phatch.

Now translations are going well. It is time to update the wiki. Let's work on screenshots. Please shift your computer to the human default theme and add screenshots to the actions where they are missing or correct them where they are outdated. Go for it!

For Phatch 0.2 I am doubting what should get priority, it is time for you to vote:
[http://ubuntuforums.org/showthread.php?t=726547](http://ubuntuforums.org/showthread.php?t=726547)

Thanks,
Stani

---

### Post by Vadi on 2008-03-16
You should post on [http://forum.ubuntu.org.cn/](http://forum.ubuntu.org.cn/) to get a good chinese response :)

---

### Post by stani on 2008-04-07
Hi Everyone,

Altough this thread might seem more quiet, Phatch development have continued. The reason is that I prefered to devote all my energy to get Phatch properly in the Hardy. As a result, I am proud to present you Phatch 0.1.3 You can get it at the usual place:
[http://photobatch.stani.be](http://photobatch.stani.be)

Phatch 0.1.3 fixes some bugs:
- exif writing
- relative paths for console mode
- the colours in Hardy just looked ugly with the new Human theme, so I implemented a special algorithm to make sure Phatch looks sexy for any theme
- many more fixes and small improvements (Phatch is 100% bug free)

IMPORTANT: As Phatch changed its version naming, you have to remove your previous version of Phatch first!!

This version also features some new icons from our master Igor and updated translations. This is the final version of Phatch in Hardy. After Hardy is released, Phatch 0.2 will start, for which you can cast your votes here: [http://ubuntuforums.org/showthread.php?t=726547](http://ubuntuforums.org/showthread.php?t=726547)

Thanks for all your feedback which has turned Phatch in a great product. Enjoy Phatch 0.1.3!

Stani

---

### Post by OZFive on 2008-04-07
I havejust found this program and boydo i just think it is the bees knees.  I tried to get the .deb package on the site but t is giving me a deopendeny error with python-central.  I have python-central installed already and need to know what to do to start using Phatch,

---

### Post by stani on 2008-04-07
Are you using Gutsy? I've made this installer on Hardy. Can you check if this works for you:
[http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.2-1_all.deb](http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.2-1_all.deb)

---

### Post by JoshLukas on 2008-04-07
Same issue here on Gutsy 64bit. Just uninstalled the old version of phatch, now ver. 0.1.3-1 won't run. Thx for the link to the old file. :)


Josh


EDIT: weird. 1.2-1 won't run either.

---

### Post by Rhubarb on 2008-04-07
> **OZFive said:**
> I havejust found this program and boydo i just think it is the bees knees.  I tried to get the .deb package on the site but t is giving me a deopendeny error with python-central.  I have python-central installed already and need to know what to do to start using Phatch,

Same here, so I successfully used the tar.gz file, and ran it fine by following the instructions:
[http://sd-2986.dedibox.fr/photobatch/download/index.html](http://sd-2986.dedibox.fr/photobatch/download/index.html)

(I use Ubuntu 7.10 64bit)

---

### Post by OZFive on 2008-04-07
I am still a bit of a noob when it come to instaling programs without Synaptic or .deb files.  I tried installing it via the instructions on the page but it is saing I do not havewxpython installed and of course it is not on synapitc  LOL.

---

### Post by Rhubarb on 2008-04-07
> **OZFive said:**
> I am still a bit of a noob when it come to instaling programs without Synaptic or .deb files.  I tried installing it via the instructions on the page but it is saing I do not havewxpython installed and of course it is not on synapitc  LOL.

It is in synaptic, just under a slightly different name:
**python-wxgtk2.8**

Install that and then try to run phatch again.

---

### Post by OZFive on 2008-04-07
That did it, but now I need to save it to a directory and add a launcher to my menus.  Thanks!

---

### Post by stani on 2008-04-07
> **JoshLukas said:**
> EDIT: weird. 1.2-1 won't run either.
That is possible. I am looking how far I have to go back. Does this one work?
[http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.bzr496-1_all.deb](http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.bzr496-1_all.deb)

---

### Post by stani on 2008-04-08
OK, no more hassle for you anymore. I did my best to bring you always the latest and greatest Phatch through PPA for Feisty, Gutsy and Hardy. 

Fist uninstall your previous version of Phatch.
```
sudo apt-get remove phatch
```
Afterwards just open your apt source file:
```
sudo gedit /etc/apt/sources.list
```
and add this for gutsy:
```
deb http://ppa.launchpad.net/stani/ubuntu gutsy main
deb-src http://ppa.launchpad.net/stani/ubuntu gutsy main
```
(You can replace gutsy with feisty or hardy)
My GPG key is 511595DF

After that install Phatch:
```
sudo apt-get update
sudo apt-get install phatch
```

More information here: [https://launchpad.net/~stani/+archive](https://launchpad.net/~stani/+archive)

---

### Post by bvanaerde on 2008-04-09
> **stani said:**
> OK, no more hassle for you anymore....
Wow, this is great news! Definitely makes it easier to keep track of the latest updates...

---

### Post by beefcurry on 2008-04-12
I ran it through bazaar, so far its great :D. The deb on the website complained about not having Python-central while I did have it. Using  Gutsy, will file a bug report on it soon. Thanks.

---

### Post by stani on 2008-04-12
> **beefcurry said:**
> I ran it through bazaar, so far its great :D. The deb on the website complained about not having Python-central while I did have it. Using  Gutsy, will file a bug report on it soon. Thanks.

There is nothing wrong with the deb installer, just with the webpage. The installer is for Hardy, not for Gutsy. If you use Gutsy, I advise you to use the Phatch repositories:
[http://ubuntuforums.org/showpost.php?p=4680119&postcount=278](http://ubuntuforums.org/showpost.php?p=4680119&postcount=278)

---

### Post by stani on 2008-04-14
After running the poll ...
[http://ubuntuforums.org/showthread.php?t=726547](http://ubuntuforums.org/showthread.php?t=726547)

... be ready for some news on Phatch 0.2!

Ok, so the winning feature is "external actions". After some thinking this will be indeed THE feature for Phatch 0.2 because of three reasons:
- It will open Phatch up to any application which as command line interface with imagemagick as a test case. This means that Phatch 0.2 will offically support all features of imagemagick.
- The other most wanted feature live preview would not make sense to implement before external actions. For external actions the base architecture of Phatch has to be changed, which requires another implementation of live preview. So if I would do it now, I would have to do it all over again after external actions has been implemented.
- It is a long time vision. It has a lot of potential and in the far future would enable to do any kind of batch processing with Phatch not just graphics. But first Phatch will develop with the focus on image manipulation. Don't worry.

A third reason could be that it won in this poll but well, I said the process would not be democratic ;-) It is nice to see Phatch users want it as well.

Some people contacted me to help programming on certain aspects of Phatch from very small tasks to bigger issues. We had a fruitful first sprint. If you know python and want to help out, please contact me. You don't need to know anything about graphics manipulation or gui programming, just python is enough. I hope some more people join.

What I need now is a list of all possible programs which can be used for external actions. This is what I have so far:
- imagemagick
- tufuse
- ...

Which other programs could Phatch support? I am looking forward to your answers.

Stani

---

### Post by stani on 2008-04-16
Hi Folks,
I have worked on the documentation wiki so now it covers almost all of Phatch at:
[http://photobatch.wikidot.com](http://photobatch.wikidot.com)

Right now I am looking for some folks who could take one or more screenshots and upload it to the wiki. If a bunch of you step up, it should be not a lot of work. If you are interested, make yourself here known and send me a private message with your email so we can discuss the details.

Thanks in advance,
Stani

---

### Post by joebert on 2008-04-18
Unfreakin real.

I just resized/resampled ELEVEN quick test images in less time than it was taking Imagemagick to do ONE.

If this thing makes it through the 10K images I have without the same lockups Imagemagick was giving me I might just have to kiss you !

---

### Post by smartboyathome on 2008-04-30
> **stani said:**
> After running the poll ...
[http://ubuntuforums.org/showthread.php?t=726547](http://ubuntuforums.org/showthread.php?t=726547)

... be ready for some news on Phatch 0.2!

Ok, so the winning feature is "external actions". After some thinking this will be indeed THE feature for Phatch 0.2 because of three reasons:
- It will open Phatch up to any application which as command line interface with imagemagick as a test case. This means that Phatch 0.2 will offically support all features of imagemagick.
- The other most wanted feature live preview would not make sense to implement before external actions. For external actions the base architecture of Phatch has to be changed, which requires another implementation of live preview. So if I would do it now, I would have to do it all over again after external actions has been implemented.
- It is a long time vision. It has a lot of potential and in the far future would enable to do any kind of batch processing with Phatch not just graphics. But first Phatch will develop with the focus on image manipulation. Don't worry.

A third reason could be that it won in this poll but well, I said the process would not be democratic ;-) It is nice to see Phatch users want it as well.

Some people contacted me to help programming on certain aspects of Phatch from very small tasks to bigger issues. We had a fruitful first sprint. If you know python and want to help out, please contact me. You don't need to know anything about graphics manipulation or gui programming, just python is enough. I hope some more people join.

What I need now is a list of all possible programs which can be used for external actions. This is what I have so far:
- imagemagick
- tufuse
- ...

Which other programs could Phatch support? I am looking forward to your answers.

Stani

By the way, I just found out [GIMP has a command line interface]("http://www.gimp.org/tutorials/Basic_Batch/"), it would be great if that was supported.

---

### Post by stani on 2008-05-01
> **smartboyathome said:**
> By the way, I just found out [GIMP has a command line interface]("http://www.gimp.org/tutorials/Basic_Batch/"), it would be great if that was supported.
Well, I had that in mind as well. But probably first Phatch will support ImageMagick.

---

### Post by @)--',------- on 2008-05-22
I really like this program, but I really wish it allowed for conditional statements. I.e. - if the width is less than 500px or the height is less than 500px, then resize, crop, etc.

Otherwise when I am processing many Images to fix canvas/ padding errors I end up processing images that do not need a resize/ fix and the quality and filesize suffers.  It is not easy for me to sort images by size in Ubuntu, so limiting the batch that way will not work.

I also think allowing for lossless crop and canvas adds would be great also!

Great program, I really look forward to future versions!

---

### Post by stani on 2008-05-30
> **@)--',------- said:**
> I really like this program, but I really wish it allowed for conditional statements. I.e. - if the width is less than 500px or the height is less than 500px, then resize, crop, etc.

Otherwise when I am processing many Images to fix canvas/ padding errors I end up processing images that do not need a resize/ fix and the quality and filesize suffers.  It is not easy for me to sort images by size in Ubuntu, so limiting the batch that way will not work.

I also think allowing for lossless crop and canvas adds would be great also!

Great program, I really look forward to future versions!

Feel free to file a blueprint for it with the title "logic".

---

### Post by stani on 2008-05-30
If you are using Phatch in a different language than English or Dutch, you might run in some serious trouble as some translations messed up keyboard shortcuts or basic functionality of Phatch. It took me a while to get this fixed properly and to ensure it won't happen in the future. So I advise everyone to update from:
[http://photobatch.stani.be](http://photobatch.stani.be)

or to use my PPA.

---

### Post by Vadi on 2008-05-30
What is your PPA?

---

### Post by stani on 2008-05-31
> **Vadi said:**
> What is your PPA?
[https://launchpad.net/~stani/+archive](https://launchpad.net/~stani/+archive)

Note this will update automatically your Phatch to the latest and greatest features and bugs. (Right now still only bugs are fixed, but when new features are added this might change, which means new bugs are introduced.) Therefore I leave you the choice download manually or get automatic updates.

If you do automatic updates, you are in the best position to test and to ensure future versions rock.

---

### Post by Vadi on 2008-05-31
Hm. It says "The packages are signed with the 511595DF GPG key." on the PPA page. I can't find that key anywhere though...

---

### Post by stani on 2008-05-31
> **Vadi said:**
> Hm. It says "The packages are signed with the 511595DF GPG key." on the PPA page. I can't find that key anywhere though...

Hmmm... that is my mistake. I changed it into:
> Unfortunately it is not possible to sign the binary packages from the PPA.

---

### Post by stani on 2008-05-31
New version released. It fixes a bug for when you try to select a font type in the text actions.

---

### Post by sashko on 2008-08-17
I have started Serbian translation.
Nice work stani, and I've to say thank you!

---

### Post by digitalis_vulgaris on 2008-08-18
> **sashko said:**
> I have started Serbian translation.
Nice work stani, and I've to say thank you!

You could connect with TZAR form Ubuntu Serbian Community to work together on translation.

Sre&#263;an rad...

[URL="http://www.ubuntu-cs.org/forum/viewthread.php?tid=6171"]
http://www.ubuntu-cs.org/forum/viewthread.php?tid=6171[/URL]

---

### Post by sashko on 2008-08-18
> **digitalis_vulgaris said:**
> You could connect with TZAR form Ubuntu Serbian Community to work together on translation.

Sre&#263;an rad...

[URL="http://www.ubuntu-cs.org/forum/viewthread.php?tid=6171"]
http://www.ubuntu-cs.org/forum/viewthread.php?tid=6171[/URL]

That's me!

pozdrav digitalis!:)

---

### Post by digitalis_vulgaris on 2008-08-19
Hahahahahaha :lol:

---

### Post by Orlsend on 2008-08-19
Site is down for 2 of my IP's can some one host the .deb file in megaupload or some file sharing site? thanks

---

### Post by stani on 2008-09-01
> **Orlsend said:**
> Site is down for 2 of my IP's can some one host the .deb file in megaupload or some file sharing site? thanks

Yes the site is down due to hard disk failure. So it has to be rebuild from scratch. I still have a backup of everything, but configuring a virtual host take time. The debs are in universe and in my ppa, so they can be obtained there anyway. In Ubuntu or debian you can install it with:
```
sudo apt-get install phatch
```

I'll do my best to get this up and running again, but please be patient as I am quite busy at the moment with other things as well. If someone has experience with virtualbox ubuntu servers and wants to give a hand, please contact me.

---

### Post by stani on 2008-09-09
> **stani said:**
> Yes the site is down due to hard disk failure. So it has to be rebuild from scratch. I still have a backup of everything, but configuring a virtual host take time. The debs are in universe and in my ppa, so they can be obtained there anyway. In Ubuntu or debian you can install it with:
```
sudo apt-get install phatch
```

I'll do my best to get this up and running again, but please be patient as I am quite busy at the moment with other things as well. If someone has experience with virtualbox ubuntu servers and wants to give a hand, please contact me.

It is up again ;-)

---

### Post by Orlsend on 2008-09-10
Finally after weeks of trial and error I managed to get the web-site running and the download.

---

### Post by altonbr on 2008-09-28
Is there any work being done to add image convertions to Phatch? If it is a batch processor, I would find it very very useful to be able to convert from PDF to JPG, such as Imagemagick's convert program.

e.g.
```
for file in `ls *.pdf`; do
	convert -colorspace RGB $file -resize 800x800 `echo $file | sed 's/\.pdf$/\.jpg/'`
done
```

I also created a brainstorm for creating an image converter and adding it as a default program in Ubuntu [1]. I didn't know of Phatch until now but am I ever glad to learn of it!

[1] [http://brainstorm.ubuntu.com/idea/13719/](http://brainstorm.ubuntu.com/idea/13719/)

---

### Post by stani on 2008-09-29
> **altonbr said:**
> Is there any work being done to add image convertions to Phatch? If it is a batch processor, I would find it very very useful to be able to convert from PDF to JPG, such as Imagemagick's convert program.

e.g.
```
for file in `ls *.pdf`; do
	convert -colorspace RGB $file -resize 800x800 `echo $file | sed 's/\.pdf$/\.jpg/'`
done
```

I also created a brainstorm for creating an image converter and adding it as a default program in Ubuntu [1]. I didn't know of Phatch until now but am I ever glad to learn of it!

[1] [http://brainstorm.ubuntu.com/idea/13719/](http://brainstorm.ubuntu.com/idea/13719/)



For a next version of Phatch it is planned to open Phatch for imagemagick, gimp, etc… However no timetable is set yet. How are your coding skills?

BTW Phatch runs on Linux, Mac & Windows.

---

### Post by binbash on 2009-02-19
I can't download patch from lauchpad or anywhere, the link is broken

---

### Post by durand on 2009-02-19
How about here: [http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by Vadi on 2009-02-19
The links there are indeed broken

---

### Post by durand on 2009-02-19
That's weird. They work for me..

**Intrepid**: [https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~8.10~ppa1_all.deb](https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~8.10~ppa1_all.deb)
**Hardy**: [https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~8.04~ppa1_all.deb](https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~8.04~ppa1_all.deb)
**Gutsy**: [https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~7.10~ppa1_all.deb](https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~7.10~ppa1_all.deb)
**Feisty**: [https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~7.04~ppa1_all.deb](https://launchpad.net/~stani/+archive/+files/phatch_0.1.6-0ubuntu1~7.04~ppa1_all.deb)

---

### Post by Vadi on 2009-02-19
All of them don't work here. Remember that LP renamed the URL structure of the PPA pages because they'll be allowing multiple ppa's per person/team soon.

Proper link is

[https://launchpad.net/%7Estani/](https://launchpad.net/%7Estani/)**+archive/ppa**/+files/phatch_0.1.6-0ubuntu1~8.10~ppa1_all.deb and etc.

---

### Post by durand on 2009-02-19
That is interesting however they do actually work for me... Anyway, I have no idea what else you could try.

---

### Post by Nevon on 2009-02-19
I'm currently working on the Swedish translation. So far I've translated about 20% of it.

---

### Post by binbash on 2009-02-19
This repo works : 

deb [http://ppa.launchpad.net/sargentd/ppa/ubuntu](http://ppa.launchpad.net/sargentd/ppa/ubuntu) intrepid main

---

### Post by richandcreamy on 2009-02-28
I've been using this program for months but after installing some updates it stopped working.  I'm not sure what's interfering with it.  Any ideas on trouble shooting it?

---

### Post by AJB2K3 on 2009-03-01
I've got an issue using phatch here.

I want to do the following

Resize to 800X600,
Save as full<###>.jpg
Resize to 100X75
Save as tmb<###>.jpg

But for some reason it stops after the first save as.

Can anyone help or do I just have to run to scripts.

---

### Post by Orlsend on 2009-03-02
Its seems I can't work with pictures that in my home directories, even with sudo.Is that a security feature or a bug?

---

### Post by richandcreamy on 2009-03-13
Anyone know how to install PIL in XP?  I can't find any guides.

---

### Post by Lonco on 2009-04-08
great tool! thx! :D

---

### Post by AJB2K3 on 2009-04-10
> **richandcreamy said:**
> Anyone know how to install PIL in XP?  I can't find any guides.
Got [http://photobatch.stani.be/]("http://photobatch.stani.be/")
Click on free download,
Follow instructions.

---

### Post by stani on 2009-04-14
I'm preparing a new release of Phatch. Please start translating on rosetta:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

Of course this release won't make it into Jaunty, but will be available from my PPA. Translating the missing strings will speed up the release process.

---

### Post by stani on 2009-05-18
Linux+ magazine of May 2009 (french edition) has a 6 page review about Phatch:
[http://lpmagazine.org/prt/view/actualites/issue/1022.html](http://lpmagazine.org/prt/view/actualites/issue/1022.html)

PS. Please keep translating so the new release does not get delayed. Almost all languages miss words now.

---

### Post by stani on 2009-06-04
Hi all,

Good news: the new test release of Phatch 0.2 is ready and available through my PPA repository! Read more about it here:
[http://ubuntuforums.org/showthread.php?p=7398717](http://ubuntuforums.org/showthread.php?p=7398717)

Please reply there and start translating (as they are a lot behind):
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

Thanks!
Stani

---

### Post by UbuntuNerd on 2009-06-04
is there a Jaunty version I just installed it with out thinking and got an error message then I realized I had Jaunty installed and not Intrepid

---

### Post by stani on 2009-06-04
Please post questions about Phatch 0.2 here:
[http://ubuntuforums.org/showthread.php?p=7398717](http://ubuntuforums.org/showthread.php?p=7398717)

---

### Post by Purre on 2009-09-19
Just find this program and I´m already love it :) Thanks for this :)

---

### Post by hesjnet on 2009-12-09
Thanks alot for this program! Nice work.:KS

---

### Post by sugcagli on 2009-12-09
Phatch is a simple to use cross-platform GUI Photo Batch Processor which handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, rename, ... and much more [actions]("http://photobatch.wikidot.com/actions") in minutes instead of hours or days if you do it manually. [Get Started!]("http://photobatch.wikidot.com/getting-started")

---

### Post by stani on 2009-12-10
Thanks a lot for the compliments! Please subscribe to our PPA to help testing the new versions of Phatch. At the moment it are bug fix releases with more translations and some cool new artwork, so they'll work better as what is by default in Karmic:
```
sudo add-apt-repository ppa:stani
sudo apt-get update
sudo apt-get install phatch
```

---

### Post by mocha on 2009-12-12
> **stani said:**
> Thanks a lot for the compliments! Please subscribe to our PPA to help testing the new versions of Phatch. At the moment it are bug fix releases with more translations and some cool new artwork, so they'll work better as what is by default in Karmic:
```
sudo add-apt-repository ppa:stani
sudo apt-get update
sudo apt-get install phatch
```


Why does your deb have Blender and locate as dependancies?

---

### Post by stani on 2009-12-12
> **mocha said:**
> Why does your deb have Blender and locate as dependancies?

The PPA contains development snapshots of the upcoming phatch releases. They are used to test all features of Phatch with a wider audience. Or to quote the ppa page itself:
> Note that if you install Phatch from this repository, it will depend on all packages with which Phatch can interact. This includes Blender, Inkscape, imagemagick, ...
If you don't want all the new features just use Phatch which ships with vanilla Ubuntu:
```
sudo apt-get install Phatch
```
Blender is a dependency in the PPA as Phatch has a Blender action which can turn any image into a 3D image of a lcd screen, book, box, can, ... Phatch uses locate to locate various useful files such as fonts on your system.

---

### Post by megamania on 2010-02-08
I'm using version 0.2.4 and I'm having problems applying IPTC tags.

I'm attaching two pictures:
- the first one shows what I'm trying to do: set the copyright field to "test", and apply a "phatch" tag to the keywords field.
- the second picture shows the result: only the first letter of the tag is inserted in the copyright field, while the result for the keywords field is even more complicated... the word "phatch" is interpreted as 6 keywords, one for each letter.

Exif tags seem to work ok.

Any ideas if I'm doing something wrong? Is it a bug?

---

### Post by protector2020 on 2010-02-11
hi dude, thanks so much for creating this great tool, it has even more functions than I need. I'll be checking them out on time. the feature I liked the most is the integration within nautilus. I use Linux Mint 8 (based upon Ubuntu 9.10 Karmic) and phatch 0.2.4

---

### Post by stani on 2010-03-04
Please start translating Phatch for Ubuntu Lucid!
[https://translations.launchpad.net/phatch/trunk](https://translations.launchpad.net/phatch/trunk)

---

### Post by spcwingo on 2010-04-03
Hi, I'm just wondering if anyone else is getting this (a video of what is happening because it's kinda hard to put into words):

[http://www.mediafire.com/?te4nttmtmli]("http://www.mediafire.com/?te4nttmtmli")

Thanks in advance for any help/insight as to what is going on.  :)

---

### Post by stani on 2010-04-03
> **spcwingo said:**
> Hi, I'm just wondering if anyone else is getting this (a video of what is happening because it's kinda hard to put into words):

[http://www.mediafire.com/?te4nttmtmli]("http://www.mediafire.com/?te4nttmtmli")

Thanks in advance for any help/insight as to what is going on.  :)

Which version of Phatch are you using? I can't reproduce this with Phatch 0.2.7, but it might have been a bug in a previous version.

---

### Post by spcwingo on 2010-04-03
Sorry, I forgot to add what version I am using.  :oops:  I'm on 0.2.7.

---

### Post by stani on 2010-04-03
> **spcwingo said:**
> Sorry, I forgot to add what version I am using.  :oops:  I'm on 0.2.7.

Hmmm... could you try to run Phatch from trunk:
```
sudo apt-get install bzr
bzr branch lp:phatch
cd phatch/phatch
python app.py
```

---

### Post by spcwingo on 2010-04-03
> **stani said:**
> Hmmm... could you try to run Phatch from trunk:
```
sudo apt-get install bzr
bzr branch lp:phatch
cd phatch/phatch
python app.py
```

The trunk version does the same.  It's also not throwing any errors on the terminal.  The version in the standard repos doesn't do this at all, but the newest version has features that would be nice to have.  BTW, thanks for giving me a hand with this.

---

### Post by stani on 2010-04-03
> **spcwingo said:**
> The trunk version does the same.  It's also not throwing any errors on the terminal.  The version in the standard repos doesn't do this at all,What you mean with 'this'? What happens when you click more to the left where the list appears? (Instead of clicking more right and moving left to the list.)
>  but the newest version has features that would be nice to have.  Which new features do you like? Trunk contains code for the upcoming 0.2.8 release which will be also available for Mac and Windows.
[https://launchpad.net/phatch/+milestone/0.2.8](https://launchpad.net/phatch/+milestone/0.2.8)
> BTW, thanks for giving me a hand with this.You're welcome ;-)

Can you paste the output of (trunk version):
```
python app.py --context
```

---

### Post by spcwingo on 2010-04-03
> What you mean with 'this'? What happens when you click more to the left where the list appears? (Instead of clicking more right and moving left to the list.)

I was referring to the disappearing dropdown menus (sorry, I should have been more descriptive).  When I click further to the left (on the selection text) I don't even see the dropdown at all.

> Which new features do you like? Trunk contains code for the upcoming 0.2.8 release which will be also available for Mac and Windows.
[https://launchpad.net/phatch/+milestone/0.2.8](https://launchpad.net/phatch/+milestone/0.2.8)

Mostly the extra options for watermarking and the imagemagick selections.

> Can you paste the output of (trunk version):
```
python app.py --context
```

```
{'app_actionlists_path': u'/home/jonathan/phatch/data/actionlists',
 'app_actions_path': u'/home/jonathan/phatch/phatch/actions',
 'app_bin_paths': [u'/home/jonathan/phatch/phatch/../../bin',
                   u'/home/jonathan/phatch/phatch/../../bin/blender',
                   u'/home/jonathan/phatch/phatch/../../bin/imagemagick'],
 'app_blender_path': u'/home/jonathan/phatch/data/blender',
 'app_data_path': u'/home/jonathan/phatch/data',
 'app_doc_dev_path': u'/home/jonathan/phatch/doc/build/html/index.html',
 'app_doc_path': u'/home/jonathan/phatch/doc',
 'app_extension': '.phatch',
 'app_fonts_cache_path': u'/home/jonathan/phatch/data/fonts.cache',
 'app_fonts_path': u'/home/jonathan/phatch/data/fonts',
 'app_gui_path': u'/home/jonathan/phatch/data/gui',
 'app_highlights_path': u'/home/jonathan/phatch/data/images/highlights',
 'app_images_path': u'/home/jonathan/phatch/data/images',
 'app_locale_path': u'/home/jonathan/phatch/locale',
 'app_masks_path': u'/home/jonathan/phatch/data/images/masks',
 'app_name': 'phatch',
 'app_preview_actionlists_path': u'/home/jonathan/phatch/data/gui/preview/actionlists',
 'app_preview_blender_path': u'/home/jonathan/phatch/data/gui/preview/blender',
 'app_preview_path': u'/home/jonathan/phatch/data/gui/preview',
 'app_preview_perspective_path': u'/home/jonathan/phatch/data/gui/preview/perspective',
 'app_source_path': u'/home/jonathan/phatch/phatch',
 'app_title': 'Phatch',
 'app_watermarks_path': u'/home/jonathan/phatch/data/images/watermarks',
 'apple': False,
 'context': ('linux', 'source'),
 'desktop_path': '/home/jonathan/Desktop',
 'distribute': 'source',
 'linux': True,
 'phatch-inspector.ico': u'/home/jonathan/phatch/setup/images/icons/256x256/phatch.ico',
 'phatch.ico': u'/home/jonathan/phatch/setup/images/icons/256x256/phatch.ico',
 'phatch_48x48.png': u'/home/jonathan/phatch/setup/images/icons/48x48/phatch.png',
 'platform': 'linux',
 'py_extension': '*.py',
 'start_time': 1270344487.0199101,
 'unix': True,
 'user_actionlists_path': u'/home/jonathan/.local/share/phatch/actionlists',
 'user_actions_path': u'/home/jonathan/.local/share/phatch/actions',
 'user_bin_paths': [u'/home/jonathan/.local/share/phatch/bin'],
 'user_cache_path': u'/home/jonathan/.cache/phatch',
 'user_config_path': u'/home/jonathan/.config/phatch',
 'user_data_path': u'/home/jonathan/.local/share/phatch',
 'user_fonts_cache_path': u'/home/jonathan/.cache/phatch/fonts.cache',
 'user_fonts_path': u'/home/jonathan/.local/share/phatch/fonts',
 'user_geek_path': u'/home/jonathan/.local/share/phatch/geek.txt',
 'user_highlights_path': u'/home/jonathan/.local/share/phatch/highlights',
 'user_log_path': u'/home/jonathan/.cache/phatch/log',
 'user_masks_path': u'/home/jonathan/.local/share/phatch/masks',
 'user_path': u'/home/jonathan',
 'user_preview_path': u'/home/jonathan/.cache/phatch/preview',
 'user_settings_path': u'/home/jonathan/.config/phatch/settings.py',
 'user_watermarks_path': u'/home/jonathan/.local/share/phatch/watermarks',
 'version_app': '0.2.7',
 'version_pil': '1.1.6',
 'version_platform': 'Linux-2.6.24-27-generic-i686-with-debian-lenny-sid',
 'version_pyexiv2': '<installed>',
 'version_python': '2.5.2 (r252:60911, Jan 20 2010, 21:48:48) [GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)]',
 'version_wx': '2.8.7.1 (gtk2-unicode)',
 'windows': False}
```

---

### Post by stani on 2010-04-03
> **spcwingo said:**
> I was referring to the disappearing dropdown menus (sorry, I should have been more descriptive).  When I click further to the left (on the selection text) I don't even see the dropdown at all.What is the Phatch version from the standard repo's where it is still working correctly for you?
> Mostly the extra options for watermarking and the imagemagick selections.
What you mean with imagemagick selections?
> 
```
{...
 'version_platform': 'Linux-2.6.24-27-generic-i686-with-debian-lenny-sid',
 ...}
```
Which distro and version are you using? Debian Lenny or Ubuntu Karmic?

---

### Post by spcwingo on 2010-04-03
> **stani said:**
> What is the Phatch version from the standard repo's where it is still working correctly for you?

0.1.3

> **stani said:**
> What you mean with imagemagick selections?

Polaroid, sharpen, unsharpen, pencil sketch, etc.

> **stani said:**
> Which distro and version are you using? Debian Lenny or Ubuntu Karmic?

Neither, Ubuntu Hardy.

---

### Post by stani on 2010-04-03
> **spcwingo said:**
> 0.1.3



Polaroid, sharpen, unsharpen, pencil sketch, etc.



Neither, Ubuntu Hardy.
Hmm... any chance for you to test this on Karmic or Lucid?

---

### Post by spcwingo on 2010-04-03
I currently don't have a spare box to test on (what kind of geek am I?!?!).  I'll be upgrading to Lucid at the end of this month (when it comes out).  I'll let you know if it does any better after the switch.  Thanks again for helping me out.

---

### Post by spcwingo on 2010-05-22
All is now well with Phatch on my machine after a clean install of Lucid.

---

### Post by Dragonbite on 2010-06-29
Is this in the repositories?

---

### Post by stani on 2010-06-29
> **Dragonbite said:**
> Is this in the repositories?

Yes.

---

### Post by jacqie on 2011-05-30
Hi, 
I've problem with phatch - can't select any file type (in save action). [Ubuntu 11.04; phatch 0.2.7] 
Any idea, what could be wrong?
Maybe some not installed packages?... I don't know. :confused:

---

