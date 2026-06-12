---
title: "Bad quality ubuntu backgrounds"
date: 2005-03-19
forum: Art &amp; Design
---

### Post by basse1989 on 2005-03-19
Why aren't all of the official ubuntu background high quality pictures?
All 2 of them (or 4 is you count the widescreen versions) have been bad quality pictures, and that isn't something you expect of a high quality distrubution as ubuntu.

When I say bad quality I don't mean a bad piece of art, what I mean is that the png pictures that the ubuntu backgrounds are looks like jpeg pictures...

---

### Post by bored2k on 2005-03-19
[QUOTE=basse1989]Why aren't all of the official ubuntu background high quality pictures?
All 2 of them (or 4 is you count the widescreen versions) have been bad quality pictures, and that isn't something you expect of a high quality distrubution as ubuntu.

When I say bad quality I don't mean a bad piece of art, what I mean is that the png pictures that the ubuntu backgrounds are looks like jpeg pictures...[/QUOTE]
 Hey dude ubuntu sparkle wallpapers are pretty wicked and I can see no sign of bad quality here ... but then again, you may work at Pixar and like high quality stuff ;) . I still change them so I dont really care.

---

### Post by basse1989 on 2005-03-19
Ehh? Don't you see the stripes were the light brown shades to dark brown?
That is something I call really bad quality.

---

### Post by bored2k on 2005-03-19
[QUOTE=basse1989]Ehh? Don't you see the stripes were the light brown shades to dark brown?
That is something I call really bad quality.[/QUOTE]
 Dont see them but, since theyre so bad, you can contribute and make an awsome wallpaper with no errors on it .



[SIZE=1]I'm the sarcasm mac daddy :D .[/SIZE]

---

### Post by Spark* on 2005-03-19
It sounds like you have some color depth issues.

---

### Post by bored2k on 2005-03-19
[QUOTE=Spark*]It sounds like you have some color depth issues.[/QUOTE]
 Probably running on 16bits
We 24bits really see no erros. Unless he's that psycho from CSI and have a microscope in front of his monitor.

---

### Post by kassetra on 2005-03-19
[QUOTE=basse1989]Ehh? Don't you see the stripes were the light brown shades to dark brown?
That is something I call really bad quality.[/QUOTE]

The Ubuntu wallpapers are extremely high quality - IF the color depth of your X server configuration is correct.

If you have a low color depth in your X-server configuration, absolutely NOTHING, and I mean NOTHING that has "photographic quality" is going to look good, because it's going to shove all of those millions of colors down into about a thousand or less - and you will get color "banding."

So it's not the quality of the artwork in Ubuntu - it's your X server configuration.

---

### Post by bored2k on 2005-03-19
[QUOTE=kassetra]The Ubuntu wallpapers are extremely high quality - IF the color depth of your X server configuration is correct.

If you have a low color depth in your X-server configuration, absolutely NOTHING, and I mean NOTHING that has "photographic quality" is going to look good, because it's going to shove all of those millions of colors down into about a thousand or less - and you will get color "banding."

So it's not the quality of the artwork in Ubuntu - it's your X server configuration.[/QUOTE]
 There you have it basse1989. You got owned by a graphic designer, how sick is that !
[img]http://www.woodturnedcreations.com/Dud3!/pix/misc/owned-wall%20tape.jpg[/img] :-P

---

### Post by basse1989 on 2005-03-19
Proof of 24bits mode:

```
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
```

---

### Post by TravisNewman on 2005-03-19
Same here (only I run nvidia, not fglrx), and just recently I've been noticing some banding going on! Not just the Ubuntu wallpapers, but other images that I know shouldn't be banding.

---

### Post by basse1989 on 2005-03-19
A friend of mine can also see the stripes. We both have tft screens so I guess that makes it easier to see them. But I saw them on my old crt screen too.

---

### Post by Buffalo Soldier on 2005-03-19
Running on 16bits depth. But I experience no *banding* / distortion of image. Both OK in Hoary and Warty.

EDIT:

Experiment: It was after I change to 8bits (256 color I guess) that I experience the *banding*. Perhaps the problem is more related to the type of graphic card?

---

### Post by basse1989 on 2005-03-19
Graphic card? I don't think so... well the friend I talked about has a nvidia card, as you know I've got an ati card and we've got the same stripes.

---

### Post by Buffalo Soldier on 2005-03-19
Really scratching my head here. Wish I could help you more.

**Edit: **

is it only in the ubuntu background image that you notice this stripes/banding? Try viewing other 16/24 bits image that use gradients (such as sky during sunset, beach)?

If you notice the same deffect in all high-depth images, then the problem is not with ubuntu desktop image.

---

### Post by basse1989 on 2005-03-19
I tried "No wallpaper" and different gradients. All colors looks good, except some for exaple the two colors used by the new ubuntu background.
Seems different colors gives different results.

---

### Post by bored2k on 2005-03-19
[QUOTE=basse1989]I tried "No wallpaper" and different gradients. All colors looks good, except some for exaple the two colors used by the new ubuntu background.
Seems different colors gives different results.[/QUOTE]
 Try wallpapers @ deviantart, they mostly funky colorish, do you see problems there?

-and btw If i did I didnt mean to offend on the "owned" thingy :P-

---

### Post by basse1989 on 2005-03-19
Don't worry, be happy. :P
No actually, I didn't take that seriously.
And hey, I wasn't owned. :)

Unrelated: So you like my new (and first (and "homemade")) avatar?

---

### Post by bored2k on 2005-03-19
[QUOTE=basse1989]Don't worry, be happy. :P
No actually, I didn't take that seriously.
And hey, I wasn't owned. :)

Unrelated: So you like my new (and first (and "homemade")) avatar?[/QUOTE]
 Awwwwsome !!! For some reason it reminded me Mario 1 NES Level 1-1 BGM :d [excuse the geek factor, under medication ;)]
[img]http://img211.exs.cx/img211/4206/supermariobroscart0rl.jpg[/img] <--- now that's Gangsta!

---

### Post by basse1989 on 2005-03-20
> **bored2k]Awwwwsome !!! For some reason it reminded me Mario 1 NES Level 1-1 BGM :d [excuse the geek factor, under medication  said:**
> 
Hehe, it reminds you of such a good game huh? Then it has to be a good avatar too. :)

Well, does anyone know anything about the color "problem"? If I get stripes and you don't, even tough all of us are running 24 bits, and Buffalo Soldier who runs 16 bits but can't see any stripes. Why do I see the stripes? Is it cuz you guys are blind or using some 10 year old crt screen?

---

### Post by cdhotfire on 2005-03-20
> There you have it basse1989. You got owned by a graphic designer, how sick is that !
[img]http://www.woodturnedcreations.com/Dud3!/pix/misc/owned-wall%20tape.jpg[/img]
this is a keeper.  8-)

edit: Darn man stop talking mario, now im gonna have to play it again.  That game is 2 great, but then again they do call it a classic. 
*Turns on his Nintendo*
*ding ding ding, ding ding diding, diding diding diding diding dididing*

---

### Post by bored2k on 2005-03-20
[QUOTE=cdhotfire]this is a keeper.  8-)[/QUOTE]
 See there hotfire, I was gonna write just "lol", but you made me feel guilty and now I have to fill this msg up ROFL .

[img]http://www.9622.net/images/lol-gorilla.jpg[/img]

---

### Post by cdhotfire on 2005-03-20
that right there is another keeper, jesus, where do you get these great pics. Also read my edit on the last post.

---

### Post by basse1989 on 2005-03-20
What is this lol thing all about?

---

### Post by cdhotfire on 2005-03-20
[http://www.ubuntuforums.org/showthread.php?t=21019&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=21019&page=2&pp=10)

old feud. :twisted:

---

### Post by bored2k on 2005-03-20
[QUOTE=cdhotfire]this is a keeper.  8-)

edit: Darn man stop talking mario, now im gonna have to play it again.  That game is 2 great, but then again they do call it a classic. 
*Turns on his Nintendo*
*ding ding ding, ding ding diding, diding diding diding diding dididing*[/QUOTE]
 Lol that game is a click away ;) [P2P] ... I still have the original cartridge next to my monitor ^_^ . Mario was even hotter than Gates pretending to be a model for Victoria Secret ;) .

---

### Post by cdhotfire on 2005-03-20
> **bored2k]Lol that game is a click away  said:**
>  ... I still have the original cartridge next to my monitor ^_^ . Mario was even hotter than Gates pretending to be a model for Victoria Secret ;) .

lol

---

### Post by cobbk2001 on 2005-03-20
[QUOTE=cdhotfire]lol[/QUOTE]
 Hello, I am pretty much a noob to linux, and am having the banding also. I tried loading a Ubuntu screenshot into another laptop, there is 'minor' banding at 24 bit, but the level of banding I have matches the 16 bit setting. I tried one 'howto' and was going to edit a file, but it already had the default depth set to 24?

Toshiba Tecra 8000 laptop - Video = Neo Magic nm 2200.

---

### Post by kassetra on 2005-03-21
[QUOTE=basse1989]Well, does anyone know anything about the color "problem"? If I get stripes and you don't, even tough all of us are running 24 bits, and Buffalo Soldier who runs 16 bits but can't see any stripes. Why do I see the stripes? Is it cuz you guys are blind or using some 10 year old crt screen?[/QUOTE]

The ATI Linux drivers have been plagued by extremely poor performance for XFree86; [font=verdana, arial, helvetica][size=2]ATI has released drivers specifically for xorg 6.8 that are supposed to be much better[/size][/font]

Once X gets a hold of the screen, the text mode console becomes corrupted and the display fails to sync to it. It also had what appears to be a nasty color depth problem; gradient images would display banding, even when the server claimed it was running in 24bpp. 

Up to now it is probably better to not use 3.7.0 drivers because of some screen corruption. Normally you should be able to use NoAccel to avoid this corruption.

Next Questions:
What ATI chipset/card do you have?  Some of them are more problematic than others.
Are you running Warty or Hoary?
Do you know the ATI driver version you're running?

---

### Post by Buffalo Soldier on 2005-03-21
[QUOTE=basse1989]Well, does anyone know anything about the color "problem"? If I get stripes and you don't, even tough all of us are running 24 bits, and Buffalo Soldier who runs 16 bits but can't see any stripes. Why do I see the stripes? Is it cuz you guys are blind or using some 10 year old crt screen?[/QUOTE]Aaaa now I'm blind :wink: :-P

---

### Post by basse1989 on 2005-03-21
> **Buffalo Soldier]Aaaa now I'm blind :wink: :-P[/QUOTE]
Hehe.

[QUOTE=kassetra]The ATI Linux drivers have been plagued by extremely poor performance for XFree86 said:**
> [size=2]ATI has released drivers specifically for xorg 6.8 that are supposed to be much better[/size][/font]

Once X gets a hold of the screen, the text mode console becomes corrupted and the display fails to sync to it. It also had what appears to be a nasty color depth problem; gradient images would display banding, even when the server claimed it was running in 24bpp. 

Up to now it is probably better to not use 3.7.0 drivers because of some screen corruption. Normally you should be able to use NoAccel to avoid this corruption.

Next Questions:
What ATI chipset/card do you have?  Some of them are more problematic than others.
Are you running Warty or Hoary?
Do you know the ATI driver version you're running?

I've got a Radeon 9600 using the 6.8.0-8.8.25-0ubuntu8 drivers running hoary.
ATI allways screw up when they try to make drivers (nvidia on next computer).

---

### Post by cobbk2001 on 2005-03-22
[QUOTE=kassetra]
Next Questions:
What ATI chipset/card do you have?  Some of them are more problematic than others.
Are you running Warty or Hoary?
Do you know the ATI driver version you're running?[/QUOTE]

Oops, forgot - NeoMagic NM2200
Warty
I have no idea, and don't know how to find out.

Thank you.

---

### Post by lathiat on 2005-05-05
[QUOTE=panickedthumb]Same here (only I run nvidia, not fglrx), and just recently I've been noticing some banding going on! Not just the Ubuntu wallpapers, but other images that I know shouldn't be banding.[/QUOTE]

This a problem with some LCDs (mostly laptop LCDs)

Basically you want to use 16-bit color, the problem si 24-bit gets "dithered" and ends up looking like ass.

Cheers,
Trent

---

### Post by TravisNewman on 2005-05-05
[QUOTE=lathiat]This a problem with some LCDs (mostly laptop LCDs)

Basically you want to use 16-bit color, the problem si 24-bit gets "dithered" and ends up looking like ass.

Cheers,
Trent[/QUOTE]
 I have a CRT ;)

---

### Post by graigsmith on 2005-05-05
[QUOTE=basse1989]A friend of mine can also see the stripes. We both have tft screens so I guess that makes it easier to see them. But I saw them on my old crt screen too.[/QUOTE]
 LCD screens Don't have as much color depth.  you can often see color banding on a subpar lcd screen (or even a high end lcd for that matter).   lcd screens dont always have 24-bit color range.  This is why most Pro-graphic designers still use CRT monitors.

so if your looking at a gradient on an LCD screen, you might see banding.  if you don't believe me, find a crt and hook it up to the same computer and you wont see any banding.

---

### Post by basse1989 on 2005-05-05
I'm sorry to let you guys down but my tft screen are working perfectly. I checked, or rather a friend checked, very carefully that it was a 24bit before I bought it.
And I just copied the hoary background to my dads computer and it looked as ugly there, even though he has a crt screen.
So my blind firends, why don't they ship ubuntu with band-free backgrounds?

---

### Post by bored2k on 2005-05-05
[QUOTE=basse1989]I'm sorry to let you guys down but my tft screen are working perfectly. I checked, or rather a friend checked, very carefully that it was a 24bit before I bought it.
And I just copied the hoary background to my dads computer and it looked as ugly there, even though he has a crt screen.
So my blind firends, why don't they ship ubuntu with band-free backgrounds?[/QUOTE]
[CENTER] Hey this are my ubuntu wallpapers, are they in BAD quality [according to you] :-| ?
[[IMG]http://img45.echo.cx/img45/7653/wartyfinalubuntu2zh.th.png[/IMG]](http://img45.echo.cx/my.php?image=wartyfinalubuntu2zh.png)[[IMG]http://img45.echo.cx/img45/525/wartyfinalwsubuntu5qv.th.png[/IMG]](http://img45.echo.cx/my.php?image=wartyfinalwsubuntu5qv.png)
Maybe you have like a really "Pixar"-high standard or something.. :roll:[/CENTER]

---

### Post by basse1989 on 2005-05-05
It looks terrible, I really like the background but I hate the quality. :(

---

### Post by XDevHald on 2005-05-05
[QUOTE=basse1989]It looks terrible, I really like the background but I hate the quality. :([/QUOTE]

I would have to agree as well, the quality is terribly poor, but the design of the abstract affect is great :D

---

### Post by basse1989 on 2005-05-05
[QUOTE=BB]I would have to agree as well, the quality is terribly poor, but the design of the abstract affect is great :D[/QUOTE]
Wiie! An ally. :)

---

### Post by bored2k on 2005-05-05
Well, I don't want to start going in circles. We already reviewd the possibility of a bad X configuration about a month ago in this same thread. So, I will have to give in on the fact that maybe the Ubuntu wallpaper lasts so little in my screen I barely see its quality..

Wow, so i was the one owned after all ^_^
[http://ubuntuforums.org/showpost.php?p=100020&postcount=18](http://ubuntuforums.org/showpost.php?p=100020&postcount=18)

---

### Post by hazza96 on 2005-05-06
[QUOTE=BB]I would have to agree as well, the quality is terribly poor, but the design of the abstract affect is great :D[/QUOTE]
If you are looking at that image and it looks poor quality it's not the fault of the image. I just looked at them and they look pefect, no banding at all.

How about you do a screen shot and post it so we can see what you mean by poor quality. I am guessing if it is a problem with your drivers etc that it will be reflected in the screen shot.

---

### Post by mohaham on 2005-05-06
same here..i too see the banding effect..
i checked the wallpapers out on a windoze and color banding was visible ther too..

---

### Post by hazza96 on 2005-05-06
[QUOTE=mohaham]i checked the wallpapers out on a windoze and color banding was visible there too..[/QUOTE]
Same computer+graphics card+monitor?

I (and many others) don't see any banding on the same image, so it can't be the image. There has to be something else in common across all the people that do see the banding because it isn't the image.

---

### Post by basse1989 on 2005-05-06
Ok, now I've cheched on 4 computers. Mine, dads, bros and a friends. I see bandings on all of them. The quality IS poor!

---

### Post by hazza96 on 2005-05-08
[QUOTE=basse1989]Ok, now I've cheched on 4 computers. Mine, dads, bros and a friends. I see bandings on all of them. The quality IS poor![/QUOTE]
Was it the same file copied to all 4? Maybe the source file was corrupted somehow.

There are many of us that see absolutley nothing wrong with the images. I believe **you** are seeing banding but I do not believe it is due to the images that are supplied by Ubuntu. Post a screenshot to show us what you are talking about.

---

### Post by basse1989 on 2005-05-08
Here is your answer:
[QUOTE=bored2k][CENTER] Hey this are my ubuntu wallpapers, are they in BAD quality [according to you] :-| ?
[[IMG]http://img45.echo.cx/img45/7653/wartyfinalubuntu2zh.th.png[/IMG]](http://img45.echo.cx/my.php?image=wartyfinalubuntu2zh.png)[[IMG]http://img45.echo.cx/img45/525/wartyfinalwsubuntu5qv.th.png[/IMG]](http://img45.echo.cx/my.php?image=wartyfinalwsubuntu5qv.png)
Maybe you have like a really "Pixar"-high standard or something.. :roll:[/CENTER][/QUOTE]
bored2k posted these images and I think they look as bad as mine.

---

### Post by hazza96 on 2005-05-08
[QUOTE=basse1989]bored2k posted these images and I think they look as bad as mine.[/QUOTE]
Bugger me, you are right, I see what you mean now. I took a closer look at those images again, full size this time. Bottom left hand corner is where I see the worst of it. Even when I look at them reduced I know what to look for can see it now.

Dam, you have ruined those backgrounds for me. It's like a whistle your car makes when you are driving, you don't notice it until someone asks what that noise is :). I guess that doesn't matter anyway because I use one of the Breezy Badger entry's for my background.

[http://www.tux.com.au/files/Screenshot.png](http://www.tux.com.au/files/Screenshot.png)

---

### Post by basse1989 on 2005-05-08
[QUOTE=hazza96]Bugger me, you are right, I see what you mean now. I took a closer look at those images again, full size this time. Bottom left hand corner is where I see the worst of it. Even when I look at them reduced I know what to look for can see it now.

Dam, you have ruined those backgrounds for me. It's like a whistle your car makes when you are driving, you don't notice it until someone asks what that noise is :). I guess that doesn't matter anyway because I use one of the Breezy Badger entry's for my background.

[http://www.tux.com.au/files/Screenshot.png](http://www.tux.com.au/files/Screenshot.png)[/QUOTE]
Thanks for looking closer. :) And btw thet breezy background also has bandings, if you look closer in the down right corner... no I'm just kidding. :D

---

### Post by SKLP on 2005-05-13
Personally, I don't really like the hoary default background (or the new calendar... ugh), but I'd like to point out that I've seen the "banding" on a maybe 1996 dated CRT monitor, and I see the ugly quality VERY CLEARLY on my new LCD monitor.
I also want to point out that the quality of the old ubuntu default background (and all the calendars) also had this bad quality thing.
I don't mean to whine, maybe this is just b/c the color spectrum isn't big enough to show a smooth  transition over this many pixels with only different shades of brown...

Well, this is not really a problem as I can just use another background but i wanted to point out that I too see this horrible quality..

---

### Post by Paul Sinnett on 2005-05-14
[QUOTE=SKLP]I don't mean to whine, maybe this is just b/c the color spectrum isn't big enough to show a smooth  transition over this many pixels with only different shades of brown...

Well, this is not really a problem as I can just use another background but i wanted to point out that I too see this horrible quality..[/QUOTE]

The problem is a combination of the choice of colours and the algorithm used by the artist's paint package to create the gradient. For those who have yet to see the problem, you can create an exaggerated version if you choose a background gradient with the colours #400000 and #002020. This should create an obvious impression of stripes rather than a smooth fade. If you take a close look at the image in Gimp you can see that instead of fading gradually from one colour into the next it jumps regularly to maintain the hue fade. However, even fading without changing hue can create visible stripes if the start and end colours are not sufficiently different. The only way to correct this is with diffusion. The desktop gradient feature doesn't support this, but it is still possible to create background images that avoid this problem.

---

### Post by Jesus Franco on 2005-05-14
Okay I've had it with people talking crap about ubuntu and such. Ubuntu is the FU(K|NG BEST!!!! And everything that is included with it is aswell OKAY!!!

Stop talking crap about it and fix it if you have such a terrible problem with it. Its just a wallpaper. What about the 800x600 wallpapers in windows xp ???

DAMN IT Basse1989 !

---

### Post by benplaut on 2005-05-14
[QUOTE=Jesus Franco]
Jesus Franco expressed his disagreements with Ubuntu trash talking in this post. It was deleted because of its offensiveness. This placeholder is just to put this post in context. --PanickedThumb
[/QUOTE]

what's wrong with discussing it? if you don't like the discussion, then just go and hang out in some other forum...  :-# 

OK, you have another backer... i see it too   :?

---

### Post by TravisNewman on 2005-05-14
Nobody is talking crap about Ubuntu. People are trying to find out why their backgrounds are having the banding effect. There was no trash talking until people started talking about trash talking.

---

### Post by Paul Sinnett on 2005-05-15
[QUOTE=panickedthumb]Nobody is talking crap about Ubuntu. People are trying to find out why their backgrounds are having the banding effect.[/QUOTE]

Absolutely. We can't fix it if we can't talk about it.

I've uploaded some images to the gallary that show the problem and an example of how to get around it using dithering. It's not a perfect solution though. The colour differences are simply scattered at random to prevent your eye from seeing them as bars. The colour differences are still visible if you look closely enough. Also if you try to scale or compress the image using jpg, the bars return.

I have a modified version of the background that you could try. It is a slightly different brightness to the original because I couldn't quite match it up right (and I thought it looked better that way anyway  :)  )

[IMG]http://ubuntuforums.org/gallery/files/1/0/7/1/4/warty-final-ubuntu-blended-1024_original.png[/IMG]

---

### Post by arctic on 2005-05-15
has anyone of you ever thought of the possibility that the picture was made with 72 dpi which is known to create problems with graphics-display? 
if the design is filled with too many gradients per square-inch, you will get a bad looking picture. the only way to avoid it is to create the pictures as png or other high-res capable formats with at least 300 dpi. ;)

---

### Post by kassetra on 2005-05-15
[QUOTE=arctic]the picture was made with 72 dpi which is known to create problems with graphics-display?[/QUOTE]

Most visual displays have a physical limitation of 72dpi rendering - yes, you can alter some settings to make it say 96dpi, but that's a software manipulation, so unless you purchase a physical 96dpi monitor (similar to those in graphic design shops) - your monitor is physically 72dpi (which you can find out the hard way by printing out "web" graphics.)

72dpi creates absolutely no issues with graphics display hardware, because it exactly matches the physical limitations of the monitor/screen - the problem occurs, instead, in the graphics rendering algorithms.

For instance - all of these graphics render flawlessly on my system.  I do not have any banding whatsoever unless I tune my display down to 16 colors.  

Furthermore, I know for a fact that a 300dpi image will not correct the banding issue, because the algorithm will still render it incorrectly.

Solving the issue is a bit trickier - because it's unlcear which algorithm, exactly, is responsible for the banding.  Have you created your own gradients that show without banding?  It is possible, perhaps, to develop a fix or workaround from knowing what parameters trigger the banding and which ones do not.

---

### Post by arctic on 2005-05-15
hmmm... maybe they own 96 dpi monitors. i actually only run high-res monitors on my design machines (two i686 pc plus one g3, four g4 and two g5 machines, each with apple 23" cinerama tft monitors (logical... somehow)), so i cannot really tell you if they look ugly on lower resolution monitors... but as some people stated it... bfff...
i actually experienced differences when working with 72 or 300 dpi on wallpapers (large prints are - of course - a different matter :D), so i guess it is not only a hardware thing but still a minor problem with numerous graphic-design programs (on mac, win and linux).

---

### Post by mohaham on 2005-05-15
i was able to get rid of the banding effect from my machine..
the problem was with the graphics card configuration..
So if u see  any color banding, chances are that ur graphics card
is configured  incorrectly..
Ubuntu Wallpapers are perfectly OK..

---

### Post by Paul Sinnett on 2005-05-15
[QUOTE=mohaham]i was able to get rid of the banding effect from my machine..
the problem was with the graphics card configuration..
So if u see  any color banding, chances are that ur graphics card
is configured  incorrectly..
Ubuntu Wallpapers are perfectly OK..[/QUOTE]

It may be true that an incorrectly configured monitor will show the problems more, but there are problems in the source images. If you take a histogram of the image you can see the tell tale gaps and spikes caused by cumulative rounding errors in the image editing. And if you draw a colour picker across the gradient you will see that instead of smoothly fading in values the colours sometimes jump and sometimes even reverse direction. These "should" be visible as rings on any correctly configured monitor since the differences are well within the ability of the average human eye to distinguish. I say "should" because it's obviously not what the artist wanted.

Computer generated images are particularly prone to this problem but natural fades such as the sky in a photograph can also demonstrate banding even with 24 bit resolution. Mostly though, it's the loss of resolution during editing that causes these effects. You can usually avoid the problems so long as you are careful about the order in which you perform edits.

---

### Post by SKLP on 2005-07-15
[QUOTE=Paul Sinnett]Absolutely. We can't fix it if we can't talk about it.

I've uploaded some images to the gallary that show the problem and an example of how to get around it using dithering. It's not a perfect solution though. The colour differences are simply scattered at random to prevent your eye from seeing them as bars. The colour differences are still visible if you look closely enough. Also if you try to scale or compress the image using jpg, the bars return.

I have a modified version of the background that you could try. It is a slightly different brightness to the original because I couldn't quite match it up right (and I thought it looked better that way anyway  :)  )

[IMG]http://ubuntuforums.org/gallery/files/1/0/7/1/4/warty-final-ubuntu-blended-1024_original.png[/IMG][/QUOTE]
Your "hacked" version is a LOT better, tho some very minor "banding" is still visible on my digital LCD monitor (DVI-connected).

---

### Post by mal on 2006-06-04
I have 2 machines - one with a nvidia gforce 5200 and the other with a gforce 6600.  Both machines are now running Dapper and both have Benq FP71E LCD monitors.

On the 6600 display the standard Dapper backgound looks fine, while on the 5200 display, there is a definite banding effect.

Both are running at 24 bit colour depth, as shown by xwininfo.

Any ideas?

Mal

---

### Post by stepping razor on 2006-06-13
the situation would be a lot better if people were allowed to post svg image on the gallery. then people could either use the svgs as desktops directly (which is possible in 6.06) or load the svg into inkscape and render the desktop to whatever resolution they want.

---

### Post by graigsmith on 2006-06-16
Your color depth may be 24 bit, and thus the image would display correctly, but if you are using a poor quality lcd (like me) then you wont be able to get all the colors, and some gradients will look crappy, and unsmooth.

---

### Post by ikilledclown on 2006-06-18
I have had times where images look bad quality, but next time you boot it's all fixed, mid you that was on windows many a time ago, but maybe thats whats happening to him?

---

### Post by mixim on 2006-06-20
Listen all of you guys, Ubuntu-wallpapers are in bad quality... Why, I don't understand!

It's better in Dapper, but in Hoary it was too bad... Still why can't they just make one with good flowing gradients without the "steps"... 

It looks like 16-bit but i'm in 24-bit... and it looks the same in windows @ 32bit... I doubt it's because of a low quality LCD-panel since i have a rather good one... Viewsonic VP930B

---

