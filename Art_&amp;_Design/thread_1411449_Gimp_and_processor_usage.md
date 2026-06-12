---
title: "Gimp and processor usage"
date: 2010-02-20
forum: Art &amp; Design
---

### Post by rmccutchan on 2010-02-20
Hi.

Today I built my first computer.  Quite a project, but it went smooth.  One reason I built a new computer is because I was using an old Dell with a pentium 4 2.8ghz processor and 2 gigs of ram.  Whenever I used a large brush to dodge or burn, the brush would really lag behind.  I would paint across the picture at a moderate pace (one second swipe across the photograph from a Canon 20D), I could take my had off of the mouse and wait for the brush to catch up after a couple of seconds.

My new machine has an AMD Phenom II dual core 3.1ghz processor and 2 gigs of ddr3 ram on an  Elitegroup A785gm-m motherboard.  There is a definite improvement, but there is still a lag when painting as before, but not near the extent as before.

I recall that when working in Photoshop, there never was a lag when dodging or burning.  If I swipe a very large brush across the picture to darken a large section, it did so instantly.

I know nothing about algorithms and such, but it seems safe to assume that Gimp and photoshop process information differently.  Is this true, or is there something I need to change in the way I manipulate photographs.  The manual for the motherboard explains how to overclock the processor.  I really didn't want to do this, but I may try just for the heck of it.  The system I built has a total of 6 fans, so heat build up should not be a problem.

The lag now is not an unbearable amount, but I am just curious, and thought there would be someone here who is a lot smarter than me who could explain.

Thanks in advance

Bob

---

### Post by cubeist on 2010-02-20
> **rmccutchan said:**
> Hi.

Today I built my first computer.  Quite a project, but it went smooth.  One reason I built a new computer is because I was using an old Dell with a pentium 4 2.8ghz processor and 2 gigs of ram.  Whenever I used a large brush to dodge or burn, the brush would really lag behind.  I would paint across the picture at a moderate pace (one second swipe across the photograph from a Canon 20D), I could take my had off of the mouse and wait for the brush to catch up after a couple of seconds.

My new machine has an AMD Phenom II dual core 3.1ghz processor and 2 gigs of ddr3 ram on an  Elitegroup A785gm-m motherboard.  There is a definite improvement, but there is still a lag when painting as before, but not near the extent as before.

I recall that when working in Photoshop, there never was a lag when dodging or burning.  If I swipe a very large brush across the picture to darken a large section, it did so instantly.

I know nothing about algorithms and such, but it seems safe to assume that Gimp and photoshop process information differently.  Is this true, or is there something I need to change in the way I manipulate photographs.  The manual for the motherboard explains how to overclock the processor.  I really didn't want to do this, but I may try just for the heck of it.  The system I built has a total of 6 fans, so heat build up should not be a problem.

The lag now is not an unbearable amount, but I am just curious, and thought there would be someone here who is a lot smarter than me who could explain.

Thanks in advance

Bob

It probably is not the processor holding you back...actually I have a similar processor and it handles everything I throw at it.  The problem I have in Gimp is ram usage, and this might be causing your slow down.  Try changing your Gimp tile cache in Edit: Prefs: Environment.  I have 3GB of ram so I use a 2GB tile cache.

If anyone else has ram usage tips for Gimp, please share.  It's such a hog.

---

### Post by rmccutchan on 2010-02-22
My system has 2 gigs of DDR3 1333 ram, and the tile cache in gimp is set to 1 gig.  So you think an additional 1 or 2 gigs of ram in the computer and giving more to the tile cache would do the trick?  If so, then I'll head back to new egg and get it ordered.  

This is actually the reason I decided to upgrade computers.  I have a LOT of pictures (1,000's) to process, and I was hoping Gimp would be a little less draggy than what it is.  It is not unbearable, but just a little slower than what I had imagined.

---

### Post by PC_load_letter on 2010-02-22
HI...I'm no Gimp expert, but I never experienced what you're talking about on my desktop, laptop is another story, read below. When I use a brush to paint over a picture it's instantaneous. May I ask 2 questions: 

1- What kind of graphics card & driver combination do you have? Could this be a driver issue?
2- How large is the image file that you're using? 

In my case, I tried painting over a 8.8MB jpeg file from my Athlon x64 dual core, 8 GB Ram, running 64bit Ubuntu Karmic + GeForce 9500 GT w/ Nvidia proprietary driver. The painting motion is instantaneous. 

OTOH, from my ancient Thinkpad 43 w/1.5 GB Ram running Xubuntu 9.04 32bit w/ on chipset ATI Radeon mobility w/ default driver, there is noticeable lagging. It's not a big deal for me, but I do agree it could be annoying.

**EDIT:**
By the way, I got my 8GB kit from Newegg, I got G.Skill brand and I think it's amazing.

---

### Post by PC_load_letter on 2010-02-22
Ok, tried the same thing from my wife's Dell Vostro laptop, Ubuntu 9.04 32bit, dual core2 duo, 4GB Ram, Nvidia GeForce 8400M GS running the proprietary driver and there is no lagging at all. 

So, I'm not sure if it is the memory, my bet is on the GPU + driver combination. My 2 cents.

---

### Post by rmccutchan on 2010-02-22
Thanks for the response.

*I have Radeon HD 4200 graphics on board
*The image file is a 47MB Tiff.
*Also tried it on a 3.5MB Jpgeg with the same results.

If I use a small brush (scaled to 3 or less), there is almost no lag, but anything over that,there is, especially at 10.  I can go back and forth several times and take my hand off of the mouse and wait for the brush to get done moving.  It also takes a long time to do the Sharpen (Smart Redux) filter.

I don't know anything about Ubuntu 64bit.  Would this be something I should check into?  I believe my hardware is set up for it, but like I said, I just don't know anything about it.  Or would a decent graphics card be a better option.

Also, when I installed Ubuntu, it found the driver for the graphics and installed it, so I assume it is up to date and correct.

---

### Post by PC_load_letter on 2010-02-23
ok, it seems that you are not familiar with the driver situation in Linux. You can google about it and read more, but the bottom line (to the best of my knowledge) is that the performance of Nvidia and ATI cards under Linux is not on the same level. 
Nvidia driver is light years ahead of ATI's, although it seems after AMD had open sourced the driver, the development is catching up, but still, the performance of ATI cards under Linux is nowhere near its performance w/ Windows.

Bottom line is, I wouldn't be surprised if what you are experiencing is an ATI driver issue more than anything, I think it'd would be too much of a coincidence that I could reproduce the lagging only on the ATI equipped computer. 

As for 64bit, you have to have a supporting processor, which I'm sure you do. Personally I'd add more memory (4GB is decent). There is a substantial gain in performance for software that takes advantage of this architecture, specially in image & video editing. I have been using 64 bit since Feisty :D Never looked back.

---

### Post by rmccutchan on 2010-02-23
Thanks.  I am still learning about how all of this works.

When I watch the system monitor, the ram never excedes 40% while processing with 2 gigs, but one of the processors hits 100% while Gimp is working on some labor intensive stuff.  If I understand correctly, if you have ram on 2 separate channels, it will utilize both and in effect be more efficient. 

I was just researching whether or not to use 64 bit, and it seems that it would be advantageous with programs like Gimp and some others.

Is there anything I can do about compatibility/drivers for the ATI graphics system, or would it benefit me to purchase a good graphics card (Nvidia) if it will work?

I was just thinking I might try to dual boot with Ubuntu 64 bit and try it out.  If it performs better, then I could back up everything and install it.

---

### Post by PC_load_letter on 2010-02-23
It's the ATI driver, see this thread and see if the workaround will fix this for you.
HERE:
[http://ubuntuforums.org/showthread.php?t=751892](http://ubuntuforums.org/showthread.php?t=751892)

---

### Post by rmccutchan on 2010-02-23
Well, I tried deactivating the driver, and it got worse and some weird colors showed up.

I think I will see if there is a Nvidia card I can get for this motherboard.  This was my first EVER build-from-scratch computer, so there is always some lessons to be learned.  Had I known about ATI, I would have chosen a different motherboard.

It definitely runs faster than my old Pentium 4, though.  Everything else besides the gimp brushes seems to run at lightning speed on this new box.

I will order some more ram and install it according to the manual for optimum speed.  Maybe that will help.

I am anxious to give 64 bit a try.  From my research, it should help to a certain degree.

We have a computer store where I live and they really push linux.  The owner was a unix programmer, so he knows a little about what he is doing.  I will take the computer in and see what he thinks.  He doesn't charge for advice and his prices are reasonable. :)  

I really appreciate all of the help.  I love this forum because of the helpful people that are willing to give advice.  I just hope I get to the point where I can contribute more.

Thanks!

---

### Post by rmccutchan on 2010-02-25
Update:

I stopped by my local computer dealer and picked up an Nvidia Geforce 8400GS.  I got installed, started using Ubuntu 64bit, but there is no change in the brush lag.

I think I will order some extra ram to see if that helps.

---

### Post by PC_load_letter on 2010-02-26
Well, just one thing, are you running the proprietary driver? 
System > Administration > Hardware drivers

EDIT: You should have the Nvidia 185 driver, and if it's working, it should look like this: 

[IMG]http://img191.imageshack.us/img191/8937/screenshothardwaredrive.png[/IMG]

---

### Post by rmccutchan on 2010-02-26
Thanks.  That's exactly what mine looks like.  I'm using version 185.

My son and I did a little test:  We played Sauerbraten and turned everything to the highest quality and used the highest number of bots to fight in a free for all match and picked the scene that looked like it had the most graphics.

I don't play games at all and I don't know how much Sauerbraten will tax a system, but everything ran very smooth and fast.  There were explosions all over the place and a million bots running everywhere and my son (who is a gamer) said it ran VERY smooth.  

I think the video card is definitely an improvement for the system, so evidently Gimp doesn't rely heavily on the GPU, but maybe the ram instead.

I have one stick of 2 gig of ram installed, and I have another 2 gigs of the exact same ram ordered (Kingston DDR3 - should be here Monday), and I will install it into the other channel like the manual says and see if that makes a difference.

I will keep updating this post in case there may be someone else who runs into the same thing.

Thanks for the replies!

---

### Post by cubeist on 2010-02-26
> **rmccutchan said:**
> Thanks.  That's exactly what mine looks like.  I'm using version 185.

My son and I did a little test:  We played Sauerbraten and turned everything to the highest quality and used the highest number of bots to fight in a free for all match and picked the scene that looked like it had the most graphics.

I don't play games at all and I don't know how much Sauerbraten will tax a system, but everything ran very smooth and fast.  There were explosions all over the place and a million bots running everywhere and my son (who is a gamer) said it ran VERY smooth.  

I think the video card is definitely an improvement for the system, so evidently Gimp doesn't rely heavily on the GPU, but maybe the ram instead.

I have one stick of 2 gig of ram installed, and I have another 2 gigs of the exact same ram ordered (Kingston DDR3 - should be here Monday), and I will install it into the other channel like the manual says and see if that makes a difference.

I will keep updating this post in case there may be someone else who runs into the same thing.

Thanks for the replies!

I wish I had come back to this thread a couple days ago.  I could have saved you some money.

First.  There is nothing wrong with ATI graphic cards in linux.  Both the 2D (open source) and 3D (restricted) drivers work great and have had a ton of development over the last few years.  Unfortunately there are many users who still think Nvidia has a huge edge over ATI in linux because that was true a half-dozen years ago.  My only concession to this statement is that Nvidia does tend to implement new technology in their driver before ATI.  So if you are a serious gamer, or do lots of video processing, Nvidia is the better bet.

Anyway, for Gimp, ATI is a perfectly fine choice and is not the most important part of running Gimp smoothly.  I often work with very large images (100MB+) and my GPU does hardly anything.

In terms of your problem, RAM may help, but there might be another problem at work too (a bug in the program).  I looked through the current bugs and did not see one exactly the same as yours, so you may want to file a bug report.  Here is a link:
[https://bugzilla.gnome.org/browse.cgi?product=GIMP]("https://bugzilla.gnome.org/browse.cgi?product=GIMP")

Finally, to clarify, your problem might just be the way Gimp is, and the rest of us are used to it.  For example, if I open a 10MB jpg from my camera and select a small brush with the dodge/burn tool I can drag it back and forth a dozen times *without releasing* before it slows down, at which point I have to *release* the stroke to let the cache catch up.  I can do this over and over all day.  However, on the same small image, if I select a really large brush (1000px wide) I can do only one stroke across the image before I have to release the stroke.
On the other hand, If I open a big image (300MB) using a small brush I only get a couple/few drags of the brush before I have to release the stroke, OR, I can keep a continuous stroke going but it begins to lag behind the cursor.
As I understand how Gimp is coded, this is normal for the program... it is just a cache hog (aka ram).

Oh, one other thing, you asked about 64-bit.  In general 64-bit is faster than a 32-bit system, especially when a process does mathematical calculations as part of it's execution.  Generally there are small improvements in desktop functions (moving/copying files), and most programs will do things a little bit faster... just a second saved here and there; but some programs, like Blender 3D are much faster in 64-bit.   I have been using a 64-bit OS for about 6 years with nary a problem.  Others have experienced problems and headaches... there are a ton of 32-bit vs 64-bit threads on theses forums!

---

### Post by PC_load_letter on 2010-02-26
Mr Cubeist: 
So, just out of curiosity, where is the $$ that you could have saved the OP if your suggestion is that it's a bug!!!???

I don't want this thread turned into Nvidia vs. ATI, but the ATI driver for Linux still lags behind their driver for Windows, more than the case on the Nvidia's camp. Maybe there is not much difference between two comparable cards in 2D, but definitely in 3D the Nvidia linux driver still has the edge. 

You're saying this is how Gimp is, well, it is not, not to me anyway running on the Nvidia equipped computers. If what u're saying is that it is not that big of a deal, well, welcome to the club. But the OP is entitled to his opinion and he obviously did not want to suffer this lagging on his newly built PC. 

Maybe more ram would help, but I don't see how memory could be a problem if he (and I can confirm) gets the lagging even with small image files, 6 or 8MB in my case on a 1.5GB laptop.

---

### Post by cubeist on 2010-02-26
> **PC_load_letter said:**
> Mr Cubeist: 
So, just out of curiosity, where is the $$ that you could have saved the OP if your suggestion is that it's a bug!!!???
.
So he would not have to go out and buy an Nvidia card when he already has a brand new ATI card.

I suggested that ram *MAY* help his situation because ram is a factor in determining the resources available for a program.  A GPU, (ATI or Nvidia) will simply render the pixels of the image that Gimp tells it to render...It is not doing the bulk of the calculations.


Further, before you lash out at others, perhaps you should have the courtesy of actually reading others posts.  I clearly state:
> "There is nothing wrong with ATI graphic cards in linux...[however] Nvidia does tend to implement new technology in their driver before ATI. So if you are a serious gamer, or do lots of video processing, Nvidia is the better bet."

Lastly, you refute your own point.  Gimp is a 2D Application, it does not render 3D images, so when you say:
> "Maybe there is not much difference between two comparable cards in 2D, but definitely in 3D the Nvidia linux driver still has the edge."
you affirm that ATI or Nvidia will work equally for Gimp and thus falsely gave hope to the original poster that his problem could be fixed by buying a new graphics card.

To rmccutchan, if you have questions feel free to send me a private message, I won't respond further in this thread.

---

### Post by PC_load_letter on 2010-02-26
First off, the objective of this forum is to help others solving problems they might have with Ubuntu. It is not for personal gain or praise, I expect neither. Solving problems through PMs IMHO misses the whole point. But if Mr. Cubeist doesn't wanna contribute to this thread then that's fine, it's his decision.   

Now back to topic: 
- I could duplicate this lagging on a friend's laptop (HP tc4200 tablet), with Intel graphics chipset w/ the standard driver. Laptop memory is 1.5 GB, the image file was 10MB, and according to htop (run in terminal), Gimp was using 20% of memory, that went up to 25% while using a size 10 brush. Total memory usage was between 680 and 700MB out of 1500MB. At no point swap was used, it was 0 from start to finish. That's why it would be very interesting to know the reason if indeed the memory will resolve this issue.

- To Mr Cubeist (or others who did not read this thread from the start): The reason the ATI driver was under suspicion of being the culprit is due to this thread: [http://ubuntuforums.org/showthread.php?t=751892](http://ubuntuforums.org/showthread.php?t=751892)

- To the OP: if you do file a bug report, make sure to post the link in this thread so I (and others) could confirm it.

---

### Post by PC_load_letter on 2010-02-27
An update: 
There is a mention of this problem on the official documentation page of Gimp and there is a suggestion that seems to improve things a bit, at least on my friend's HP tc4200. 

Link:[http://docs.gimp.org/en/gimp-pimping.html](http://docs.gimp.org/en/gimp-pimping.html)

Search for the word "lag" on the linked web page above. The suggestion given is to uncheck "Show brush outline" from Edit > Preferences > Image Windows menu.

---

### Post by rmccutchan on 2010-02-27
I unchecked the "show brush outline", and it might have helped slightly, if at all.

I submitted a bug report.  I hope I did not do this prematurely.  I've never submitted a bug before (never had one!), so I hope I went through the proper channels.

The bug number is:  611264
Here is a link:  [https://bugzilla.gnome.org/show_bug.cgi?id=611264](https://bugzilla.gnome.org/show_bug.cgi?id=611264)

It does seem strange, though, that everything else I do on this computer is freaky fast (compared to what I am used to), and the brushes in Gimp have such a lag.

According to what cubeist says, it just may be the nature of the beast and something I have to live with.  That would be a shame, because this issue is the reason I built this computer in the first place.  I thought the brush lagged because I was using such an old computer.  

My motherboard has 2 channels for ram, and the manual recommends if using 2 sticks of ram, to use one in each channel for best performance.   Like I said, I have another stick of 2 gig ram ordered, so it will be interesting to see if using this configuration will change anything.

Is there anything else I need to do about the bug report?

PS:  I really appreciate the input from both of you.

---

### Post by PC_load_letter on 2010-02-27
Well, I'm no expert on memory, but what I know is that you should always install ram sticks as matching pairs. You do not mix and match as this may result in increased memory errors and might slow you computer down. That's why most if not all the ram kits you see at Newegg for example has two matched sticks.

Question: How about the performance of other 2D graphics software? For example, how fast and responsive is Inkscape?

EDIT:
Also, why don't you install htop (just type **sudo apt-get install htop**), and run it from the terminal by typing **htop** while you do a brush lagging experiment on Gimp and see how much memory Gimp is using, how much total ram is being used, and if swap is being used at all.

---

### Post by rmccutchan on 2010-02-27
I tried inkscape.  I'm not sure how to use it, but I did manage to choose a large brush, and not matter how fast I went, there was no lag.

Here is a reply from one of the Gimp developers:

[I][B]"That is a problem with your graphics card driver then. It obviously cannot
handle the large amount of lines we ask it to draw. Mid-term we'd like to
change the way the brush and selection outlines are drawn. For now I suggest to
disable drawing of the brush outline."[/B]

[/I]I ran htop and got this while the brush was in full lag:

[I]   Processor 1:  97%
   Processor 2:  1.3%
   Mem:  632/2009MB
   Swp:  0/5137MB[/I]

It sounds like it may just be the way it is, and I may have to be patient and slow down while using the brush.

Ram will be here Tuesday, so I can do test then.

I have a lot of respect for the Gimp developers.  They can't make everything for everybody, so if this is the way it is, I will gladly live with it. :)  I mean seriously, look at the price of Gimp compared to Photoshop, and Gimp can do WAY more than I will ever need for my photography.

It also sounds like the deveopers have some new things coming within the next year or so.:P

---

### Post by rmccutchan on 2010-03-02
Another update:

Ok.  I installed another 2 gig stick of ram according to the manual.  So I now have one in DIMM3 and DIMM4 for a total of 4 gigs.

Hardware:
   *AMD Phenom II X2
   *ECS Elitegroup Motherboard
   *EVGA Nvidia 8400 GS GPU w/proper driver activated
   *2 X 2gig DDR3 1333 Kingston Ram
Gimp:
   *Tile Cache: 2GB
   *Number of Processors to use: 2

I did not really notice a difference in the brush lag.  Maybe a little if I move at a moderate to slow speed, but not much.  Also, after working on a photograph for a while, it starts to slow down more.

You can see what the Gimp developers had to say in my last post.

Like I said, it is not an unacceptable problem, but just something I was wondering about.  

I really am happy with the Gimp since I went non-Windows last August, and also with the performance of this new computer build :D:D

Thanks to all who replied.

Bob

---

### Post by Baljamin on 2010-03-03
Thanks for share valuable information.

---

