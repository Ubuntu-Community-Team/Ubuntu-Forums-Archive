---
title: "Phatch 0.2: Photo &amp; Batch!"
date: 2009-06-04
forum: Art &amp; Design
---

### Post by stani on 2009-06-04
Phatch is an user friendly, cross-platform Photo Batch Processor and Exif Renamer with a nice graphical user interface. Phatch handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, apply shadows, perspective, rounded corners, ... and do much more actions in minutes instead of hours or days if you do it manually.
[http://photobatch.stani.be](http://photobatch.stani.be)
[http://en.wikipedia.org/wiki/Phatch](http://en.wikipedia.org/wiki/Phatch)

[IMG]http://upload.wikimedia.org/wikipedia/en/0/0d/Phatch_Actions.png[/IMG][IMG]http://photobatch.wikidot.com/local--files/action-write-tag/write_tag.png[/IMG][IMG]http://upload.wikimedia.org/wikipedia/en/1/11/Phatch_Image_Inspector.png[/IMG]

For an introduction to Phatch, you can also read this thread if you have patience ;-)
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

Phatch 0.2 is still in full development, but since today it is available for alpha testing. This means that the program is already quite usable, but it still can contain serious errors. Moreover some new features might not be implemented yet, or just partly. If this doesn't frighten you, I'd like to invite you to do some serious testing of the program.

What is new in Phatch 0.2?
Actions:
- color to alpha: makes a (background) color transparent (eg icon background from white to transparent)
- contour: draw a contour line around an image
- highlight: create a transparent highlight (great for web2.0 style buttons)
- crop (with autocrop)
- write tag: write any exif/iptc tag to images (you can copy and paste them from the image inspector)
User interaction:
- notifications (also works on Mac & Windows, uses new system on Jaunty)
- f-spot support via drag&drop or right click mouse context menu (Open With)
- better logging
Under the hood:
- support for EXIF.py tag reading
- saving transparent gif images
- support for tiff images with compression (lzw, g3, g4, jpg, zip, ...)
- configuration follows free desktop specification (~/.config, ~/.local/share, ~/.cache)

An example of shiny button made with contour+highlight in an action list:
[img]http://photobatch.wdfiles.com/local--resized-images/action-highlight/feed-icon.png/thumbnail.jpg[/img]

An example of only the contour action:
[IMG]http://photobatch.wdfiles.com/local--files/action-contour/star_contour.png[/IMG]

An example of the polaroid action list (File > Library) with the variable border action:
[IMG]http://photobatch.wikidot.com/local--files/tutorial-polaroid/polaroid.png[/IMG]

or a little bit twisted:

[IMG]http://photobatch.wikidot.com/local--files/tutorial-polaroid/polaroid-twisted.png[/IMG]

Planned features are:
- gps action: adding gps locations to photos (don't use it yet, is not working)
- variabel border action (done!)
- better exif support
- and more surprises ...

For more info: [https://blueprints.launchpad.net/phatch/0.2](https://blueprints.launchpad.net/phatch/0.2)

A lot of work has been done in bug fixing:
[https://bugs.launchpad.net/phatch/+bugs](https://bugs.launchpad.net/phatch/+bugs)

For the release of Phatch 0.2 it is the purpose that ALL correctly reported bugs are solved. I'm happy with any reported bug which has a zip file attached with an action list and example images. Always check if the bug hasn't been reported yet.

You can always file new blueprints (feature requests), but again, check if they are not reported before.

You can install Phatch through my PPA archive (hardy, intrepid, jaunty, karmic):
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)
Add this to your sources.list (replace jaunty with your version): ```
deb [http://ppa.launchpad.net/stani/ppa/ubuntu](http://ppa.launchpad.net/stani/ppa/ubuntu) jaunty main
```
Add the key to your system: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7B0FB2CA
```

Phatch 0.2 is the first release to which others have contributed in development. I'd like to thank especially Nadia Alramli ([http://nadiana.com](http://nadiana.com)) for her great work! I'm also looking forward to the contributions of Erich and Robin.

But Phatch NEEDS you:
- translations are trailing behind, please go for it now:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)
- we need people helping with documentation, send me a private message
- if you know python & pil, why not join our friendly team:
[https://launchpad.net/~phatch-dev](https://launchpad.net/~phatch-dev)
[https://lists.launchpad.net/phatch-dev/](https://lists.launchpad.net/phatch-dev/)
- if you are good in graphics, send me some work you did, so I can see if it fits with Phatch

I am very curious for your reactions!

Stani

PS Warning: Previous Phatch 0.1 action lists are not compatible with Phatch 0.2!

---

### Post by stani on 2009-06-04
The package was not compatible with python 2.4 So I removed the packages and uploaded new ones. It will take a few minutes for them to appear.

---

### Post by UbuntuNerd on 2009-06-04
is there a jaunty version?

---

### Post by stani on 2009-06-04
Sure, just use the Jaunty PPA as described in my first post. If you don't know how to do that, just let me know. And if it works let me know too ;-)

---

### Post by UbuntuNerd on 2009-06-04
yeah I know how to use the PPA :)

---

### Post by tuannq123 on 2009-06-05
> **stani said:**
> Phatch is an user friendly, cross-platform Photo Batch Processor and Exif Renamer with a nice graphical user interface. Phatch handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, apply shadows, perspective, rounded corners, ... and do much more actions in minutes instead of hours or days if you do it manually.
[http://photobatch.stani.be](http://photobatch.stani.be)
[http://en.wikipedia.org/wiki/Phatch](http://en.wikipedia.org/wiki/Phatch)

[IMG]http://upload.wikimedia.org/wikipedia/en/0/0d/Phatch_Actions.png[/IMG][IMG]http://upload.wikimedia.org/wikipedia/en/1/11/Phatch_Image_Inspector.png[/IMG]

For an introduction to Phatch, you can also read this thread if you have patience ;-)
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

Phatch 0.2 is still in full development, but since today it is available for alpha testing. This means that the program is already quite usable, but it still can contain serious errors. Moreover some new features might not be implemented yet, or just partly. If this doesn't frighten you, I'd like to invite you to do some serious testing of the program.

What is new in Phatch 0.2?
- color to alpha: makes a (background) color transparent (eg icon background from white to transparent)
- contour: draw a contour line around an image
- highlight: create a transparent highlight (great for web2.0 style buttons)
- crop (with autocrop)
- notifications (also works on Mac & Windows, uses new system on Jaunty)
- f-spot support via drag&drop or right click mouse context menu (Open With)
- better logging
- support for EXIF.py tag reading
- saving transparent gif images
- support for tiff images with compression (lzw, g3, g4, jpg, zip, ...)
- configuration follows free desktop specification (~/.config, ~/.local/share, ~/.cache)

An example of shiny button made with contour+highlight in an action list:
[img]http://photobatch.wdfiles.com/local--resized-images/action-highlight/feed-icon.png/thumbnail.jpg[/img]

Planned features are:
- gps action: adding gps locations to photos (don't use it yet, is not working)
- variabel border action
- better exif support
- and more surprises ...

For more info: [https://blueprints.launchpad.net/phatch/0.2](https://blueprints.launchpad.net/phatch/0.2)

A lot of work has been done in bug fixing:
[https://bugs.launchpad.net/phatch/+bugs](https://bugs.launchpad.net/phatch/+bugs)

For the release of Phatch 0.2 it is the purpose that ALL correctly reported bugs are solved. I'm happy with any reported bug which has a zip file attached with an action list and example images. Always check if the bug hasn't been reported yet.

You can always file new blueprints (feature requests), but again, check if they are not reported before.

You can install Phatch through my PPA archive (hardy, intrepid, jaunty, karmic):
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)
Add this to your sources.list (replace jaunty with your version): ```
deb [http://ppa.launchpad.net/stani/ppa/ubuntu](http://ppa.launchpad.net/stani/ppa/ubuntu) jaunty main
```
Add the key to your system: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7B0FB2CA
```

Phatch 0.2 is the first release to which others have contributed in development. I'd like to thank especially Nadia Alramli ([http://nadiana.com](http://nadiana.com)) for her great work! I'm also looking forward to the contributions of Erich and Robin.

But Phatch NEEDS you:
- translations are trailing behind, please go for it now:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)
- we need people helping with documentation, send me a private message
- if you know python & pil, why not join our friendly team:
[https://launchpad.net/~phatch-dev](https://launchpad.net/~phatch-dev)
[https://lists.launchpad.net/phatch-dev/](https://lists.launchpad.net/phatch-dev/)
- if you are good in graphics, send me some work you did, so I can see if it fits with Phatch

I am very curious for your reactions!

Stani

PS Warning: Previous Phatch 0.1 action lists are not compatible with Phatch 0.2!

So Good
thanks a lot

---

### Post by AJB2K3 on 2009-06-05
Is raw support added yet?

---

### Post by ManiDhillon on 2009-06-05
Looks quite interesting! I will try it today after I install and update Jaunty! i will let you know what i feel about it!
Thanks for this..

---

### Post by stani on 2009-06-06
@AJB2K3
Raw support is not implemented yet. Which raw tools do you use now? Could you write what you would like Phatch to do concerning raw in this blueprint?:
[https://blueprints.launchpad.net/phatch/+spec/raw-support](https://blueprints.launchpad.net/phatch/+spec/raw-support)

I can't make promises, but we can see what we can do. The more detailed and specific the blueprint gets, the more easy it will be to implement. (Especially if you know I haven't used any of the raw software myself.)

---

### Post by stani on 2009-06-08
New action has been added:
> write tag: write any exif/iptc tag to images (you can copy and paste them from the image inspector)
I've added a screenshot to the first post. Feel free to test it.

[http://photobatch.wikidot.com/action-write-tag](http://photobatch.wikidot.com/action-write-tag)

---

### Post by megamania on 2009-06-08
> **stani said:**
> New action has been added:

I've added a screenshot to the first post. Feel free to test it.
That's what I had been waiting for! 

Unfortunately, it doesn't appear to work for me, since when I try to apply an exif tag it hangs on the first picture.

I tried with a few jpegs (both single files and full directories).

---

### Post by stani on 2009-06-08
> **megamania said:**
> That's what I had been waiting for! 

Unfortunately, it doesn't appear to work for me, since when I try to apply an exif tag it hangs on the first picture.

I tried with a few jpegs (both single files and full directories).
Probably you've run into this bug:
[https://bugs.launchpad.net/phatch/+bug/384548](https://bugs.launchpad.net/phatch/+bug/384548)

It is probably fixed if you update. You can do that easily if you installed from the PPA:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Phatch is at the moment in full development and therefore not stable. Although this might be not nice, it has one big advantage: any reported bug will be fixed as soon as possible.

If you like exif tags, be sure to follow the development of Phatch closely as we will hand out more cool exif candies ;-):
[https://bugs.launchpad.net/phatch/+subscribe](https://bugs.launchpad.net/phatch/+subscribe)

However because this is a new area we need serious testers for exif. If you encounter an error save the action list and some example image(s) and attach it to a bug report:
[https://bugs.launchpad.net/phatch/+bugs](https://bugs.launchpad.net/phatch/+bugs)

---

### Post by stani on 2009-06-09
Another update: Phatch now respects the exif orientation of your images, both in processing as in the Image Inspector.

Thanks for all of you who reported a bug, we fix them at a fast pace:
[https://bugs.launchpad.net/phatch/+bugs](https://bugs.launchpad.net/phatch/+bugs)

Please give us more bugs ;-)

Also it is very important to get Phatch translated right now. Please if you have a minute, translate at least some words:
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

---

### Post by megamania on 2009-06-09
> **stani said:**
> Probably you've run into this bug:
[https://bugs.launchpad.net/phatch/+bug/384548](https://bugs.launchpad.net/phatch/+bug/384548)

That was it, thanks!

And I just translated a bit of the missing translations to Italian...

---

### Post by stani on 2009-06-11
Phatch now has a variable border action. I've made an action list which uses that for a polaroid effect. (It is available from File>Library.

[IMG]http://photobatch.wikidot.com/local--files/tutorial-polaroid/polaroid.png[/IMG]

or a little bit twisted:

[IMG]http://photobatch.wikidot.com/local--files/tutorial-polaroid/polaroid-twisted.png[/IMG]

I attach another example result. Please keep on testing and translating.
[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

Thanks!
Stani

---

### Post by megamania on 2009-06-11
I'm testing Phatch and I must say I like it. I'm also trying to polish and complete the italian translation.

I see you added a Crop action. Do you think lossless crop for jpg pictures could be implemented? That would be a real plus, considering that apparently very few programs can do it.

EDIT: see here --> [http://sylvana.net/jpegcrop/](http://sylvana.net/jpegcrop/)

---

### Post by stani on 2009-06-11
> **megamania said:**
> I'm testing Phatch and I must say I like it. I'm also trying to polish and complete the italian translation.

I see you added a Crop action. Do you think lossless crop for jpg pictures could be implemented? That would be a real plus, considering that apparently very few programs can do it.

EDIT: see here --> [http://sylvana.net/jpegcrop/](http://sylvana.net/jpegcrop/)

Good idea! Please file a blueprint:
[https://blueprints.launchpad.net/phatch](https://blueprints.launchpad.net/phatch)

No promises however. The more people subscribe to the blueprint the more it gets on the table. So recruit your supporters ;-)

---

### Post by megamania on 2009-06-12
> **stani said:**
> Good idea! Please file a blueprint:
[https://blueprints.launchpad.net/phatch](https://blueprints.launchpad.net/phatch)

No promises however. The more people subscribe to the blueprint the more it gets on the table. So recruit your supporters ;-)
No rush. Gthumb supports it so I don't need to have it implemented now, I just thought it would be a good addition.

Have you taken a look at phraymd? I have the feeling that phatch and phraymd could find a way to grow up together and help eachother...

[http://launchpad.net/phraymd](http://launchpad.net/phraymd)

---

### Post by stani on 2009-06-12
Especially if there is no rush, it is good to add a blueprint as otherwise it gets forgotten.

About phraymd, I see they've implemented the "Open With" in the context menu. 

[IMG]http://groups.google.com/group/phraymd/web/phraymd-screenshot-context-menu.png?display=thumb&width=420&height=420[/IMG]

If you have Phatch installed it should appear there automatically and work out of the box. Please file a bug if it doesn't. This could be taken a step further by a plugin for phraymd which detects if Phatch is installed and if it is add a Phatch entry with direct access to all the library action lists. Feel free to contact the phraymd developers. There is more chance if this is requested by users.

---

### Post by hero1900 on 2009-06-12
cool stuff 
i will try it
thanks

---

### Post by stani on 2009-06-15
Phatch now supports a geotag action for your photos. Just pass a gpx file and Phatch will do the rest. It even can generate a cvs report which can open in a spreadsheet program. Please test it!

[http://photobatch.wikidot.com/action-geotag](http://photobatch.wikidot.com/action-geotag)

[IMG]http://clanmills.com/articles/gpsexiftags/gpsexiftags.jpg[/IMG]

PS We are working on improving the exif workflow:
[https://blueprints.launchpad.net/phatch/+spec/save-metadata-action](https://blueprints.launchpad.net/phatch/+spec/save-metadata-action)

---

### Post by spillz on 2009-06-16
> **stani said:**
> Phatch now supports a geotag action for your photos. Just pass a gpx file and Phatch will do the rest. It even can generate a cvs report which can open in a spreadsheet program. Please test it!


nice stani -- I just added preliminary support for viewing and editing geolocation exif data to phraymd. This new feature of phatch will complement phraymd nicely.

---

### Post by stani on 2009-06-17
> **spillz said:**
> nice stani -- I just added preliminary support for viewing and editing geolocation exif data to phraymd. This new feature of phatch will complement phraymd nicely.

Hi spillz, if you are the developer of phraymd, feel free to contact me to see how close our python applications can work together :D

---

### Post by megamania on 2009-06-19
Correct me if I'm wrong, but by what I can see EXIF tagging is not lossless for Jpeg pictures.

I understand the need to resave the pictures if (some of the) other actions are added, but I think the EXIF tagging action should need no "save action" at the end.

---

### Post by stani on 2009-06-19
> **megamania said:**
> Correct me if I'm wrong, but by what I can see EXIF tagging is not lossless for Jpeg pictures.

I understand the need to resave the pictures if (some of the) other actions are added, but I think the EXIF tagging action should need no "save action" at the end.
If you want to save only your metadata, use the 'Save Metadata' action (under the metadata category, new in 0.2) which does this lossless:
[http://photobatch.wikidot.com/action-save-metadata](http://photobatch.wikidot.com/action-save-metadata)

---

### Post by megamania on 2009-06-21
> **stani said:**
> If you want to save only your metadata, use the 'Save Metadata' action (under the metadata category, new in 0.2) which does this lossless:
[http://photobatch.wikidot.com/action-save-metadata](http://photobatch.wikidot.com/action-save-metadata)
Ok, thanks for pointing me into the right direction.

Can I suggest, however, the following amendments: 
- when the "run action" button is pressed,
- check if the action(s) selected involve only metadata manipulation.
- if that's the case, the "save tags" action should be added (not the general "save" action), or you should get a warning about that possibility.

In the future, that could be expanded to lossless operations in general.

---

### Post by stani on 2009-06-21
> **megamania said:**
> Ok, thanks for pointing me into the right direction.

Can I suggest, however, the following amendments: 
- when the "run action" button is pressed,
- check if the action(s) selected involve only metadata manipulation.
- if that's the case, the "save tags" action should be added (not the general "save" action), or you should get a warning about that possibility.

In the future, that could be expanded to lossless operations in general.
Excellent suggestion! Please file a blueprint so it gets on my todo list. (Otherwise I might forget.)
[https://blueprints.launchpad.net/phatch/0.2](https://blueprints.launchpad.net/phatch/0.2)

---

### Post by megamania on 2009-06-22
> **stani said:**
> Excellent suggestion! Please file a blueprint so it gets on my todo list. (Otherwise I might forget.)
[https://blueprints.launchpad.net/phatch/0.2](https://blueprints.launchpad.net/phatch/0.2)
Done. I hope I didn't mess it up (I'm not experienced with the series/goals and maybe I did something wrong)...

---

### Post by stani on 2009-06-22
> **megamania said:**
> Done. I hope I didn't mess it up (I'm not experienced with the series/goals and maybe I did something wrong)...

No, you did it right ... and to reward you, I implemented it already! Please test.

---

### Post by stani on 2009-06-22
> **megamania said:**
> I'm testing Phatch and I must say I like it. I'm also trying to polish and complete the italian translation.

I see you added a Crop action. Do you think lossless crop for jpg pictures could be implemented? That would be a real plus, considering that apparently very few programs can do it.

EDIT: see here --> [http://sylvana.net/jpegcrop/](http://sylvana.net/jpegcrop/)

Lossless jpeg editing has now landed in Phatch. ('Lossless JPEG' action in category metadata or transform.) You can rotate, flip, transpose, crop (with jpegtran), ... even grayscale. Could you please test this action carefully, as I need my time for developing.
Thanks a lot!

---

### Post by ^_Pepe_^ on 2009-07-17
I reach this post and this application looking for something that I usually do with IrfanView in Windows...but this is...amazingly easy and ¡¡¡quick!!!, even with my netbook.

I'm completely glad. Thank you so much for this application. Dont stop developing it.

regards,

^_Pepe_^

---

### Post by cisoprogressivo on 2009-07-20
I really enjoy this program.
Is it there a way to apply an immage as watermark?

Thank you :)

---

### Post by Samhain13 on 2009-07-20
> **^_Pepe_^ said:**
> ...but this is...amazingly easy and ¡¡¡quick!!!, even with my netbook.

Best I got out of Phatch is downsize/downgrade some 900+ high-resolution images in around 5 minutes. It's really a damn good batch processor and cheers to the devs, I owe you guys big time!!! :D

---

### Post by stani on 2009-08-18
Hey guys!

Please do a translation sprint now for Phatch! So I can include Phatch in Karmic. Too many translations are still missing:
[https://translations.launchpad.net/phatch](https://translations.launchpad.net/phatch)

Go! Go!

---

### Post by hellocatfood on 2009-08-19
Really awesome program. I'm glad 0.2 adds metadata support

---

### Post by hellocatfood on 2009-08-19
Is there a way to write metadata to a png file? I know that you can't add an exif or ipct tag to it, but what about just writing to the file anyway? I know Inkscape has achieved something similar.

---

### Post by stani on 2009-08-19
> **hellocatfood said:**
> Is there a way to write metadata to a png file? I know that you can't add an exif or ipct tag to it, but what about just writing to the file anyway? I know Inkscape has achieved something similar.

It might be doable. Please file a blueprint 'png-metadata' here:
[https://blueprints.launchpad.net/phatch](https://blueprints.launchpad.net/phatch)

We'll see what we can do and you'll be following its progress.

---

### Post by stani on 2009-08-26
Great news. Phatch 0.2 got some new features:

- Support for reading camera RAW images

- Support for reading SVG files

- Support for reading PDF files

- Imagemagick actions (all imagemagick functionality can become available in Phatch)

- Blender actions (yes you can do 3d now without starting blender yourself)

- a Geek action to integrate *any* command line application in your workflow, so the sky is the limit

- Image explorer to preview in folder hierarchy which images will be processed or afterwards which ones have been processed

- ...

and much more. Now we really need you to stress test Phatch 0.2 so it can enter the Karmic stable. Spread the word:
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)

Also a lot of new features means a lot of new translations so jump in it:

[https://translations.launchpad.net/phatch/trunk/+pots/phatch](https://translations.launchpad.net/phatch/trunk/+pots/phatch)

---

### Post by hellocatfood on 2009-08-29
Is it possible to export mulit-page pdf's as images using phatch? I've tried to saving a pdf as an image and it only saves the last page

---

### Post by stani on 2009-08-30
> **hellocatfood said:**
> Is it possible to export mulit-page pdf's as images using phatch? I've tried to saving a pdf as an image and it only saves the last page

Maybe ;-) Can you describe your exact user scenario. What do you want to do?

---

### Post by hellocatfood on 2009-08-31
I've got a multiple-page pdf, created with [Alchemy](http://al.chemy.org). I want to export each of those pages as an image (png or jpg). I add a Save action to phatch and then drag the pdf to it. I can't see any options for saving a specific page or range of pages so just click OK. The file explorer comes up an I press Continue. After a time I only get the last page exported as an image.

I just want to export each page as an image. I understand that this could take some time to export, but I don't mind that.

Is that enough info?

---

### Post by stani on 2009-08-31
> **hellocatfood said:**
> I've got a multiple-page pdf, created with [Alchemy](http://al.chemy.org). I want to export each of those pages as an image (png or jpg). I add a Save action to phatch and then drag the pdf to it. I can't see any options for saving a specific page or range of pages so just click OK. The file explorer comes up an I press Continue. After a time I only get the last page exported as an image.

I just want to export each page as an image. I understand that this could take some time to export, but I don't mind that.

Is that enough info?
Almost, what about the paths? Let's say your file is called:
```
/home/hellocatfood/projects/alchemy/demo.pdf
```

What would be the file names of the exported pages? Also note that Phatch at this stage (0.2) would only be able within one action list to export, not to manipulate the exported pages. To manipulate these page images, you would need a separate action list.

---

### Post by hellocatfood on 2009-08-31
> **stani said:**
> Almost, what about the paths? Let's say your file is called:
```
/home/hellocatfood/projects/alchemy/demo.pdf
```

What would be the file names of the exported pages?

I'd want them to be called something like demo_1.png, demo_2.png, demo_3.png etc

---

### Post by stani on 2009-08-31
> **hellocatfood said:**
> I'd want them to be called something like demo_1.png, demo_2.png, demo_3.png etc
OK, if you file a blueprint with these details (just copy & paste), I'll see what I can do:

[https://blueprints.launchpad.net/phatch/+addspec](https://blueprints.launchpad.net/phatch/+addspec)

---

### Post by hellocatfood on 2009-08-31
Before I do that I had a search on Google and found that imagemagick can convert pdf pages to images, [source](http://snipplr.com/view/10361/imagemagick-convert-pdf-to-images/)

As well as providing some more presets for the imagemagick action might it be worth allowing people to add there own custom imagemagick actions to the phatch action list?

---

### Post by stani on 2009-09-02
> **hellocatfood said:**
> Before I do that I had a search on Google and found that imagemagick can convert pdf pages to images, [source](http://snipplr.com/view/10361/imagemagick-convert-pdf-to-images/)
I know that. Phatch uses btw imagemagick to open pdfs. Can you provide the imagemagick command for what you want to do?

> 
As well as providing some more presets for the imagemagick action might it be worth allowing people to add there own custom imagemagick actions to the phatch action list?
That exists already! For that Phatch 0.2 provides the 'Geek' action. Look in your user library (Tools>Browse Library>User). You will find geek.txt there where you can add any commands you wish. However useful commands should be reported to me, so I can maybe include them better (such as multi-image pdf save).

Please try your imagemagick command in the geek action and let me know if it works.

---

### Post by ElSlunko on 2009-09-02
I love this neat little program, been sharing it with some friends and a lot of them have found it easy to use and have stopped bugging me to re-size their images.

---

### Post by bluebyt on 2009-09-04
The link (deb) for Intrepid package doesn't work?

---

### Post by stani on 2009-09-05
> **bluebyt said:**
> The link (deb) for Intrepid package doesn't work?

Sorry you need to use the PPA:
[https://launchpad.net/~stani/+archive/ppa](https://launchpad.net/~stani/+archive/ppa)

There you can also find a link to the Intrepid deb:
[https://launchpad.net/~stani/+archive/ppa/+files/phatch_0.2.0.bzr1191-0ubuntu1~8.10~ppa1_all.deb](https://launchpad.net/~stani/+archive/ppa/+files/phatch_0.2.0.bzr1191-0ubuntu1~8.10~ppa1_all.deb)

But check this link on the PPA page as it changes with every build.

---

