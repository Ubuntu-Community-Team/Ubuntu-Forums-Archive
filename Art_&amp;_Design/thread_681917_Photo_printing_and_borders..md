---
title: "Photo printing and borders."
date: 2008-01-29
forum: Art &amp; Design
---

### Post by robfindlay on 2008-01-29
Okay so I take my pics, load them up in gimp, crop manipulate or whathave you. 

However gimp will not see my printer, so I end up trying to print with different graphics programs and none of them will print to a 4x6 without leaving HUGE borders. 

is their some "size" and proportion I should scale the image to before trying to print it?  

Am I making sense? HELP! 

-Rob

---

### Post by robfindlay on 2008-01-29
So why don't i have an option to print under GIMP?

---

### Post by robfindlay on 2008-01-29
This is in Gutsy with the standard version of GIMP that comes with Gutsy.

---

### Post by robfindlay on 2008-01-29
Bump -- help?

---

### Post by rax_m on 2008-01-30
I haven''t tried this, but could you use the Gimp to scale the image to 4x6 inches and then try printin? 

On my version of gimp (the standard one with Gutsy), under the image window I have File-> Print with Gutenprint. Do you not have this ?

---

### Post by rjs987 on 2008-04-11
I was also having this problem, unable to get rid of the border. I am using digiKam and print to a HP Photosmart c6280 all-in-one with a dedicated 4x6 photo paper tray. I run this using HPLIP 2.8.4 (just upgraded). After much forum searching and configuration settings searching I finally found the setting in the printer properties (driver tab) where I could set the resolution to a setting that included FULL BLEED as part of the description. I also set the margins to zero, and the position to centered, but I really believe the resolution setting set to any FULL BLEED choice is the key and the other settings may not matter after that. I like the Image Print Wizard in digiKam for the auto crop feature that lets ME decide what part of the photo to crop if it doesn't all fit inside the 4x6 aspect (unlike windows that decides for you).

---

### Post by jedimasterk on 2008-04-15
Seems like Linux in general pretty much sucks when it comes to photography and printing. No wonder professional photographers havn't embraced Linux as much as Windows or Mac OSX. My thoughts.

---

### Post by jedimasterk on 2008-04-15
No native Photohop support!. Forget wine!. To complicated to set up for novices. What about Lightroom, or Illustrator. Are they supported?. Linux is only good if you want to show off your pictures on your computer or internet. That's all!.

---

### Post by smartboyathome on 2008-04-15
> **jedimasterk said:**
> No native Photohop support!. Forget wine!. To complicated to set up for novices. What about Lightroom, or Illustrator. Are they supported?. Linux is only good if you want to show off your pictures on your computer or internet. That's all!.

Thats because Adobe doesn't see it as valuable, it isn't Linux's fault. I find Inkscape a great vector editor/creator. Photoshop isn't everything, I get along with GIMP just fine. Unless there is a specific function you absolutely need, then you should try it with an open mind.

---

### Post by jedimasterk on 2008-04-15
I haven't found an application in Linux yet that allows you to do borderless printing with ease. and no one has been able to answer my questions about what is the best app in linux to do borderless printing. In Photoshop, Paintshop Pro, etc.. You click on a button that says "Borderless"  and you get a borderless print. No adjusting margins etc..

---

### Post by smartboyathome on 2008-04-15
> **jedimasterk said:**
> I haven't found an application in Linux yet that allows you to do borderless printing with ease. and no one has been able to answer my questions about what is the best app in linux to do borderless printing. In Photoshop, Paintshop Pro, etc.. You click on a button that says "Borderless"  and you get a borderless print. No adjusting margins etc..

Maybe that is because not many of us need that. I know I don't. The way open source works, it isn't made unless it is needed.

---

### Post by jedimasterk on 2008-04-15
So why doesn't Adobe see Linux as valuable. Especially if it is true that Linux surpassed Mac OSX in user base.

---

### Post by smartboyathome on 2008-04-15
Because Linux users who need photoshop either run it through wine/virtualbox or dualboot for it.

---

### Post by jedimasterk on 2008-04-16
Not good enough!. What if Windows or Mac users had to dualboot into Linux to do descent photo or video editing. God forbid!. Seems like a lame excuse not to natively port their apps to Linux. Probably getting paid off by MS and Apple.

---

### Post by Foster Grant on 2008-04-17
> **robfindlay said:**
> Okay so I take my pics, load them up in gimp, crop manipulate or whathave you. 

However gimp will not see my printer, so I end up trying to print with different graphics programs and none of them will print to a 4x6 without leaving HUGE borders. 

is their some "size" and proportion I should scale the image to before trying to print it?  

Am I making sense? HELP! 

-Rob

No, you're not. Sorry.

What I think you're saying is that you're trying to print pictures on 4x6 photo paper, but when you do you're shrinking the canvas size and it's still printing the whole canvas (lots of white space and a tiny picture). You just want the picture.

However, I also think you could be saying that whatever grfx programs you're using are printing with large picture frames, essentially wide black lines, and you don't want them.

Suggest you download Scribus via Synaptic. GIMP is not designed for print output. Cinepaint is worse. Never used Krita (don't use KDE).

Edit your images as per usual in GIMP, Krita or Cinepaint. Save and close.

Load Scribus (it will need some time to read your fonts), then set up a new document in the New Document dialog box as follows, *ignoring the Page Size popup menu in that dialog box*:

(NOTE: PRINT THESE INSTRUCTIONS! It's easier.)

OPTIONS SECTION (top right)
o Number of pages: 1
o Default Unit: Inches (in)

PAGE SIZE SECTION (top center) 
o Size: *Again, ignore this popup. It will change on its own.*
o Orientation: Landscape
o Width: 6 in
o Height: 4 in

MARGIN GUIDES SECTION (bottom center)
o Set all four boxes (left, right, top and bottom) to zero.
o Press the [COLOR="MediumTurquoise"]Printer Margins...[/COLOR] button. Make sure your inkjet printer is selected on the Select Printer popup. Set all Minimum Margins to '0 in.'

AUTOMATIC TEXT FRAMES (lower right)
You don't want one. Make sure the check box at the top of this box is deselected.

Press [COLOR="MediumTurquoise"]OK.[/COLOR]

Go to the Page menu and make sure Snap To Guides is selected. If it's not, choose it on the menu.

Go to the Insert menu and select the second item, 'Image Frame.' The cursor will change to show that it's ready to draw a picture frame. Point to the upper left corner of your document (white box), click and drag to the lower right corner. Release. Now you have a picture frame.

If the floating Properties palette is not showing by default, press F2 to display it. Make sure the chain icon-button at the right of the measurements is broken. If it is unbroken, click it to break it. (Very important, saves annoyance and confusion in the next step.)

On the [COLOR="MediumTurquoise"]X, Y, Z[/COLOR] tab, set X- and Y-position to 0 in, width to 6 in and height to 4 in. This makes sure your box is where it should be and is the proper size. Now click the lock icon 

Save this document now (name of your choice) in your home directory.

Select the picture frame. Hit <Ctrl>-D (the [COLOR="MediumTurquoise"]Get Picture[/COLOR] command. In the ensuing dialog box, navigate to the picture you want and press OK. Assuming you sized it in your image editor, it should come in at the right size and location. If it it comes in seriously blown up, go to the Image tab in the Properties menu, make sure the chain icons are selected and adjust either the X- or Y-scales (with the chains turned on, adjusting one adjusts the other).

When it fits, print it. In the print dialog box, look at the upper right popup menu under the Options tab (NOT the Advanced Options), and select 'Print In Colour If Available.' Press the 'Print' button at the bottom of the dialog box.

Should work. :)

---

### Post by jedimasterk on 2008-05-09
Seems like a pain in the you know what to me, having to go through all that. Rather than selecting 4X6 clicking a key that says borderless, click print and wholla a borderless 4X6 print, like you can do in Photoshop or Photoshop Elements. I tried doing a 8.5 X 11 borderless print with Gimp and gutenprint today to frame. But when I went to print, clicking borderless option and all. I still got a white margin that I had to use a paper cutter to. I can't be using a paper cutter on borders to all my images. I need the borderless option working properly.

---

### Post by mgmiller on 2008-05-11
I print borderless 4x6 images all the time.  I use Picasa for Linux to crop the images with the 4x6 aspect ratio.  You can also use gthumb to do the same thing.  I also defined several different printer drivers.  I have a 4x6 printer driver that is just doing 4x6 borderless prints, then when I'm ready to print, I select that one and it works perfectly every time.

---

### Post by jedimasterk on 2008-05-11
> **mgmiller said:**
> I print borderless 4x6 images all the time.  I use Picasa for Linux to crop the images with the 4x6 aspect ratio.  You can also use gthumb to do the same thing.  I also defined several different printer drivers.  I have a 4x6 printer driver that is just doing 4x6 borderless prints, then when I'm ready to print, I select that one and it works perfectly every time.

Ok what do you do in Picassa for Linux if your image is already cropped the way you want it. In Photoshop/Photoshop Elements you don't need to crop anything. Borderless options just work right out of the box!!.

---

### Post by jedimasterk on 2008-05-11
> **mgmiller said:**
> I print borderless 4x6 images all the time.  I use Picasa for Linux to crop the images with the 4x6 aspect ratio.  You can also use gthumb to do the same thing.  I also defined several different printer drivers.  I have a 4x6 printer driver that is just doing 4x6 borderless prints, then when I'm ready to print, I select that one and it works perfectly every time.


I tried gThumb. And even with borderless option clicked, 4X6 chosen, landscape, etc. I still got a border on each end of my Photo. Even using Epson 4X6 (tear off borders) option. It don't work!!. Also doing an 8X11 size, still get a border.

---

### Post by jedimasterk on 2008-05-11
Check this guys experience with Video Editing and Linux.
[http://www.progbox.co.uk/wordpress/?p=540](http://www.progbox.co.uk/wordpress/?p=540)

Comparied to MacOSX and Windows XP apps, video editing and photo editing applications in Linux just plain suck!!. No wonder the majority of professional photographers or video editing shops never consider Linux as an option to Windows XP or MacOSX for their professional work. Linux is only needed for server farms and virtualization. Never the desktop and the open source apps!. If Linux is to succeed on the desktop this needs to be remedied, and not in 20 years or so, but now!. Just my thoughts!.

---

### Post by mgmiller on 2008-05-12
> I still got a border on each end of my Photo.

This happens when you don't crop the photo to a 4x6 aspect ratio first.  I just tried it and I can reproduce the white border on each side by just trying to print to the 4x6 paper without first doing the crop.

This also holds true for 5x7 and 8x10.  You must crop the image to the right aspect ratio first, or you won't get a borderless print.

If you are doing the crop in gthumb, after establishing how you want to crop the image, you must click the crop button in the upper left corner of the window.  If you just hit apply or save, it won't work.

If you are doing the crop in Picasa, it's more intuitive.

Frankly, I use Picasa for almost all my photo manipulation and printing.  It works great and makes finding things very easy.  If I need to do something really interesting to a picture I use gimp first, then reopen it in picasa to do the final tweaks and to print.

I have framed photos hanging all over my house and print borderless 4x6 for family and friends.  I make 11x14 masked to 8x10 framed pictures as gifts.  I have no problems doing all of this in linux.  

Back when I used to use Win XP, I had a lot of issues trying to get reliable borderless prints where I knew exactly what would be on the image.  XP seems to do the aspect ratio change automatically, but you can't predict where it is going to be on the image.  I find doing it in linux gives me more control over the final print.

---

### Post by jedimasterk on 2008-05-12
> **mgmiller said:**
> This happens when you don't crop the photo to a 4x6 aspect ratio first.  I just tried it and I can reproduce the white border on each side by just trying to print to the 4x6 paper without first doing the crop.

This also holds true for 5x7 and 8x10.  You must crop the image to the right aspect ratio first, or you won't get a borderless print.

If you are doing the crop in gthumb, after establishing how you want to crop the image, you must click the crop button in the upper left corner of the window.  If you just hit apply or save, it won't work.

If you are doing the crop in Picasa, it's more intuitive.

Frankly, I use Picasa for almost all my photo manipulation and printing.  It works great and makes finding things very easy.  If I need to do something really interesting to a picture I use gimp first, then reopen it in picasa to do the final tweaks and to print.

I have framed photos hanging all over my house and print borderless 4x6 for family and friends.  I make 11x14 masked to 8x10 framed pictures as gifts.  I have no problems doing all of this in linux.  

Back when I used to use Win XP, I had a lot of issues trying to get reliable borderless prints where I knew exactly what would be on the image.  XP seems to do the aspect ratio change automatically, but you can't predict where it is going to be on the image.  I find doing it in linux gives me more control over the final print.


But for the majority of us. We don't have the time to be adjusting aspect ratios etc.. It should be done automatically. You know how much ink I go through just to get a proper borderless print, making all kinds of adjustments. It's way to expensive. In Photoshop Elements, or Paintshop Pro, in Windows you don't go through all that hassle.

---

### Post by mgmiller on 2008-05-12
> But for the majority of us. We don't have the time to be adjusting aspect ratios etc.. It should be done automatically. You know how much ink I go through just to get a proper borderless print, making all kinds of adjustments. It's way to expensive. In Photoshop Elements, or Paintshop Pro, in Windows you don't go through all that hassle.

That is exactly the point.  Once you know what you are doing, you don't waste anything.  You should not be doing test prints to see what the borders are.  They show up on screen before you print.

In Windows, I never really knew what I would get, or the tops of heads would be cut off.  It was borderless, though.  It was doing an automatic crop that you have no control over.

What you are really doing is cropping the print to fit the aspect ratio of the paper you are going to print on.

Cropping is a basic part of photography.

If you are not cropping your photos, you're not getting the full benefit of a digital (or chemical) darkroom.  I would never dream of just printing what I took without doing something to it.  I was a serious photo hobbiest as far back as the 1960's.  I even worked for a professional photographer, doing his black and white enlargements and had an old school chemical darkroom in my home. Everything Gets Cropped!  Doing the crop in Picasa is trivial and takes no more than a few seconds.  It also changes the whole look of the final print.  Cropping is one of the easiest and most important things you can do to a picture.

What you are getting is windows is an uncontrollable borderless print.  Of course, now that I'm familiar with Picasa, I could also get repeatable good results in Windows also, but why bother.

What I am getting in linux is exactly what I want, every time, with no waste.

---

### Post by jedimasterk on 2008-05-13
> **mgmiller said:**
> That is exactly the point.  Once you know what you are doing, you don't waste anything.  You should not be doing test prints to see what the borders are.  They show up on screen before you print.

In Windows, I never really knew what I would get, or the tops of heads would be cut off.  It was borderless, though.  It was doing an automatic crop that you have no control over.

What you are really doing is cropping the print to fit the aspect ratio of the paper you are going to print on.

Cropping is a basic part of photography.

If you are not cropping your photos, you're not getting the full benefit of a digital (or chemical) darkroom.  I would never dream of just printing what I took without doing something to it.  I was a serious photo hobbiest as far back as the 1960's.  I even worked for a professional photographer, doing his black and white enlargements and had an old school chemical darkroom in my home. Everything Gets Cropped!  Doing the crop in Picasa is trivial and takes no more than a few seconds.  It also changes the whole look of the final print.  Cropping is one of the easiest and most important things you can do to a picture.

What you are getting is windows is an uncontrollable borderless print.  Of course, now that I'm familiar with Picasa, I could also get repeatable good results in Windows also, but why bother.

What I am getting in linux is exactly what I want, every time, with no waste.


So if I edit in Gimp I need to wait till I do my final editing and then open up Picassa to crop my saved image so I can get a reasonable print. People usually crop their image first then procede to edit after then print. Seems like a wacky workflow to me. I'll stick with Photoshop/Elements and Windows for now for my photo editing needs. Linux in my estimation is still way behind the eight ball. Sorry but that's how I feel based on my experience with Linux and photography. Until Photoshop is ported, if ever, to Linux. Photography and Linux will never be a good match!. Except to store your photos on a server. Especially for professional photography!.

---

### Post by mgmiller on 2008-05-13
> People usually crop their image first then procede to edit after then print.

There is no reason you can't do it that way.  Once it's cropped, it should print fine.  Besides, if you are cropping properly, you should not be having problems with borderless prints.

I only use gimp on a handful of photos.  Most of what I need to do I can do within Picasa.  One stop for most of my tweaks, cropping and printing.

The native linux app, f-spot can also do these things, but I like Picasa better.

For that matter, gthumb can also do most of the things that are needed for the majority of photos to look good.  Red eye removal, cropping, fixing brightness and contrast, etc.  No reason to switch apps.

You seem determined to want to use windows.  More power to you.  I waste more time administering the windows computers on my work network than I care to think about.  I am always worried about viruses and other malware (although with careful computing I haven't been hit in a while "that I know of").  The linux boxes on my office network "just work".  I never worry about them.  

Everything you want to do with digital photography can be done easily in a Linux environment.  I have been doing it for years, you just seem not to want to learn. ](*,)

Linux is not Windows.  Things are done differently.  Not necessarily better or worse, just differently.  Until you get used to that, you will never get anywhere.

---

### Post by jedimasterk on 2008-05-13
> **mgmiller said:**
> There is no reason you can't do it that way.  Once it's cropped, it should print fine.  Besides, if you are cropping properly, you should not be having problems with borderless prints.

I only use gimp on a handful of photos.  Most of what I need to do I can do within Picasa.  One stop for most of my tweaks, cropping and printing.

The native linux app, f-spot can also do these things, but I like Picasa better.

For that matter, gthumb can also do most of the things that are needed for the majority of photos to look good.  Red eye removal, cropping, fixing brightness and contrast, etc.  No reason to switch apps.

You seem determined to want to use windows.  More power to you.  I waste more time administering the windows computers on my work network than I care to think about.  I am always worried about viruses and other malware (although with careful computing I haven't been hit in a while "that I know of").  The linux boxes on my office network "just work".  I never worry about them.  

Everything you want to do with digital photography can be done easily in a Linux environment.  I have been doing it for years, you just seem not to want to learn. ](*,)

Linux is not Windows.  Things are done differently.  Not necessarily better or worse, just differently.  Until you get used to that, you will never get anywhere.

Your wrong. I am determined to use Linux more, since I enjoy the Linux/Opensource philosophy. I do use Linux (Ubuntu) more on my DualBoot system then Windows. But as for the apps I am mainly using now, Linux can't compete with either Windows or Mac OSX. I want to learn astro-photography,and maybe do some professional landscape photography to try to earn some extra money. Their are no descent astro-photgraphy apps for Linux, or professional photography apps like Photoshop CS3 or Lightroom. Both give me way more tools for landscape photography over Gimp. Considering all the actions and plugins you can get for Photoshop. Also Gimp has very limited 16/32 bit support and the interface is horrible by todays standards. Also in astro-photography 16/32 bit support is essential. According to allot of the professional photographers I have read about or talked to, Photoshop is the standard. Not many have even heard of or use the Gimp. And those that have heard of it, consider it an amateur photographers tool, not a professionals tool. So my gripe apart from bad photographic printing, is no real good highend apps in Linux for photography or astro-photography. The top companies like Canonical and Novell, should try to push the issue of getting Adobe's Creative suite ported to Linux natively. Not like Google using Wine!. If it can be ported to Mac OSX than it can surely be ported to Linux!. We need good highend photography app developers for Linux. Who really know what they are doing. And I mean highend for professional photographers, who earn a living with their photographs!.

---

### Post by jedimasterk on 2008-05-13
Read this article and you will see what I mean!.

[http://lxer.com/module/newswire/view/91180/index.html](http://lxer.com/module/newswire/view/91180/index.html)

---

### Post by mgmiller on 2008-05-13
You have just totally changed the subject of your original post.  You wanted to create borderless 4x6 prints in Linux and had problems.  I believe I pointed out how to do that.

Your last post is about using Linux for professional photographic work.  

The vast majority of users will have all they need with the tools provided by the typical Linux distribution.

Sadly, when you want to take it to the professional levels you are describing in your last post, there is a miserable lack of adequate software in Linux.  
In this regard, we are in total agreement.

I will now get up on my soapbox and reach for my megaphone...

I would be willing to pay for a Linux version of Quicken.  I would love to get my proprietary office management software off windows on my server.  I can't.  Some of my machines are stuck in Windows because of this.  

As regards what you are trying to do, I understand that crossover office will run some versions of photoshop, but I don't know which ones or how well it's supported.  But, that's besides the point.  
**We need to have these major applications ported to run natively in Linux! **
Or at the very least have decent alternatives written by people in our own community. 
(Please excuse my use of bold font here, but I feel pretty strongly about this.)

Now I will get down off my soapbox...

I think there are many of us that would pay for the Linux versions of major commercial apps if they were available.

The number of people using Linux is increasing rapidly.  I hope that it will reach a "tipping point" where the commercial software vendors decide the market is big enough to start supporting us.

The bottom line for me is for normal home use, Linux is great, but for certain types of high end professional use, Windows is better, if only because that's were the software is.

---

### Post by mgmiller on 2008-05-13
> **jedimasterk said:**
> Read this article and you will see what I mean!.

[http://lxer.com/module/newswire/view/91180/index.html](http://lxer.com/module/newswire/view/91180/index.html)

Yes, I read it.  The author did not try the easiest and best ways to do it.  She did not try gthumb, which will do all the normal quick things most people need.  Or Picasa, which does a whole lot more.  Combined with the multiple printer drivers for different paper sizes, it works perfectly.  The first person to respond at the bottom of the page who discusses turboprint, got it exactly right.

---

### Post by jedimasterk on 2008-05-17
[IMG][[IMG]http://img528.imageshack.us/img528/5245/img0601nv8.jpg[/IMG]](http://imageshack.us) [[IMG]http://img528.imageshack.us/img528/5245/img0601nv8.1a6ad38a56.jpg[/IMG]](http://g.imageshack.us/g.php?h=528&i=img0601nv8.jpg)[/IMG]

This is what I get trying to printout a borderless print with Linux(Ubuntu Hardy). All settings set with Epson R340, and borderless enabled. Aspect ratio was set for 4X6. As you can see I am still getting borders around print. This was actually F_Spot, with 4X6 postcard and cropped to get 4X6 ratio. Still doesn't work!. Same results with gutenprint etc..

---

### Post by mgmiller on 2008-05-17
I won't bother to show you any of my pics, suffice to say they are perfect borderless 4x6 every time.  I am now wondering which printer driver you are using.  I have a Canon i960 printer and use the turboprint drivers.  I just looked and they include your model epson printer in the package.  It was the only way I could get my i960 to work, but it is a beautiful solution and not very expensive.  You get a ton of drivers and can do free updates whenever they come out.  You can also download and try the driver first before paying for it to see if it works for you.

[http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")

---

