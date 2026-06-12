---
title: "Photo: gThumb vs F-Spot vs digiKam vs Picasa?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-31
Greetings, forum community!

I am struggling to gradually convert from XP to Edgy via dual-boot.
After a discouraging start, it is looking better & better.  :)

Today's topic is photo-handling. 
I am a noobie, so don't hesitate to correct anything inaccurate I may say here....

Up to now with XP I have been using Picasa & find it meets my very modest needs pretty well. (Except for lack of convenient 'Tag' process - I would like to have a chart of previous tags & just click them in, instead of current keywords you need to remember - I think Picasa is working on this).
Mainly I use just the basics like: Crop - Straighten - Fill in - Redeye - Export & Print:  and it does all this OK.  Nothing fancy at the moment.

In Ubuntu, I nervously hooked up my Canon A85 (heard a lot about Canon/Linux incompatibility) and was delighted it immediately found & identified the camera & downloaded the pictures! 
GREAT!  :)

Actually it only loaded them to gThumb, which seems to be a very limited image viewer with no retouch tools, so not a good place to start?

Then I found F-Spot & imported my pictures there - but this left me with duplicate images on file (I think..) which I would not want. I suppose I can transfer them without duplicating, but who wants to bother with all that every time?
Browsing forums, I found I should be able to get Ubuntu to import directly from camera to F-Spot by going:
System > Preferences > Removable Drives and Media > Cameras > Browse...   but was unable to "Browse to select a Program to Import.." 'cos without 'Program Files' I don't know where to find F-Spot (yet, I am still looking..).
I copy/pasted "f-spot-import" from the forum post and it works fine, but how would any GUI-centered noobie like me be able to do this, just stuck in front of his screen? Who could imagine you need to replace "gnome-volume-manager-gthumb %h" by "f-spot-import"?

So now I only have one copy of my images and I can do:  Crop - Fill in - Redeye & Export OK. (Haven't checked 'Print' yet - that's another story...)
Except that when I crop  or  fill-in, I generate another big file for each image so I need to either live with huge image memory space (it's too big already) or sacrifice my originals. I prefer the way Picasa handles this, keeping originals intact & storing modifications in tiny files. 
I also didn't find any way of 'straightening' which I absolutely need.
Is it there somewhere?

I have not tried digiKam yet, but from the site: [http://www.digikam.org/](http://www.digikam.org/)  it looks as though it will do all I want (Crop - Straighten - Fill in - Redeye - Export & Print) easily & with some kind of 'Tag' as well.
Is that right that it will do 'Straighten' (= slight rotation) ?
Does it handle modifications as space-efficiently as Picasa, or does it also create big duplicate files?

I did not try Picasa under Ubuntu yet either, though I know it is now possible - I suppose the features are exactly the same as under Windows. Is that true?

One feature I would like but have not found anywhere yet, is to de-perpective images. Typically with a too-close & up-facing shot of a castle or cathedral, the top is (obviously!) tapered in & it would be neat to be able to expand it to square-up the result... (Yeah - I know I should stand further back & use telephoto, but it's not always feasible. I also know I should hold the camera straight & then I wouldn't need to straighten all my images, but then nobody's perfect!)

So - I would be interested to hear any advice & comments on the best way to go now.

Thanks very much!

---

### Post by gn2 on 2006-12-31
I have used Digikam, with PCLinuxOS and it's fine.

One ofthe joys of Linux is you can try software out for free, and if it doesn't suit, just remove it.

The Gimp is fully featured and will do almost anything but is far from user friendly.

---

### Post by bailout on 2006-12-31
There are packages on the digikam site for digikam 9 that was released just before Christmas. It is quite a big update.

Digikam works by having one location for your photos. I have all of mine in folders on a shared fat32 partition so I just pointed digikam to that directory the first time I ran it and that is now my default photo location.

If you install digikamplugins and kipi plugins then you can do a lot of editing in digikam. I know it has a lens distortion correcting plugin but not entirely sure about perspective (in windows now so can't check) but it probably does. Digikam also handles most raw files and will handle 16 bit images, unlike gimp.

Definitely give it a go and see which suits you best.

---

### Post by slimdog360 on 2006-12-31
I personally use digikam (the new version), there is a repository for it somewhere but I cant find it at the moment. Its on my other computer so tomorrow if I can remember I'll post it here.

As an aside I noticed you said you had a bit of trouble finding where your applications were. Here is a little tip when you need to find something. Open a terminal and type ```
whereis blablabla
``` of course replaing the blablabla part with what your trying to find. It is spelling sensitive though so make sure you know the name of the program. Note that the whereis part is **meant** to be one word. 

Linux programs are often installed into a few different places so you will get a few different answers of where your application is. The 'executable' file for the program will usually be placed in your /usr/bin directory so that is often a good place to start.
Try this and see for your self how it works ```
whereis fspot
``` you should get nothing coming up right, this is because of the spelling. Now try ```
whereis f-spot
```Now you should be getting a few different answers as to where the application is. Note that the 'executable' file as I mentioned before is in /usr/bin/f-spot.
So when you want to do that 'browse to select a folder' thingy you now know where to point it to, the /usr/bin/f-spot file.

I hoped that helped and didnt confuse you.

Picasa for linux is really easy to install you can do it either from here [http://picasa.google.com/linux/download.html]("http://picasa.google.com/linux/download.html")


Or you can do it this way, for you Im guessing this would be the easiest way. Just open synaptic, click settings --> Repositories -->click the 'third party' tab--> then click the add button. All you would have to do then is copy the line ```
deb http://dl.google.com/linux/deb/ stable non-free
``` and paste it into the right place. This way you would have the ability to automatically update picasa with the rest of your system.
To install picasa from using this method all you have to do is hit the reload tab in synaptic then search for picasa. Simple eh.

---

### Post by gummibaerchen on 2006-12-31
from my sources.list:

# Mono Programs
deb [http://directhex.mfgames.com/](http://directhex.mfgames.com/) ./

All the latest Versions (except the very new banshee).

works nice (also f-spot 0.3 is included)

---

### Post by xabbott on 2006-12-31
Picasa.

---

### Post by Magnes on 2006-12-31
Picasa for Linux is (almost) exacly like Picasa for Windows. I use it but I don't recommend it:
- it's closed, you don't know what the program really does, it can break, it can be buggy, it can send your personal data to Google,
- it's running through wine, that means that bugs could be not only in Picasa itself but in wine library it uses, also it is slower than native applications,
- it's very slow in development, there wasn't a new version for a VERY long time (for it's very long ;) ),
- importing photos from camera hangs linux Picasa for me.

If you don't dislike F-Spot (like I does :) ) use it. It's great, it has the same method of handling images (non destructive) as Picasa (well, it is a strange application but I suppose one can get used to it) .
(sorry for my English)

---

### Post by xabbott on 2006-12-31
> **Magnes said:**
>  also it is slower than native applications

Just because something uses Wine does not mean it is any slower than a native application. That comes from a mis understanding of how Wine works.

---

### Post by 2CV67 on 2007-01-01
Thanks to all for those helpful replies!
Special thanks to slimdog360 for taking the trouble to step me through the Terminal codes! This is the kind of help a knooby kneeds!

Well - I poked about a bit in F-Spot, but did not find anything for perspective or slight rotation (it may well be there - at my stage in Ubuntu it is easy to miss big things...).

Next I looked at digikam & at first was not impressed, but in RTFM-ing I started to find all kinds of goodies & plugins which look very promising.

I installed kipi plugins through Synaptic & was surprised they didn't seem to match the good news I had read about in the manual - then I realized the manual was refering to 'DigikamImagePlugins' at [http://extragear.kde.org/apps/digikamimageplugins](http://extragear.kde.org/apps/digikamimageplugins) & not kipi.

So then I installed DigikamImagePlugins, again via Synaptic & WOW!!!

DigiKam will now do all the perspective & rotation stuff I wanted & of course a tremendous variety of color, texture & usual things too.

So I think I will be switching to DigiKam, just regretting slightly Picasa's neat trick of keeping original images intact while storing modifications efficiently.
I shall just have to get used to being more careful before finally saving my edited images.

Thanks again everyone!

---

### Post by Magnes on 2007-01-01
> **xabbott said:**
> Just because something uses Wine does not mean it is any slower than a native application. That comes from a mis understanding of how Wine works.

I know that, I use some programs in WINE that are very fast. But Picasa Linux IS slower than Windows version.

---

### Post by Apipote on 2007-07-11
I can't export pictures to picasa web, with digikam.
Tip or trick please?
Regards

---

