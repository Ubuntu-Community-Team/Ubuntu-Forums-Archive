---
title: "Opinions on an AMD APU setup?"
date: 2012-02-25
forum: Any Other OS
---

### Post by Giraffemonster on 2012-02-25
Firstly, I'd like to start this off by saying that any mods should feel free to move this to the correct sub-forum, if there's a better place for this thread. Also, I'd like to apologize for any "facepalm worthy" stupidity I'll inevitably show.

So, I'm thinking about building a new setup. I've been using Ubuntu operating systems for around two years by now, but I've used the same system throughout. A lot of the things I do with my current setup run very slow. Some things I would like to do won't work at all. Desktop resolution is at 1280x960, and I'd probably keep it like that in a new setup.

Things I would like to be able to do, that I can't do in my current setup: Graphics editing at high resolutions, streaming videos at 720p or higher, video editing, composing audio with many tracks, recording audio with audio playback in audacity. Also, I'd most likely be using KDE with a few desktop effects.

I'm planning on building a system that uses AMD's new A8-3850, 2.9GHz  which includes an integrated 6550D processor. I've read a few reviews about it, but most just talk about gaming with it, which I won't be doing on a large scale. Thanks for reading, and once again, sorry if anything here sounds really stupid. I'll provide more information as requested.

EDIT: So I've built the system a while ago, and I'm now running Linux Mint 12 (Lisa) 64-bit. I'm having a few problems, and I believe that most of them are related to the drivers I'm using. They could really be anything though. If the details of these smaller problems are important, I'll be sure to provide the information.

I've been trying to improve some stability on my setup by using the proprietary drivers, but none of them seem to work. I've used the jockey-gtk application to install the drivers from the repositories. I've also tried to manually install the drivers from AMD's website. Regardless of the method, I end up with a system that runs fine, but crashes within the first minute of usage.

Is there anything that could help, or would it be better just to stick with the open-source drivers?

---

### Post by gradinaruvasile on 2012-02-25
That apu should handle everything you describe (as any decent cpu would btw).
Playing 1080p videos work even on pure cpu decoding on my Athlon II 250 x2 @3 GHz with no issues, so no problems here (make sure you install the xvba driver, libva and use vlc with gpu decoding, it will help greatly). Recording/playing back audio should not be a problem either. The computer in your sig should be able to do these also, i wonder why it isnt.

Tips: That kind of system must use dual channel memory to maximize performance so make sure you buy 2 identical memory modules and install them in dual channel mode (usually the blue colored brackets). The ideal memory speed is minimum 1600, anything below might slow down things a bit.
Install the proprietary fglrx driver and libva+ the xvba driver, so you can use vlc with hardware decoding.
Watch out for bugs in desktop compositing (desktop effects) - using desktop compositing can lower system stability and slow things down, i dont advise it if you want to use the computer for real work (this applies to all compositing engines).

---

### Post by Giraffemonster on 2012-02-25
> **gradinaruvasile said:**
> That apu should handle everything you describe (as any decent cpu would btw).
Playing 1080p videos work even on pure cpu decoding on my Athlon II 250 x2 @3 GHz with no issues, so no problems here (make sure you install the xvba driver, libva and use vlc with gpu decoding, it will help greatly). Recording/playing back audio should not be a problem either. The computer in your sig should be able to do these also, i wonder why it isnt.

Tips: That kind of system must use dual channel memory to maximize performance so make sure you buy 2 identical memory modules and install them in dual channel mode (usually the blue colored brackets). The ideal memory speed is minimum 1600, anything below might slow down things a bit.
Install the proprietary fglrx driver and libva+ the xvba driver, so you can use vlc with hardware decoding.
Watch out for bugs in desktop compositing (desktop effects) - using desktop compositing can lower system stability and slow things down, i dont advise it if you want to use the computer for real work (this applies to all compositing engines).

Thanks for the response. About the audio editing, my computer can record audio and such, but it's pretty laggy. Playing multiple tracks while recording bogs it down beyond usability. I'll be sure to check out those libraries as well. I already plan on buying 2 memory modules to go with it. As for the compositing engines, I don't really need too much effects. I barely use any on my current setup as it is.

When I mentioned streaming videos, I'm just saying that because my computer currently has trouble streaming anything 360p and higher. Just really not sure what to expect.

One question, where would you mostly find the GPU being used primarily over the CPU, other than in games? Benchmarks suggest that this APU is pretty good at performing CPU tasks, but not so much at those of the GPU.

And I'm happy to hear more from anyone else who can share their thoughts on this.

---

### Post by greg.9 on 2012-02-28
Hi there,
Just put together a system with an A8-3850 APU on a Gigabyte A75M-UD2H board as a family computer. Although I'm no expert, I have been with Ubuntu since Gutsy on my old desktop so am used to 'tinkering' a bit to get things right.
Its taken a couple of days, but, I now have Natty running well on 2.6.38-13 kernel with Catalyst 12.1 driver and it seems ok. 
Still a few bugs out there affecting these new APU's I think, hoping the next release will fix them, but will try it on separate partition till I'm sure.
Any questions I can help with before you decide let me know.

Greg

---

### Post by Giraffemonster on 2012-02-28
> **greg.9 said:**
> Hi there,
Just put together a system with an A8-3850 APU on a Gigabyte A75M-UD2H board as a family computer. Although I'm no expert, I have been with Ubuntu since Gutsy on my old desktop so am used to 'tinkering' a bit to get things right.
Its taken a couple of days, but, I now have Natty running well on 2.6.38-13 kernel with Catalyst 12.1 driver and it seems ok. 
Still a few bugs out there affecting these new APU's I think, hoping the next release will fix them, but will try it on separate partition till I'm sure.
Any questions I can help with before you decide let me know.

Greg

Oh, that's great! I ordered the same processor, but with a Biostar board. The processor still has yet to arrive, so I'll see how it works then.  I'll be sure to keep you in mind if I have any questions.

I was thinking of purchasing a dedicated graphics card to set up dual-graphics, but I figured I didn't need it. How's your processor working in terms of graphics processing?

---

### Post by greg.9 on 2012-03-03
Its a massive leap up from my last GeFORCE 6200 256mb card! Streams HD from BBC iPlayer and youtube no problem. I imagine Windoze would make it bigger, faster, better but I dont use it so cant compare. Tested it with the linux 3D 1st person shoot em games like open arena and plays all great on high graphics. It has done everything I have asked of it so far.
My best linux experience so far!

---

### Post by Giraffemonster on 2012-03-10
So yesterday, I just installed my new system which includes AMD's A8-3860 (Which includes Radeon HD6550D graphics). Yes, it is a huge leap. I don't game much, but there were a few games which I just couldn't get around to because of system specs.

Rather than downloading Kubuntu, I chose Linux Mint. Using GNOME 3 right now, which I don't really like that much. I might try downloading Cinnamon (Their fork of GNOME 3) soon, and see how that goes. It runs fast though, very smooth.

Having a problem though. The system runs just fine as it is, but if I choose to update the drivers, my system crashes. I've tried using the one provided by the "Additional Drivers" program, and I've also tried one downloaded directly from AMD's site. Both of them have the same result. The performance is fine with these stock drivers, but I don't have access to as many resolution options as I did before. No biggie, but does anyone have any articles or news to read up on about this?

Still though, HD videos are really nice.

---

### Post by greg.9 on 2012-03-12
I had to install the latest Catalyst driver manually to get things running well. There are lots of guides to doing this and although some advise against it worked fine for me.

---

### Post by Giraffemonster on 2012-03-15
> **greg.9 said:**
> I had to install the latest Catalyst driver manually to get things running well. There are lots of guides to doing this and although some advise against it worked fine for me.

Eh, just finished reinstalling Linux Mint and getting everything back to normal. Thankfully, I have my entire home directoy and var/cache/apt/archives (for packages) saved to a large USB 3.0 drive. Getting synaptic to read the packages from the directory took quite a bit of wrestling, but it was alright.

The reason I had to reinstall, is because I tried to install the proprietary drivers once more. Didn't work.

So I installed this once, installed the FGLRX drivers and then it started to crash within seconds. Installed it again, and installed it manually with a package from AMD's site. Same result. Tried to install the FGLRX (Post-release updates version), which wouldn't finish installing. Instead, I did the install from AMD's website, but with the help of a guide. Same result. Tried to remove the drivers, but my system seemed to have crashed sometime just before completely and safely removing them (yeah, perfect timing) and then ended up with a broken system. I tried to use a fix from the guide "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.ati" if I recall, and that didn't work.

So yeah, now I'm here with my newly installed system. I'm really hoping that some of the issues I get with Linux Mint 12 are limited only to Linux Mint 12, and that they don't have anything to do with the fact that I'm using an AMD Llano series processor.

Oh well, I guess I can deal with these things for a while. I'd still like to know if there's any sort of solution to it. Probably going to edit the OP and stuff, since the topic's changed for the most part.

---

### Post by kosme15 on 2012-03-15
I used to have a lot of problems with the fglrx driver not installing properly and even when it did install, not working the way it should.  And this is with a good old HD4650 card -- they've been around a long time and should be well supported.  Things started working for me, when I followed this guide:  [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)  

Two thing in particular that I learned from this guide are, first, never to run the installer directly.  Always create a .deb package and install it from the command line.  And second, the importance of calling aticonfig with proper command line options after installing the .deb files cannot be overestimated.  All this is described in detail in the above guide.  I used to have lots of headache with fglrx, but not anymore.  I hope this helps.

---

### Post by Perfect Storm on 2012-03-15
Thread moved to Other OS/Distro Talk.

---

### Post by mips on 2012-03-15
> **Giraffemonster said:**
> I'd still like to know if there's any sort of solution to it.

Buy a nVidia GPU and disable the onboard. Personally I would not have purchased such a system.

Either way I hope you get it sorted.

---

### Post by greg.9 on 2012-03-15
> **mips said:**
> Buy a nVidia GPU and disable the onboard. Personally I would not have purchased such a system.

Either way I hope you get it sorted.

Not very helpful, is it. Hope your 6539 other beans were more constructive.
My last system had lots more problems with nvidia and Nouveau drivers than I have had with Llano and ATI?



It reminds me though of a problem I read somewhere else of motherboard onboard graphics needing to be disabled in BIOS to get ATI driver to work.
Doubt your FM1 board has onboard but worth checking.

---

### Post by 0011235813 on 2012-03-15
> **Giraffemonster said:**
> Firstly, I'd like to start this off by saying that any mods should feel free to move this to the correct sub-forum, if there's a better place for this thread. Also, I'd like to apologize for any "facepalm worthy" stupidity I'll inevitably show.

So, I'm thinking about building a new setup. I've been using Ubuntu operating systems for around two years by now, but I've used the same system throughout. A lot of the things I do with my current setup run very slow. Some things I would like to do won't work at all. Desktop resolution is at 1280x960, and I'd probably keep it like that in a new setup.

Things I would like to be able to do, that I can't do in my current setup: Graphics editing at high resolutions, streaming videos at 720p or higher, video editing, composing audio with many tracks, recording audio with audio playback in audacity. Also, I'd most likely be using KDE with a few desktop effects.

I'm planning on building a system that uses AMD's new A8-3850, 2.9GHz  which includes an integrated 6550D processor. I've read a few reviews about it, but most just talk about gaming with it, which I won't be doing on a large scale. Thanks for reading, and once again, sorry if anything here sounds really stupid. I'll provide more information as requested.

EDIT: So I've built the system a while ago, and I'm now running Linux Mint 12 (Lisa) 64-bit. I'm having a few problems, and I believe that most of them are related to the drivers I'm using. They could really be anything though. If the details of these smaller problems are important, I'll be sure to provide the information.

I've been trying to improve some stability on my setup by using the proprietary drivers, but none of them seem to work. I've used the jockey-gtk application to install the drivers from the repositories. I've also tried to manually install the drivers from AMD's website. Regardless of the method, I end up with a system that runs fine, but crashes within the first minute of usage.

Is there anything that could help, or would it be better just to stick with the open-source drivers?
The driver problem completely doesn't surprise me. I have an AMD APU running on this laptop and it only partially works. You should have done your research and instead bought a processor that doesn't require the use of fiddly AMD graphics drivers to use. I'm afraid the only thing I can recommend is to return your computer, or install a more compatible OS.

EDIT:@mips completely agree. It's not that I don't like AMD hardware, but one must do their research before buying! If desktops it is we're talking about, a system with a small Intel motherboard, maybe an energy-efficient I5 or FX4100 with an nVidia GPU like the Gt430 would have been a better choice. Also, Hybrid drives if you can't get SSD.

---

### Post by mips on 2012-03-15
> **greg.9 said:**
> Not very helpful, is it. Hope your 6539 other beans were more constructive.
My last system had lots more problems with nvidia and Nouveau drivers than I have had with Llano and ATI?


I think this is where I'm gonna cash in my chips on this forum and tell you to go do whatever they say in the movies to go to yourself.

So long and thanks for all the fish all you gentle people ;)

Live long and prosper!

---

### Post by mips on 2012-03-15
> **greg.9 said:**
> Not very helpful, is it. Hope your 6539 other beans were more constructive.
My last system had lots more problems with nvidia and Nouveau drivers than I have had with Llano and ATI?



It reminds me though of a problem I read somewhere else of motherboard onboard graphics needing to be disabled in BIOS to get ATI driver to work.
Doubt your FM1 board has onboard but worth checking.

Not very often that I do this but your wish is granted ;)
[http://ubuntuforums.org/showthread.php?p=11768528](http://ubuntuforums.org/showthread.php?p=11768528)

---

### Post by Giraffemonster on 2012-03-15
> **kosme15 said:**
> I used to have a lot of problems with the fglrx driver not installing properly and even when it did install, not working the way it should.  And this is with a good old HD4650 card -- they've been around a long time and should be well supported.  Things started working for me, when I followed this guide:  [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)  

Two thing in particular that I learned from this guide are, first, never to run the installer directly.  Always create a .deb package and install it from the command line.  And second, the importance of calling aticonfig with proper command line options after installing the .deb files cannot be overestimated.  All this is described in detail in the above guide.  I used to have lots of headache with fglrx, but not anymore.  I hope this helps.

So I looked at that guide, and tried it again. It required a few different packages, a few different steps too. I got the same result though. It kinda-worked, but crashes soon. At least the crashes occurred in 1-2 minutes rather than less than one minute this time.

Ended up reinstalling because the fglrx package couldn't be removed. My Linux Mint disc for some reason refuses to install, but thankfully, I have a 64-bit Fedora disc with me. I'm posting this from Konqueror while it installs (One feature I like in most distos). Oh well, I guess that's that. I'll be fine with the open-source drivers. They worked well.

I'm also aware that I should have done some more research. You guys are right, but it's too late I guess. Not going to get a graphics card because I'll be fine without the drivers. About getting an nVidia card though, doesn't AMD have better driver support than nVidia? At least, that's what I've heard. Maybe it just doesn't apply to this case?

Going to mark this as solved though, not much more to be said here. Thanks for the help and info though, I'll be sure to put more effort into research in whatever my next purchase is.

---

### Post by 0011235813 on 2012-03-16
> **Giraffemonster said:**
> So I looked at that guide, and tried it again. It required a few different packages, a few different steps too. I got the same result though. It kinda-worked, but crashes soon. At least the crashes occurred in 1-2 minutes rather than less than one minute this time.

Ended up reinstalling because the fglrx package couldn't be removed. My Linux Mint disc for some reason refuses to install, but thankfully, I have a 64-bit Fedora disc with me. I'm posting this from Konqueror while it installs (One feature I like in most distos). Oh well, I guess that's that. I'll be fine with the open-source drivers. They worked well.

I'm also aware that I should have done some more research. You guys are right, but it's too late I guess. Not going to get a graphics card because I'll be fine without the drivers. About getting an nVidia card though, doesn't AMD have better driver support than nVidia? At least, that's what I've heard. Maybe it just doesn't apply to this case?

Going to mark this as solved though, not much more to be said here. Thanks for the help and info though, I'll be sure to put more effort into research in whatever my next purchase is.

In response to your last question, this is an issue that so often gets people muddled up. It's not nVidia who are keeping their drivers closed source, it's AMD, especially since nVidia chips have better support for the superior OpenGL game engine than AMD. It's strange, you'd think a company dedicated to giving you a performance computer for less money than an Intel one would go mad and support a free OS and a open-source game engine as much as possible, but apparently not. Maybe you-know-how is giving the fringe company some ca$h to support their OS?

---

