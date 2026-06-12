---
title: "Phatch 0.2 (Photo Batch Processor): Vote for new features!"
date: 2008-03-16
forum: Art &amp; Design
---

### Post by stani on 2008-03-16
Phatch is a photo batch processor with an user friendly gui:
[http://photobatch.stani.be](http://photobatch.stani.be) (ubuntu installer available)

You can read more about Phatch here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

I'd like to hear your feedback for the next version of Phatch 0.2. What are your priorities? I am just curious about your reactions but I will chose anyhow by myself, so it won't be a democratic. I rather listen to good arguments in the discussion which can start in this thread.

Of course you could want all that at once in Phatch 0.2, but that is not realistic. I prefer to concentrate on one major feature for each release.

I originally planned myself live preview. But I got numerous requests for opening up Phatch to external actions.

- external actions: phatch can interoperate with other command line tools such as imagemagick, tufuse, and even blender (why not). This could even be taken a step further and not limit phatch not only to batch process images but any file type (eg html 2 pdf).

- live preview: Phatch could have a window with a test image which updates as soon as one of the parameters in the action list is changed. Phatch would compete more directly with Lightbox. _Disclaimer: Phatch uses Python which is not fast enough for realtime preview. So take in account it will take probably from some seconds to some minutes to update the preview. Don't say I didn't warn you._

- full layer support: Phatch would be able to do multi-layered actions such as in Gimp or Photoshop

- exif & iptc: Right now Phatch can only keep the existing metadata, but does not allow to manipulate it.

- other: you name it...

If you are python developer and feel like joining, maybe we can get more work done together. Your vote for a feature will weight stronger if you commit yourself to writing documentation and tutorials with screenshots for it.

It is time to vote now!
Stani

---

### Post by stani on 2008-03-17
I added a disclaimer to "live preview", so you don't have false expectations.

---

### Post by bvanaerde on 2008-03-17
About the live preview: maybe this can be replaced with a "standard dummy image", to make the preview faster.
It won't be a real preview anymore, but it will still indicate what effect the actions will have on the images.

Live preview doesn't make sense to me, as you're applying the actions to a collection of images. That means you'd have to show a preview of all images, which is a bit overkill, imo.

---

### Post by lyceum on 2008-03-17
Is this suppose to be like the new GIMP?

---

### Post by stani on 2008-03-17
> **bvanaerde said:**
> About the live preview: maybe this can be replaced with a "standard dummy image", to make the preview faster.
It won't be a real preview anymore, but it will still indicate what effect the actions will have on the images.This only makes sense for a *single* action but for a preview of a whole action list it would not make sense as there are the possible combinations into action lists are endless. So this is really a separate thing next to live preview. For that feature someone gives the dummy image he wants and Phatch generates previews for all the actions, which could be displayed from then on when choosing an action.

> Live preview doesn't make sense to me, as you're applying the actions to a collection of images. That means you'd have to show a preview of all images, which is a bit overkill, imo.
I think live preview does make sense because of certain actions and especially in combining them. For example configuration of the action perspective is almost impossible without a live preview. The live preview would not be for all the images but for selected images, such as the image inspector now. I think that live preview would make Phatch even more accessible for graphic newbies.

---

### Post by stani on 2008-03-17
> **lyceum said:**
> Is this suppose to be like the new GIMP?

Do you mean GEGL ([http://www.gegl.org/)?](http://www.gegl.org/)?) In a way Phatch is already working a bit like that. The main difference between Gimp and Phatch is that in Gimp you interact with the image by the mouse, while in Phatch you interact with the image by action lists.

---

### Post by lyceum on 2008-03-18
After playing with it, it looks like a great idea. I can't wait to see the 1.0 release :)

---

### Post by stani on 2008-03-18
> **lyceum said:**
> After playing with it,it looks like a great idea.What Phatch as you played with it or a planned feature?> I can't wait to see the 1.0 release :)Haha, I am very conservative with my version numbers. In fact there is no reason, why 0.1 could not be 1.0 and 0.2 could be 2.0, ... but I like high standards ;-)

---

### Post by lyceum on 2008-03-18
> **stani said:**
> What Phatch as you played with it or a planned feature?Haha, I am very conservative with my version numbers. In fact there is no reason, why 0.1 could not be 1.0 and 0.2 could be 2.0, ... but I like high standards ;-)

The only ones I am really into at this point are the rounded, shadow and water mark. My only grip so far would be that  I could not put my name as the water mark. It would be nice if an artist could upload there own logo and/or type their name and place it where they want the since they want on the page as a branding. Like this:

[http://deathbycanon-stock.deviantart.com/art/Water-Girl-17-56517505](http://deathbycanon-stock.deviantart.com/art/Water-Girl-17-56517505)

When I "water marked" with the Phatch logo I got this huge picture on my picture. To be totally honest, I would be happier if you could make this program run with the GIMP, that way I could click on the Phatch extension and finish my picture faster. But I know that is too much to ask. 

All in all, great job! The one thing I miss from Photo Impact Pro was the window where I could do cool things, like this program can do. I you are looking for a list of things to want to add please let me know. I have one. 

:popcorn:

---

### Post by stani on 2008-03-18
> **lyceum said:**
> The only ones I am really into at this point are the rounded, shadow and water mark. My only grip so far would be that  I could not put my name as the water mark.If you would read the documentation (on [http://photobatch.wikidot.com](http://photobatch.wikidot.com)), you can! In that case you need to choose the "Text" action and you can write with any available font on your system your name on the picture. >  It would be nice if an artist could upload there own logo and/or type their name and place it where they want the since they want on the page as a branding. Again you can already, read the documentation. With watermark you select the option "Offset" and specify where to place it in pixes, % or whatever. (Negative values align from the other side right-left of top-bottom.) > Like this:

[http://deathbycanon-stock.deviantart.com/art/Water-Girl-17-56517505](http://deathbycanon-stock.deviantart.com/art/Water-Girl-17-56517505)
If you have such a font on your system, you could do it with the Text action, or you prepare it in Gimp and use the Watermark action.> 
When I "water marked" with the Phatch logo I got this huge picture on my picture. That is because you choose the scale method of watermark.> To be totally honest, I would be happier if you could make this program run with the GIMP, that way I could click on the Phatch extension and finish my picture faster. But I know that is too much to ask. Phatch and Gimp serve different goals:
[http://photobatch.wikidot.com/faq#toc4](http://photobatch.wikidot.com/faq#toc4)
> 
All in all, great job! The one thing I miss from Photo Impact Pro was the window where I could do cool things, like this program can do. I you are looking for a list of things to want to add please let me know. I have one. 
You can add your wishes here:
[https://blueprints.launchpad.net/phatch](https://blueprints.launchpad.net/phatch)

First look carefully if it has not been proposed yet or if it is better to add it to an existing blueprint.

---

### Post by lyceum on 2008-03-18
Thanks for the info. I am sure I am not the best judge, as I just started using it this morning. I do think this will be a great program. I like the idea that if I have a lot of pictures and need to do the same thing to them I can do it quickly.

---

### Post by andersja on 2008-03-18
Phatch looks interesting indeed! 

I posted two wishlist items of my own as launchpad "Wishlist" bugs: GPS data integration for localisation tagging of photos + RAW processing.

[https://bugs.launchpad.net/phatch/+bug/203495](https://bugs.launchpad.net/phatch/+bug/203495)
[https://bugs.launchpad.net/phatch/+bug/203497](https://bugs.launchpad.net/phatch/+bug/203497)

If someone likes the sound of those - feel free to draft up blueprints!

---

### Post by bvanaerde on 2008-03-18
> **stani said:**
> For that feature someone gives the dummy image he wants and Phatch generates previews for all the actions, which could be displayed from then on when choosing an action.
Actually, that is what I meant: the result still needs to be generated. But with a standard image (low quality, small size, ...), it can be processed faster.
I'm not sure if it's needed that the user has to select a picture himself. Imagine someone choosing a hi-res >4MB picture...

---

### Post by xxxYURAxxx on 2008-03-18
i think true way to better your application - create image gallery

---

### Post by Rhubarb on 2008-04-07
I have a small wish list that I'd like to see implemented in phatch / stand alone CLI program:

[LIST]
[*]Support for writing text metadata info to PNG files (to be applied to all PNG pictures in a batch and / or individual PNG pictures)

[*]Compressing a batch of PNG pictures so they consume less file size (no loss in quality) - much like pngcrush (as found in the ubuntu repos)
[/LIST]

It's quite odd that there are programs to extract the metadata information from a PNG, but no programs exist that allow me to add text comments into PNG images.

I love your program phatch very much <3

---

### Post by stani on 2008-04-07
> **Rhubarb said:**
> I have a small wish list that I'd like to see implemented in phatch / stand alone CLI program:

[LIST]
[*]Support for writing text metadata info to PNG files (to be applied to all PNG pictures in a batch and / or individual PNG pictures)

[*]Compressing a batch of PNG pictures so they consume less file size (no loss in quality) - much like pngcrush (as found in the ubuntu repos)
[/LIST]
For the first wish you can vote on "changing exif & iptc values". For the second wish you should vote on "external actions" so Phatch can call pngcrush. I am wondering if you put in Phatch the compression level for PNG to the maximum, you get similar results as pngcrush. Can you give me some example data (about size) between Phatch and pngcrush?
> 
It's quite odd that there are programs to extract the metadata information from a PNG, but no programs exist that allow me to add text comments into PNG images.

I love your program phatch very much <3
The exif library which Phatch uses, already permits writing metadata. So it is more matter of implementing the user interface and adapting Phatch's data model to it. Anyone who is familiar with python could help implementing it.

---

### Post by Rhubarb on 2008-04-07
Oops, I'm an idiot, I had already voted (voted for other), and I just discovered pngcrush can add text based metadata to PNG files anyhow (have a look at the man page for pngcrush).

That, and I didn't realise that phatch could increase the compression level upon saving.

I've just tested file size difference between phatch and pngcrush (for a 3586x2496 photo at 8 bits per channel):
phatch: 11.3MB
pngcrush: 10.9MB

The command line used for pngcrush was: ***pngcrush original.png pngcrushed.png***
I was using phatch 0.1.3

I will endeavour to learn some python myself soon - so I may be able to help you out in a month or so.

**Edit**: It seems pngcrush won't save text comments for me, for info I used:  ***pngcrush -text b "Description:" "This is the description" original.png metadata-ised.png***
(There's a handy CLI tool called **pngmeta** to extract meta information from PNG files.)

---

### Post by stani on 2008-04-07
I would not recommend using phatch as a filename. Rather use:
```
<filename>_phatch
```

Otherwise a your images will be saved with the same name, so you end up with one image per folder.

---

### Post by itsanudae on 2008-04-12
Hello All,

While you are thinking of Phatch 0.2 Features...

Prepare for a look at a Phatch Screenshot Tour for version 0.1.3 on the Phatch Wiki. 

An initial Tour is Scheduled for Monday, April 14th at 06:00pm. 

This will give you an overview of the current stable interface, a writeup on some of the features, and help you decide what direction to lobby for Phatch to take for 0.2.

A detailed Screenshot Tour is scheduled for Friday, April 18th, 2008 @ 06:00pm (14:00) PST.

 I will mirror it on [**_xubuntupals.ning.com_**]("http://xubuntupals.ning.com/"), where you can drop by, join into the network, and actively post in the [***[I]_Phatch Discussion_*[/I]**]("http://xubuntupals.ning.com/forum/topic/show?id=2058368%3ATopic%3A322") on the Screenshot Tour, and ask questions that I will be there for to answer in Real Time. This event will last from 06:00pm (14:00) PST until 10:00pm (18:00) PST.

---

