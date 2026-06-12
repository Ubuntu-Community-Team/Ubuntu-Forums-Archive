---
title: "Sketching with the GIMP in Ubuntu 9.04"
date: 2009-04-29
forum: Art &amp; Design
---

### Post by Niva on 2009-04-29
Hello friends,
I'm shocked and amazed at many things in Ubuntu 9.04 and I honestly think it's the most usable and friendly linux distribution to date.  Especially pleasing is the fact that my wacom tablet was immediately recognized during the install!

I sketch a lot, usually in windows/photoshop where I do most of my production painting.  However, every once in a while I get the urge to push GIMP a bit, to get used to it and know the interface.  Here's today's result after 30 mins in GIMP 2.6.6

[IMG]http://www.eternalseven.com/images/2009/ubuntu-girl.jpg[/IMG]

I really think GIMP is also improving for the better and is becoming a real competitor for PS on many fronts, esp considering it's OSS.  

I did hit a minor snag though, I can't seem to configure my tablet keys using wacomcpl as I used to be in the past.  Attempting to run it resulted in a message to do:

> sudo apt-get install wacom-tools

After this installs successfully i can run wacomcpl but it comes up corrupted, nothing shows in the window.  Restarting the system results in it not recognizing wacomcpl at all after the restart (not like it was any good anyways) and prompts for another install which similarly fails to work like the previous attempt.

Any pointers in the right direction would be much appreciated.  

My biggest peeve for the GIMP cycle of development right now is that it doesn't on its own recognize an available tablet.  I also think that once the tablet is enabled as an extended device it would be nice to have the strips on my intuos3 tablet work for zooming in and out similar to how photoshop works.

Wacomcpl allows me to set the strips to +/- keys, so this is why I need wacomcpl to work, unless things have changed and there's a new tool I need to know about.

Thanks in advance!

---

### Post by Favux on 2009-04-30
Hi Niva,

Nice!  There's actually some new rendering stuff in Gimp 2.6 that isn't turned on yet.  It is supposed to be in the next version and is felt to be a real move forward.

The problem is with the current HAL/.fdi method appears to be the callout from the .fdi file is returning names linuxwacom/xsetwacom doesn't recognize, and hence wacomcpl doesn't work.  While we wait for it to get fixed there are two work arounds.  One uses a script by rec that translates the HAL names to wacom names before Xserver starts and the other is finding out the current HAL names and using them.  Start on post #154 here and read forward:  [http://ubuntuforums.org/showthread.php?t=967147&highlight=tablet&page=16](http://ubuntuforums.org/showthread.php?t=967147&highlight=tablet&page=16)  And here is the Wacom.fdi wiki that talks about customizing the .fdi:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

I hope this is helpful.

---

### Post by Wiebelhaus on 2009-04-30
Wow , That's fantastic! Seriously.

---

### Post by Sand &amp; Mercury on 2009-04-30
Holy crap, you are brilliant.

---

### Post by Favux on 2009-04-30
No one has yet commented on the Ubuntu shoulder tatoo.  So I will.  Nice tatoo!

---

### Post by lyceum on 2009-04-30
The pic is great! and I agree. I have done art in Ubuntu with GIMP and my wacom tablet, and it is like using a mouse - no sensitivity. For some magic reason when I first started using Ubuntu it worked great, but then I bought a new laptop and it didn't work at all. When I did get it working, it was too clunky. I would really love to see more stuff for the art world in FOSS and until wacom works standard, there will be problems no matter how good GIMP is, IMHO.

---

### Post by Dragonbite on 2009-04-30
Great pic. Are you able to do a tutorial on how you did it (what brushes, settings, etc.)?

As for the Wacom tablet issue, sorry I have not experience with that. I have an Adesso that my parents gave me and I can't get it to react any different than a mouse!

---

### Post by Niva on 2009-05-02
Hey guys,
Thanks a lot for the kind feedback on the sketch.

Favux, yeah, I guess we wait.  I'll check out that thread for a workaround and see if I can get it to work.

There isn't anything special about the drawing above, it was done with the standard brushes that come within GIMP, mostly the round hard brush with opacity linked to pressure.  I usually start with black and white, then put a color overlay and then tweak the colors until I get them to a point where I like them.  I also adjust the levels a lot during my drawing process, I usually tend to work too light and then overcompensate by darkening things up too much.

Here is another very quick sketch I made tonight, demon type face:

[IMG]http://www.eternalseven.com/images/2009/ubuntu-demon.jpg[/IMG]

I did use the pencil brush on this a bit for some of the texture.  Since the GIMP brush engine is totally different from the photoshop engine I'm going to have to experiment a while before I get it to work right like I want it to.  Also the smudge tool in GIMP works VERY different from the photoshop brush.

One thing I don't like about GIMP is how it sticks brushes between different tools.  I should be able to pant with one brush, with its own settings, and switch to a tool like the smudge with a totally different brush w/o affecting the paint tool.  

I'll report back after I try the new settings.

Is there some video capture program I can use in ubuntu to record a drawing in progress?  Or maybe something that would take screenshots every 30 seconds or something like that?

---

### Post by Favux on 2009-05-02
Hi Niva,

Awesome!  Worthy of nightmares.


In retrospect I realize I gave you quite an info dump.  I apologize.  If you want to cut to the the chase read Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  If you decide on 1) and use rec's script (wacomtohal) that looks like all you need to do.  So that is fairly quick and simple.  And wacomcpl should then work.

Even though it is a usb tablet, since it is working, I think you can ignore the stuff about compiling 0.8.3-2 for the wacom.ko kernel module and the rest.  If you get an update and things suddenly stop working that probably means they fixed things.  So then you would just remove rec's script.  That avoids renaming things.

And a link to setting up an intuos 3 that may be useful:  [http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup](http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup)

---

### Post by Dragonbite on 2009-05-03
Love it!

---

### Post by Bölvaður on 2009-05-03
> **Niva said:**
> 
Is there some video capture program I can use in ubuntu to record a drawing in progress?  Or maybe something that would take screenshots every 30 seconds or something like that?

Under Add/Remove you can find
[B]gtk-recordMyDesktop

[/B]or just type in terminal

```
sudo apt-get install gtk-recordmydesktop 

```

---

### Post by jszdouhuolai on 2009-05-04
This clock projects the time, date, or temp on the wall or ceiling [http://www.liangdianup.com/clocks_1.htm](http://www.liangdianup.com/clocks_1.htm)  some people call 
it a ceiling clock but I call it a digital projection clock. I got the black one because at the time that was the only color 
they had. But now they have them in black and also in white.

---

### Post by Psyphre on 2009-05-04
Hi all.

I too am trying to draw fully in ubuntu - I previously used Windows/photoshop.

GIMP is really good, im so impressed with it especially considering its free. It does have a few issues, most notably the brush strokes arent as smooth as photoshop (has some jaggedness), so doing lineart is harder.
Strangely enough the 'caligraphy' tool is really smooth, so i use that instead of a brush. It seems wierd that they dont incorporate the same smoothness into the brush.

Niva is it ok if we exchange emails/chat? From one artist to another I thought it might be helpful as we are both trying to grapple with learning GIMP. Im curious how you've set your brushes and such.

Heres a practice attempt I did in GIMP.

[[IMG]http://img144.imageshack.us/img144/7039/eyepractice2.th.png[/IMG]](http://img144.imageshack.us/my.php?image=eyepractice2.png)

Finally another issue I'm having is aspect ratio. My Wacom is a 4:3 where as my monitor is a widescreen. In windows the wacom drivers allow you to cut off a part of the top/bottom of the wacom so it becomes widescreen.
Dont know how (if possible in the first place) to do it in ubuntu.

---

### Post by Niva on 2010-09-21
So I heard of folks having all sorts of trouble with wacom and Ubuntu 10.04  Actually I heard about this a while ago and never upgraded my big workstation to the newest Ubuntu until this could be resolved.  Today I decided to see if I can get it to work on my laptop which is sporting 10.04 and amazingly everything worked right out of the box... 

So why people are having trouble I have no clue?

Anyways, I figured I'd post here a quick sketch I just made.  

[IMG]http://www.eternalseven.com/images/2010/20100921-GIMP-Sketch-Ubuntu10.04-small.jpg[/IMG]

Really looking forward to updates in the GIMP.  I also need to figure out how to set up my strip bar for zooming, that slows me down the most right now.  I'm going to play with this in the next weeks when I have some time and see if I can get it right and to stick.  In the past I was able to configure it but every time when I rebooted I had to reconfigure the settings.

Psyphre:  Sorry i didn't respond to your questions.  You can email me through my site if you need to get in touch, I rarely check here.  That eyeball looks awesome, keep it up.

---

### Post by Niva on 2010-10-17
I installed 10.10 the other night, still not sure how I feel about it.  Anyways one of the first things to get in order is to make sure the tablet works fine and to do a quick test sketch.

About 30 mins of fun.

[IMG]http://www.eternalseven.com/images/2010/20101015-GIMP-Test-Portrait.jpg[/IMG]

[ATTACH]172695[/ATTACH]

---

### Post by Dragonbite on 2010-10-18
> **Niva said:**
> I installed 10.10 the other night, still not sure how I feel about it.  Anyways one of the first things to get in order is to make sure the tablet works fine and to do a quick test sketch.

About 30 mins of fun.

[ATTACH]172695[/ATTACH]

Cool job!  Especially for 30 minutes.

---

### Post by belkinsa on 2010-10-19
Maybe you could try MyPaint, might be a better choice then GIMP.

GIMP for me is just to hard to use.

---

### Post by Niva on 2010-10-22
Mecha > I've never used MyPaint but installed it last night and will give it a test drive hopefully this weekend if my liver survives the festivities we have planned :)

I do like GIMP in general, because many things are laid out similar to photoshop which is my main software painting package that I use.  The one thing that really sets GIMP back right now is brush engine and the various things you can do with brushes in an app like photoshop.  It's great for basic sketching though which is what I use it for.

Thanks for the tip though, I'm always up for trying new things.

---

### Post by Niva on 2010-10-23
OK thanks for letting me know about MyPaint, I just played around with it for an hour.  The brush engine is clearly awesome but still some issues.  Really at this stage I'm not sure where stuff is properly located and how to control things.  Seems like brushes and smudging and erasing tools are all mixed in.  Layer controls are bad in this application.  Brush size control is only by button pushes and it seems only certain % sizes are supported though I can't really tell.

The worst part about the brush size issue is that it requires me to have the keyboard at my disposal.  With PS or GIMP I can just put the tablet in my lap and lean back away from the keyboard as I work.  

Anyways, after about an hour of hacking this is what came out.  I know it's horrible and I adjusted the levels in GIMP at the end but my skills with this program are really limited at this stage.

[IMG]http://www.eternalseven.com/images/2010/20101023-Dragon.jpg[/IMG]

I can't believe it but this took me a bit more than an hour!  It would probably take me about 2 mins in Photoshop to doodle this.

---

### Post by robert shearer on 2010-10-24
Learning curves are so much fun :)..

[http://mypaint.intilinux.com/](http://mypaint.intilinux.com/)
[http://mypaint.intilinux.com/?page_id=3](http://mypaint.intilinux.com/?page_id=3)
[http://wiki.mypaint.info/Main_Page](http://wiki.mypaint.info/Main_Page)
[http://www.sintel.org/videos/tutorial-painting-time-lapse-by-david-revoy/](http://www.sintel.org/videos/tutorial-painting-time-lapse-by-david-revoy/)

---

### Post by Niva on 2010-10-25
Robert thanks a lot, those are awesome links, I looked through the first two quickly and I'll definitely play more with the program.

Below is the updated version of the dragon, done in Photoshop after the initial sketch.

[IMG]http://www.eternalseven.com/images/2010/20101023-Dragon-FINAL.jpg[/IMG]

And more updates to the girl a few posts above, I purposely left the hand huge, just wanted to render w/o modifying the shapes too much.

[IMG]http://www.eternalseven.com/images/2010/20101024-Elf-Sword-Girl.jpg[/IMG]

---

