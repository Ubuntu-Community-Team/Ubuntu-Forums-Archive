---
title: "Better alternative to GIMP"
date: 2012-10-20
forum: Art &amp; Design
---

### Post by SpeedGonzales on 2012-10-20
Hi Ubuntu Forums,

I've been a long time Ubuntu fan.  I like Ubuntu 12 so far, although I've had to switch to Gnome classic.

I really used to like the GIMP program however the new changes are really annoying.  The save and export feature is driving me insane.  

Its really difficult to change brush sizes.  I miss the old version.

Is there a free alternative to GIMP?  I need a relatively fast program which has some decent features

I've tried MyPaint and find it frustrating that you cannot zoom in using the mouse wheel.  Ideally I'd like to install the old version of GIMP found in Ubuntu 10 but I really don't know how.

---

### Post by zombifier25 on 2012-10-20
Personally I think GIMP is the most decent.

If you want an alternative, Pinta is pretty good. It's supposed to be a clone of Paint.NET, one of the best image manipulation tool for Windows.

---

### Post by kc1di on 2012-10-20
Pinta +1

---

### Post by SpeedGonzales on 2012-10-20
Thank you, I'm installing Pinta now.  I'll let you know how I find it.

---

### Post by SpeedGonzales on 2012-10-20
Thank you so much kc1di and zombifier25!!!! 

Pinta is spot on, its exactly what I've been looking for.  Now I can get back to my creative projects.  I'm very happy.

---

### Post by submarinekitty2 on 2012-10-26
Just to add: Krita is excellent for digital painting (it's in the default repo). It's like a free Corel Painter (it even has a drag-pen-to-resize-brush ala PS/Painter/Artrage... you know, 'cause pressing L/R brackets to change brush size is horribad). For pure editing though, we're all stuck with GIMP.

---

### Post by barretiano on 2012-11-07
Hello everybody,
i like to ask for your help please , how /where do i get any old version of GIMP the new one is a nightmare for me and i have try  to get used to the export and save new way but i cant i just cant and is in UBUNTU that is has become specially corrupted or mixed up or i just dont know what is going on,
i have re-installed many times but nothing is just a mess ,

please how do i get any old version prior to the last big chance.

i thank the people who work hard on the new format but i just not working for
me
thanks

> **SpeedGonzales said:**
> Hi Ubuntu Forums,

I've been a long time Ubuntu fan.  I like Ubuntu 12 so far, although I've had to switch to Gnome classic.

I really used to like the GIMP program however the new changes are really annoying.  The save and export feature is driving me insane.  

Its really difficult to change brush sizes.  I miss the old version.

Is there a free alternative to GIMP?  I need a relatively fast program which has some decent features

I've tried MyPaint and find it frustrating that you cannot zoom in using the mouse wheel.  Ideally I'd like to install the old version of GIMP found in Ubuntu 10 but I really don't know how.

---

### Post by Inoki on 2012-11-07
I don't get your picture what's wrong with GIMP. I've been using it for a while and can loudly state "Who needs Photoshop anyway?" Everything you can do in Photoshop you can do with GIMP. You'll get the same results, it only requires a little bit more effort, but in the end it's worth it and you're just more proud.

Photoshop is designed the way that it does most things for the user and in the end you'll end up asking "who did that? was it the artist, or the program?" Sorry, but that is just lame.

Soon you'll be able to command those programs with your voice. Will that still make you an artist?

---

### Post by NewAmercnClasic on 2012-11-12
I believe in a few versions gimp will be much better than Photoshop (it is much faster, and a much more attractive price), however currently it is immediately below it (especially from a usability standpoint).  It really could benefit from gimp specific GUI layout themes.

---

### Post by offgridguy on 2012-11-12
Always looking for something different in the way of photo editing, thanks to all
for the input.

---

### Post by prokoudine on 2012-11-13
> **Anathaen said:**
> Everything you can do in Photoshop you can do with GIMP. You'll get the same results, it only requires a little bit more effort, but in the end it's worth it and you're just more proud.

Photoshop is designed the way that it does most things for the user and in the end you'll end up asking "who did that? was it the artist, or the program?" Sorry, but that is just lame.

This is an incredibly misleading statement. Both parts of it.

1. You cannot do everything with GIMP. For instance, there is no free transform tool in GIMP, and no even remote substitutions for it exist. In the roadmap it currently has a rather low priority. 

It's also not possible to make non-destructive changes such as adjustment layers or layer effects. The only existing bunch of scripts for layer effects provide a similar UI, but you can't adjust settings after you applied an effect. So you have to redo things again and again. And that's just loss of time.

2. Photoshop isn't designed that way. It's designed to remove as many roadblock as possible and to unclutter the work of its users. So that they could focus on actual work. Hence your argument about "who did the work" simply doesn't apply unless for some obscure reason you were referring to extensive use of third-party actions. Which anyway isn't what everybody mostly does.

So let's be honest. Just because GIMP is free, and Photoshop is proprietary, GIMP-powered designs aren't true art by humans, and Photoshop-powered designs aren't computer generated art.

Similarly, GIMP doesn't provide all the features that Photoshop has. Some of these features are irrelevant for most users, but a lot of them are quite important and help you complete your work faster.

> **barretiano said:**
> Hello everybody,
i like to ask for your help please , how /where do i get any old version of GIMP the new one is a nightmare for me

I suppose 12.10 ships 2.8 now? In that case you will have to build 2.6 yourself.

sudo apt-get build-dep gimp

will get you all dependencies

then you can fetch sources and do the usual

./configure && make && sudo make install

routine.


> **SpeedGonzales said:**
> I've tried MyPaint and find it frustrating that you cannot zoom in using the mouse wheel.

Works just fine for me. Although I'm using a build from Git.

---

### Post by Inoki on 2012-11-17
> **prokoudine said:**
> This is an incredibly misleading statement. Both parts of it.

1. You cannot do everything with GIMP. For instance, there is no free transform tool in GIMP, and no even remote substitutions for it exist. In the roadmap it currently has a rather low priority. 

It's also not possible to make non-destructive changes such as adjustment layers or layer effects. The only existing bunch of scripts for layer effects provide a similar UI, but you can't adjust settings after you applied an effect. So you have to redo things again and again. And that's just loss of time.

2. Photoshop isn't designed that way. It's designed to remove as many roadblock as possible and to unclutter the work of its users. So that they could focus on actual work. Hence your argument about "who did the work" simply doesn't apply unless for some obscure reason you were referring to extensive use of third-party actions. Which anyway isn't what everybody mostly does.

So let's be honest. Just because GIMP is free, and Photoshop is proprietary, GIMP-powered designs aren't true art by humans, and Photoshop-powered designs aren't computer generated art.

Similarly, GIMP doesn't provide all the features that Photoshop has. Some of these features are irrelevant for most users, but a lot of them are quite important and help you complete your work faster.
This man: [http://dctb.deviantart.com/](http://dctb.deviantart.com/) uses only GIMP for his art. Tell me what difference you see here between Photoshop and GIMP.

The only real difference between GIMP and Photoshop is that with GIMP things require more effort than with Photoshop, cause Photoshop has a few tools GIMP doesn't, but that doesn't mean you cannot reproduce those effects. It may take more time, more effort, but you can reproduce things in GIMP.

---

### Post by Inoki on 2012-11-17
Ya, one more thing, art ain't about tools.

---

### Post by prokoudine on 2012-11-17
> **Anathaen said:**
> This man: [http://dctb.deviantart.com/](http://dctb.deviantart.com/) uses only GIMP for his art. Tell me what difference you see here between Photoshop and GIMP.

Dude, there's no need to tell me about what GIMP can do :)

> **Anathaen said:**
> The only real difference between GIMP and Photoshop is that with GIMP things require more effort than with Photoshop, cause Photoshop has a few tools GIMP doesn't, but that doesn't mean you cannot reproduce those effects.

Nope, it actually means exactly that: you can't do certain things at all (like the free transformation or deep painting), and doing other things with GIMP is counterproductive.

> **Anathaen said:**
> Ya, one more thing, art ain't about tools.

Let's talk about it when you try painting on an OpenEXR image :)

---

### Post by Jorhyan on 2013-03-15
> **Anathaen said:**
> I don't get your picture what's wrong with GIMP. I've been using it for a while and can loudly state "Who needs Photoshop anyway?" Everything you can do in Photoshop you can do with GIMP. You'll get the same results, it only requires a little bit more effort, but in the end it's worth it and you're just more proud.

  > **prokoudine said:**
> This is an incredibly misleading statement. Both parts of it.

 1. You cannot do everything with GIMP. For instance, there is no free transform tool in GIMP, and no even remote substitutions for it exist. In the roadmap it currently has a rather low priority. I am a user of Gimp. You can indeed do everything in Gimp that you can do in Photoshop. I have used Gimp for about a month now. I have used PS, PSP, Fireworks, and a host of other top Imaging Programs over the last ten years. I found it hard to believe that a free program would be as powerful as the top paid programs until I downloaded Gimp and used it. There is a free transform tool in Gimp. It's called the cage tool. You use it like you would the pen/path tool to outline the parts of an object you want to transform. If you put points around the whole object, then you can free transform certain parts of the object from that point and then on to the next point etc. It's actually better than the free transform tool in PS. As for the other arguments, I believe that Anathaen mentioned that even though it would require "more" work, you can perform all of the same functions in Gimp that you can in PS. I for one do not use any pads or laser pens and prefer to draw with my mouse (mostly using the pen tool). I agree with Anathaen and think it is refreshing to actually have to create your own work/images instead of doing a lot of button mashing.

---

### Post by prokoudine on 2013-03-22
> **Jorhyan said:**
> I am a user of Gimp. You can indeed do everything in Gimp that you can do in Photoshop.

— No, you can't
— Yes, you can!
— ...and so on'

LOL

If you say that you really used "PS, PSP, Fireworks, and a host of other top Imaging Programs over the last ten years", then you obviously didn't find any use for lots of features in them. In other words, your use of the apps was very limited.

> **Jorhyan said:**
> There is a free transform tool in Gimp. It's called the cage tool.

They are different tools. Each of them is better than the other for certain tasks. Just use them long enough to understand the difference.

---

### Post by Derelinquat fenestras on 2013-05-10
Here Here!
I used photoshop for a few years around the time I switched to Ubuntu, and I found GIMP and I could do everything better actually than photoshop.  Plus all of the options provided by the GIMP plugin registry just made it to appealing to ever go back!

---

### Post by Zteam on 2013-05-10
Gimp is pretty amazing, but it isn't as powerful as Photoshop.


btw  Prokoudine is one of developers behind Gimp, so arguing with him, that Gimp is more powerful than PS, is arguing against the reality.

With that said, I use Gimp, nearly everyday, and I'm very happy with it.

---

### Post by kurt18947 on 2013-05-11
please delete

---

### Post by Buntu Bunny on 2013-05-11
Wow, what a conversation. I've been pretty happy with Gimp and prefer the newer version because I like having everything in one window. Have never even tried Photoshop. All that said, I'm always curious about something new, so thanks for the info about Pinta. I'll have to give it a try.

---

### Post by Buntu Bunny on 2013-05-11
OK, very nice. I like that it can zoom to more than 800%. I like that it's features are all the basic, most used ones. Had a little trouble figuring how to crop, also how to how many kilobytes I'm optimising to. I'll have to play around with it more. Not much for a user manual though. Haven't tried it for actual painting yet, but I don't do much of that anyway.

---

### Post by SeijiSensei on 2013-05-12
Last I checked GIMP had some limitations that limits its use by professionals.  There is no support for PANTONE® colors, which are encumbered with intellectual property claims.  Specifying colors by PANTONE® code is pretty crucial for print work.  There is also no native support for the [CMYK]("https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP") color model.

Most people who post on forums like this saying there is no difference between GIMP and Photoshop probably have only used these programs to create or edit electronic images.  The print world is a whole 'nother ballgame.

Like the OP, I find the new differentiation in the File menu between Save (meaning .xcf) and Export (everything else) annoying. It is inconsistent with most GUI designs where the filetype determines the format as was the method in 2.6.  I really don't see the value in changing it.  I also liked having a tool's options open automatically in the lower half of the toolbox.  Now there's a message about drag-and-drop there, but I cannot get it to work for me.  If I double-click a tool, it opens the options in a separate window.  I've tried dragging that window onto the toolbar to no avail.  If anyone has a quick answer to this, I'd appreciate it.  Otherwise I'll do some research.

I think I might compile v 2.6 in /usr/local, so I can run both versions.

Edit: Not as easy as it looks.  I've again encountered versioning problems with GEGL.

---

### Post by Buntu Bunny on 2013-05-12
> **SeijiSensei said:**
>   The print world is a whole 'nother ballgame.

That's a problem I'm running into, Gimp being an example. It seems to me that professional lookint preparation for print is sorely lacking with Linux in general.

---

### Post by Rukiri on 2013-05-12
Print has never been that great in Linux, and if you're doing prints I'd probably stay with the industry standard which is Photoshop. There's krita if you like painting.  Linux to me has a long long way to go before it's ready for the desktop, print is just one example that needs serious work, gfx being the second. Lightworks will be great once it's completed, the alpha was alright but not there just yet, the windows counterpart is runs awesomely and is what I use for video editing so I can't wait for the full version on Linux!    I think once Linux has more of a marketshare I'd love to see some professional applications like Photoshop just to name one land in Linux, and along with pro audio creation and editing software.

---

### Post by Buntu Bunny on 2013-05-13
I'm looking particularly at text printing with photos and diagrams, as in a self-published paperback. I can do everything in Linux except convert the finished manuscript to PDF/X-1a:2001. Only Acrobat distiller does this, apparently.

---

### Post by Dry Lips on 2013-05-14
> **Buntu Bunny said:**
> I'm looking particularly at text printing with photos and diagrams, as in a self-published paperback. I can do everything in Linux except convert the finished manuscript to PDF/X-1a:2001. Only Acrobat distiller does this, apparently.


Are you sure you need PDF/X? Won't PDF 1.4 (supported by Scribus) do the trick?

---

### Post by Buntu Bunny on 2013-05-15
> **Dry Lips said:**
> Are you sure you need PDF/X? Won't PDF 1.4 (supported by Scribus) do the trick?

Unfortunately, yes. I'm looking at self-publishing a book through Lightening Source. They require manuscripts to be submitted in PDF/X-1a:2001. I read somewhere that Scribus 1.5 is supposed to do this, but it's still in the testing stage. When I get to that point I may download it to see what I can do, but I'm not exceptionally geeky so I doubt I could tell a bug from user error. ;)

---

### Post by Dry Lips on 2013-05-16
> **Buntu Bunny said:**
> Unfortunately, yes. I'm looking at self-publishing a book through Lightening Source. They require manuscripts to be submitted in PDF/X-1a:2001. I read somewhere that Scribus 1.5 is supposed to do this, but it's still in the testing stage. When I get to that point I may download it to see what I can do, but I'm not exceptionally geeky so I doubt I could tell a bug from user error. ;)

Ok, I'm no expert on this issue, but according to wikipedia [COLOR=#000000][FONT=sans-serif]PDF/X-1a:2001 is based on PDF 1.3 with the addition of "blind exhange and Spot colours." Anyway, have a look at this, perhaps there is a way around your problem?

[/FONT][/COLOR][http://www.prepressure.com/pdf/basics/pdfx-3](http://www.prepressure.com/pdf/basics/pdfx-3)[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by Buntu Bunny on 2013-05-16
> **Dry Lips said:**
> Ok, I'm no expert on this issue, but according to wikipedia [COLOR=#000000][FONT=sans-serif]PDF/X-1a:2001 is based on PDF 1.3 with the addition of "blind exhange and Spot colours." Anyway, have a look at this, perhaps there is a way around your problem?

[/FONT][/COLOR][http://www.prepressure.com/pdf/basics/pdfx-3](http://www.prepressure.com/pdf/basics/pdfx-3)[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]

Dry Lips, thank you for the link! I'm no expert either and have been scouring the internet on this issue, so all leads are welcome. I noted that the article you linked to differentiated between PDF/X-3 and PDF/X-1a. I know that PDF/X-1a:2001 has something to do with CMYK for color, which is required for print, as opposed to RGB for the web. 

I also know that Lightning Source uses Adobe software for their print set-up and requests that documents sent to them be prepared in Acrobat Distiller (which only comes packaged with Acrobat Professional versions 6 and up) for the PDF/X-1a:2001 format. 

I am definitely looking for workarounds, as I would love to do this with all open source. For this first time, though, I may break down and go with Adobe. It's been an amazing learning curve, and the first time at least, I want to get it right. :D

---

### Post by Dry Lips on 2013-05-17
Good luck, then! :)

And yeah, Adobe's products have many features that you don't get in open source software. But they are expensive, though.

---

### Post by chmegr on 2013-05-18
GIMP works great for me....

---

### Post by Buntu Bunny on 2013-05-18
> **Dry Lips said:**
> Good luck, then! :)

And yeah, Adobe's products have many features that you don't get in open source software. But they are expensive, though.

Thanks! I found an old version on Amazon for $80.  :) I have an old computer running XP, so it will only be used for that. I'd still love to be able to do it all on Linux. Maybe someday!

---

### Post by pixiq on 2013-07-03
Interesting discussion ... but gimp has been good enough for me.

---

### Post by kurt18947 on 2013-07-04
> **Dry Lips said:**
> Good luck, then! :)

And yeah, Adobe's products have many features that you don't get in open source software. But they are expensive, though.

If my understanding is correct, the new Adobe subscription model might be a boon in this situation.  One could just pay for 1 months' usage.  I'm not clear if one would need to purchase software initially, or if it's all downloaded and the only cost is the monthly subscription.

---

### Post by Baldrick_NZ on 2013-10-13
Hmmm... I'm an amature photographer who shoots mainly landscapes and some portraiture. 
I usually use Aftershot Pro (Linux edition) for all my RAW work, then pass it to Gimp to make any cosmetic changes, ready for print.

I think that there are a few quirks that need to be settled within Gimp, but the print quality for me is outstanding. So, am I missing something here?

For me, I'm a great supporter of the underdog. I question why most in my profession insist on paying an exorbitant amount for software that, in the main, Gimp and Aftershot Pro can do adequately for a mere fraction of the price. Sure Photoshop may have a few more features that some would use regularly, but for me I would use them so infrequently that it would be near impossible to justify making the purchase.

Secondly, I have a pretty profound sense of fairness, and as a result I refuse to support any software company that blind-sides Linux. If it's good enough to support Windows and iMac, then it's good enough to support Linux too. Especially for a corporate giant like Adobe!

Just my two cents...

---

### Post by abrianb on 2013-11-18
I use Aftershot pro and gimp on a regular basis. I can tell you exactly why professionals are reluctant to use them. Try taking 75 photos in one setting where light and color will be consistant throughout. Then start editing with Aftershot, you can pull up one image get it looking good and copy your settings to all the others so that you don't have to look at each individually. All is well so far. Now you come to an image that needs more work so you want to export to gimp. You can use jpeg but you are going to start losing quality if you do, or you can use tiff its lossless. No if you use tiff you lose color control because you have to take your image down to 8 bit color. You really don't want to go down to 8 bit because you put a lot of effort and money into buying gear to color manage your process from camera to monitor to printer so that your prints have spot on color. So you have to get over it. You get done and you decide to print 50 of the 75 images. Gimp prints real well. One at a time. Open an image, print an image, close an image, repeat. No professional will spend the time it takes do the job with gimp. I could print with AfterShot. Well after the last update I lost printing in Aftershot. But before I lost it there were a few problems. It did print very well and you could batch print, saving time and improving work flow. The thing is the problems, select your papersize, no option for the very common 4x6 size, just use a6, no the system does not realize a6 and 4x6 should be interchangable so none of your 4x6 ratio photos from your expensive DSLR will fit without being cropped. You can pick a custom paper size, but you have to do it twice, once when set the print in que and once again when you click print you have to choose it for your printer. If that was not enough you will soon find that when you are done printing the first photo in the batch the que will stop because you have to enter the custom paper size again. AfterShot not only does not remember settings from one batch to the next it does not remember them from one photo in a batch to the next. (it works fine in windows). Did I mention that your output will not be centered and will have an offset border even when printing borderless. The only program that i have found that will allow you to easily and quickly select and print (centered on the paper) is picasa. You just have to put up with 300 dpi prints only. I really enjoy using Ubuntu, I hope picasa 3.9 does not stop running under wine because I would not be able to print 4x6. I have tried countless programs to print photos in linux and none really work satisfactorily. Most will not center photos on the paper for bordered printing, most will not automatically interface with your printer driver like windows programs. I am not trying to be negative, I am a user of Ubuntu and Gimp and ASP. Printing photos in Ubuntu is just not supported in a manner that could be called ready for mainstream.

---

### Post by Guilden_NL on 2013-12-18
No doubt about the power of Gimp, but the UI is frustrating to use for even simple tasks.   The Help is not very much help!  I frequently have to Google how to do even a simple task.  I use it maybe 10 times/month, just long enough apart to forget how I performed a task before.  As for UI, early Paint Shop Pro (circa 1994-95) was great.  Easy to see how to perform easy tasks, yet the powerful stuff was there in the background.

---

