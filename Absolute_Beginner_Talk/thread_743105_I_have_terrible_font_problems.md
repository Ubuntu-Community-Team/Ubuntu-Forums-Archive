---
title: "I have terrible font problems"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by mamadu bwana on 2008-04-02
Hi,

I have just installed Ubuntu 7.10 on my computer and the fonts look absolutely terrible: they look blurred, some of them look almost transparent (in the terminal, for example). Here is what I have:

A Samsung SyncMaster 770 TFT

Graphics card: ATI Radeon 7000/Radeon VE
driver: XFree86 v4 Server Module: radeon
XFree86 v4 Server Module: radeon
3D Support: yes
Color Depths: 16
Extensions:

etc/fonts/conf.avail has the following files:

10-autohint.conf 30-amt-aliases.conf 65-nonlatin.conf
10-no-sub-pixel.conf 30-urw-aliases.conf 65-ttf-thai-tlwg.conf
10-sub-pixel-bgr.conf 40-generic.conf 69-unifont.conf
10-sub-pixel-rgb.conf 49-sansserif.conf 70-no-bitmaps.conf
10-sub-pixel-vbgr.conf 50-user.conf 70-yes-bitmaps.conf
10-sub-pixel-vrgb.conf 51-local.conf 80-delicious.conf
10-unhinted.conf 52-languageselector.conf 90-synthetic.conf
20-fix-globaladvance.conf 53-monospace-lcd-filter.conf
20-lohit-gujarati.conf 60-latin.conf
20-unhint-small-vera.conf 65-fonts-persian.conf


I have tried all sorts of combinations under System->Preferences->Appearance->Fonts but I only succeeded in making things worse.

I should probably add here that I did not have this issue in the past with the same hardware, but I had a hard disk crash and I needed to reinstall everything. Ever since the fonts are *horrible*.

Please help me out here!

Many thanks,

Mamadu

---

### Post by philinux on 2008-04-02
Go into appearance fonts. 

Select LCD smoothing then click details and select hinting-slight.

---

### Post by mamadu bwana on 2008-04-02
I did and that did nothing to resolve the problem: the fonts still look like something seen through a fog...

The least bad looking fonts are DejaVu Sans Mono Book, and even they are not fantastic, the rest just look terrible.

Any other ideas or suggestions?!

---

### Post by philinux on 2008-04-02
Sounds more like a graphics driver problem then.

---

### Post by perce on 2008-04-02
From your description it looks like you have a wrong resolution. Go to 
system > preferences > screen resolution and check if you are using the best resolution for your display. If you don't, se if you have it among the options. If you have it, you're lucky: chose it. If you don't see the correct resolution among the options, open a terminal and type:

sudo dpkg-reconfigure -phigh xorg

to reconfigure the X server

---

### Post by mamadu bwana on 2008-04-02
My monitor (Samsung SyncMaster 770 TFT) provides a maximum density of 1,280 x 1,024 dpi and a 75 Hz refresh rate but when I  go to 'screen resolution' I only can get a refresh rate of 60Hz with no other option offered.  Can I modify this and, if yes, how do I do that?

Thanks!

---

### Post by Therion on 2008-04-02
> **mamadu bwana said:**
> ... I only can get a refresh rate of 60Hz with no other option offered. 
LCD monitors don't refresh like CRT's do -- they have response times -- so changing this setting will have no effect on how your fonts display.

Posting up a screen shot of what your fonts look like might help troubleshoot the issue better.

---

### Post by mamadu bwana on 2008-04-02
> **Therion said:**
> 
Posting up a screen shot of what your fonts look like might help troubleshoot the issue better.

Ok. see attached file.

Can you see what is going on in this pic? (try zooming in to see better)

---

### Post by Therion on 2008-04-02
> **mamadu bwana said:**
> Can you see what is going on in this pic? (try zooming in to see better)
Roger that...  Looks like you need to change your Application or Desktop font (can't remember which one it is but I'm pretty sure it's one or the other).  Can't tell you what font that is in particular - assuming you mean that hideous font being used on your FF tabs, toolbars, etc. - but yeah, I wouldn't care for that either.

Have you gone to System/Appearance/Fonts and tried changing the application font to something like the default **Sans** font?  Your font selection looks good IN Firefox (e.g. your post, my post, etc.) but the toolbars, tabs, etc. all seem to be using a different (monospaced?) font.  I'd just try changing that one font in particular to something more attractive.  Try something like this, maybe (although I prefer to use Subpixel Smoothing (this is just a generic pic I found via Google Image Search, but it gets the point across)):

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/FontPreferencesNew.png[/IMG]

---

### Post by mamadu bwana on 2008-04-02
I am already using mostly "Sans" fonts (see my post #3 above) and they do indeed look less terrible than the rest.  But if you look closer you will see that they also have the "fudged edges" (if my pics is not good enough for you to see take a look at the higher res I attached to this post).

Could it be that for whatever reason I have the wrong driver for my card/monitor or that it is poorly configured?  Or that I do not have the correct fonts downloaded to my /etc/fonts subdirectory?!

---

### Post by Therion on 2008-04-02
I think what you're seeing is how poorly Firefox handles font rendering and is a common complaint.  You call them "fudged"; by that you mean the fonts look blurry, correct?  Because, yes, they do, and I don't know how to fix it.  

Long story short, I think those fonts are about as good as it's going to get in Firefox under Ubuntu.  I bet your fonts look much better other applications though?  I know my fonts look sharper in, say, Open Office applications, than they do in Firefox.

---

### Post by philinux on 2008-04-02
This is how it looks on my screen.

I'm using the subpixel smoothing and hinting slight.

Satisfied customer here.

---

### Post by Therion on 2008-04-02
> **philinux said:**
> This is how it looks on my screen.
Looks nice.  I do notice you're using FF 3.0-b4 under Hardy. 
Maybe the whole font-rendering thing has been addressed at some level, then, in this release of 'Fox?

---

### Post by philinux on 2008-04-02
> **Therion said:**
> Looks nice.  I do notice you're using FF 3.0-b4 under Hardy. 
Maybe the whole font-rendering thing has been addressed at some level, then, in this release of 'Fox?

No real diff from FF2.

FF3 Beta5 has been released so anytime soon it should hit the hardy repos.

It faster than FF2 thats a fact.

---

### Post by Therion on 2008-04-02
> **philinux said:**
> It faster than FF2 thats a fact.
Toyed with HH (64-bit) in alpha-6 flavor, and yeah...  I remember FF being *screamin'*  fast.

Still, I swear your fonts look better in your screenie than mine do now under FF 2.?.??? and Gutsy.  Or... I could just be losing it.

---

### Post by philinux on 2008-04-02
> **Therion said:**
> Toyed with HH (64-bit) in alpha-6 flavor, and yeah...  I remember FF being *screamin'*  fast.

Still, I swear your fonts look better in your screenie than mine do now under FF 2.?.??? and Gutsy.  Or... I could just be losing it.

Hard to compare now :)

I may have posted a screenshot under gutsy with FF2 recently. In any case I had hinting off then .

---

### Post by mamadu bwana on 2008-04-02
Glad you mentioned other applications.  Look at the attached pic how terrible an Open Office window looks.  That stuff affects my entire system, which is why I am wondering about cards, drivers and settings...

What do you think?  The fonts in OO look as blurry/fudged as can be, no?

(heeeeeeeeeeeeeelp!!)

---

### Post by perce on 2008-04-02
I'm still of the opinion that you're using a wrong resolution. Have you tried other resolutions?

---

### Post by Average Joe on 2008-04-02
You could try:
```
sudo dpkg-reconfigure fontconfig-config
```
and choose Autohinter, Automatic, No.

Or try another configuration in there. You probably have to logout, and log back in again for the changes to have effect.

It has helped my font rendering in the past.

---

### Post by Therion on 2008-04-02
Maybe this will help:  [Comprehensive Ubuntu Font Configuration Guide]("http://www.ubuntutips.net/node/35").

It's comprehensive!

Also [possibly interesting](http://brainstorm.ubuntu.com/idea/96/) or helpful???  See Richard Neill's post in particular.

---

### Post by bn127 on 2008-04-02
Hi,

I use to change the Ubuntu and FF themes quite often and found out that some of the themes produce better fonts than others. Probably this won't solve your problem but try to change themes anyway.

Regards.

---

### Post by mamadu bwana on 2008-04-03
> **Therion said:**
> Maybe this will help:  [Comprehensive Ubuntu Font Configuration Guide]("http://www.ubuntutips.net/node/35").

It's comprehensive!

Also [possibly interesting](http://brainstorm.ubuntu.com/idea/96/) or helpful???  See Richard Neill's post in particular.

Thanks for all your help!  I will read up on all this.

Cheers,

Mamadu

---

