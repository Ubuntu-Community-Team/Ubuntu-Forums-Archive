---
title: "Is anyone using Ubuntu for Audio purposes?"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by steve k on 2005-09-23
Hi,
So I've been using Ubuntu for a while now, mainly for it's amazingly stable desktop and because it's so easy to install...

anyway, I do lots of recording on my Windows PC and I work with audio for part of almost every day.  I've been dying to move over to using Linux for everything, yet I've had little luck getting audio things going on Ubuntu.

Often there are conflicts with the sound server or other such things.  
On top of that I'm almost totally confused by Jack and how it can or should be working with Gnome and the rest of my audio applications.  Also, since updating to Breezy I can't even get Jackd working. 

That said, there's lots of neat software for linux users to use, PD, FreeWheeling, Sweep...If i could get things working I feel like i could make some pretty neat music with that stuff.

yeah, so any advice would be totally welcome!

---

### Post by KingBahamut on 2005-09-23
Recommended list of audio apps

Rezound - [http://rezound.sourceforge.net/](http://rezound.sourceforge.net/)
RoseGarden - [http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)
Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
TerminatorX - [http://www.terminatorx.org/](http://www.terminatorx.org/)
Muse - [http://muse.serverkommune.de/](http://muse.serverkommune.de/)
mp4live - [http://mpeg4ip.sourceforge.net/](http://mpeg4ip.sourceforge.net/)
gdam - [http://gdam.ffem.org/](http://gdam.ffem.org/)
cinerella - [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)
soundtracker - [http://www.soundtracker.org/](http://www.soundtracker.org/)

---

### Post by uc50_ic4more on 2005-09-23
steve k -

For whatever this is worth, I use Vegas Video, Nuendo, Adobe InDesign and Flash to do multimedia work, and I have found nothing close to these apps in Linux (keeping me tethered to Windows); although there are perhaps *workable* equivalents: Cinelerra, Ardour and Scribus seem to be the standards.

---

### Post by steve k on 2005-09-24
[QUOTE=KingBahamut]Recommended list of audio apps

Rezound - [http://rezound.sourceforge.net/](http://rezound.sourceforge.net/)
RoseGarden - [http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)
Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
TerminatorX - [http://www.terminatorx.org/](http://www.terminatorx.org/)
Muse - [http://muse.serverkommune.de/](http://muse.serverkommune.de/)
mp4live - [http://mpeg4ip.sourceforge.net/](http://mpeg4ip.sourceforge.net/)
gdam - [http://gdam.ffem.org/](http://gdam.ffem.org/)
cinerella - [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)
soundtracker - [http://www.soundtracker.org/](http://www.soundtracker.org/)[/QUOTE]
 see,
my problem is that it's hard to get these things to work properly in ubuntu.
I keep finding conflicts where the audio software, audacity or PureData or what have you, are telling me that they can't access the audio layer unless I go and shut off Gnome's sound server, which seems a bit ridiculous to  me, it's not the worst thing in the world, but there's got to be a better way of making it work.   lots of interesting Linux Audio software, especially for live performance relies heavily on the Jack Toolkit and that's something that I've never been able to quite figure out...does anyone know how to make things like Audacity, Pure Data and Free Wheeling work cleanly, simply and such under Ubuntu?

and yeah: the way things look I might have to rely on Nuendo on my old Windows PC for a while yet, no one's written drivers for my pro-soundcard yet (as far as I can tell).

---

### Post by uc50_ic4more on 2005-09-24
Steve -

Which sound card are you using? For what it's worth, the RME Hammerfall series is well supported (and can be had these days for <$150USD, enabling you to work with some very, very capable converters and clocks...), but most of the (more) proprietary format cards will not work. What looks somewhat promising is the increasing number of mid and high grade converters coming out with IEEE1394; but for now it looks like folks like us need to support FOSS in the ways we can, and "hurry up and wait" for better media production tools.

---

### Post by MetalMusicAddict on 2005-09-24
I **really** wanted to use Ardour but never could get it to work well in Ubuntu. So I dual boot with [Agnula](http://www.agnula.org/) more specificly their Demudi (Debian based) version.

Works really well. Still learnin it. Im comming from a pro-tools point of view and a beginning understanding of linux.

Cant wait till my 2 Dell 20" widescreen monitors come in. ;)

---

### Post by steve k on 2005-09-24
I'm using a MOTU sound card for most of my recording, 
however, since I'm kind of committed to working with Ableton and Nuendo for the next little while I'm not so concerned with the MOTU card, but more with getting things going on my Thinkpad X40.  I go on tour sometimes and it'd be great to be able to work on things with headphones or do little improv sets with PD or something while I'm sitting still in the back of a car or van for another 3 hours or so...
So i'm super concerned with getting my thinkpad soundcard to co-operate with other stuff...

is there any really nice walk through for using Jack? it seems like every time I try and spend some time on Linux audio it all comes back to Jack.  

I also tried to dual boot with Agnula on (yet another) computer but Agnula failed to load properly, it couldn't find the CD-Rom that it had booted off of or something...It was a while ago, and since it wasn't working i just pulled the plug on that installation.  

I'd like to make more audio stuff work in Ubuntu, just from a personal satisfaction perspective.  so as to say "i did it".

---

### Post by MetalMusicAddict on 2005-09-24
[QUOTE=steve k]I'd like to make more audio stuff work in Ubuntu, just from a personal satisfaction perspective.  so as to say "i did it".[/QUOTE]
I wanted to also till I heard that the Kernel used in Ubuntu wasnt good for recording. I forget the exact term that was used but thats the jist. Im still learning.

---

### Post by dolson on 2005-09-24
I used Ubuntu to record a song... If you would like to hear it, I'll warn you up front that it's a song taken out of the Bible, but it gives you an idea of what Ubuntu + Audacity is capable of: [http://rivironline.com/files/rivir-psalm117.ogg](http://rivironline.com/files/rivir-psalm117.ogg) or [http://rivironline.com/files/rivir-psalm117.mp3](http://rivironline.com/files/rivir-psalm117.mp3)

I'm pretty happy with the final sound quality of that track.

Audacity works great for me, I've been using it for years, and currently in Breezy it works fine too. My sound card is an Audigy 2 ZS, using ALSA. I didn't have to change my gnome stuff, all my sounds still work fine. I'm currently building the CVS version of Audacity as well, so if you would like to try a deb of it I can give it to you. Email me at [email]adolson@gmail.com[/email] or PM me on this board, and I'll give you a link. (I'm assuming that the build is possible, it's still going).

---

### Post by Perfect Storm on 2005-09-24
Nice Dolson  :)

By the way: Nice to see ya again  :grin:

---

### Post by BoyOfDestiny on 2005-09-25
[QUOTE=steve k]Hi,
So I've been using Ubuntu for a while now, mainly for it's amazingly stable desktop and because it's so easy to install...

anyway, I do lots of recording on my Windows PC and I work with audio for part of almost every day.  I've been dying to move over to using Linux for everything, yet I've had little luck getting audio things going on Ubuntu.

Often there are conflicts with the sound server or other such things.  
On top of that I'm almost totally confused by Jack and how it can or should be working with Gnome and the rest of my audio applications.  Also, since updating to Breezy I can't even get Jackd working. 

That said, there's lots of neat software for linux users to use, PD, FreeWheeling, Sweep...If i could get things working I feel like i could make some pretty neat music with that stuff.

yeah, so any advice would be totally welcome![/QUOTE]

Ah, welcome to my arch enemy in Ubuntu, it's called ESD (enlightened sound daemon). I'm glad to say none of my comps need it... open up a terminal and type "sudo killall esd", now run whatever app was having trouble accessing a layer...now it won't I hope :)

Anyway, I can get multiple sounds using ALSA, without ESD there are no gnome system sounds (which I didn't want anyway). The bonus is no lag, and no audio problems any more. 

If you want to keep it as is, go to System -> preferences (going from memory here) and choose sound, uncheck start sound server. Then go to multimedia selector and choose ALSA. Last thing, is I recommend downloading a package called libsdldebian-all (or something close), and your sdl games/apps should have no problem at all with sound.

As for audio purposes, I can say I get excellent sound from my dos, snes, nes, and arcade games =) And from beep.

---

### Post by dolson on 2005-09-29
I don't understand why I can't disable esd and still have sounds in Gnome... ie: specify a play command to play Ogg, WAV, or whatever it is they use. That would be NICE. Then us people with modern sound cards can ditch the crap sound servers and just use the drivers.

---

### Post by 23meg on 2005-09-29
has anyone had success with installing the patched AGNULA kernel (2.6.11-multimedia) and audio apps from the AGNULA repositories on top of ubuntu?

---

### Post by dolson on 2005-09-29
[QUOTE=23meg]has anyone had success with installing the patched AGNULA kernel (2.6.11-multimedia) and audio apps from the AGNULA repositories on top of ubuntu?[/QUOTE]

What's so good about that kernel? I could always just get the source and recompile it, it's really pretty simple. Maybe I'll look at that, and I could make an unofficial deb for Ubuntu, if anyone wants it.

---

### Post by MetalMusicAddict on 2005-09-30
[QUOTE=dolson]What's so good about that kernel? I could always just get the source and recompile it, it's really pretty simple. Maybe I'll look at that, and I could make an unofficial deb for Ubuntu, if anyone wants it.[/QUOTE]
Its compiled to be a low-latency kernel. Its important when doing things like multi-track recording.
Does anyone here use M-Audio cards? Im looking at [THIS]("http://www.m-audio.com/products/en_us/Audiophile2496-main.html") one. Ide like to buy 2 or 3. Maybe 4 so I can do 16 track recording. Ide have to build a good patch-bay. :)

---

### Post by Paulus on 2005-09-30
yeah, i use M-audio delta 10/10.,  can anyone show me some screenshots of these suggested harddisk recording programs?

do they support VST plugins?   maybe  have audio instruments? ex24?

I have not used a better program than logic audio; no linux client tho :(

shame really, it's going strong on the mac

---

### Post by acidvertigo on 2005-09-30
I know that the latest live cd iso image of Agnula is based on ubuntu... but i don't know what kernel use.

I think that is possible to install the packages from the live cd with synaptic.

Anyone have tried it?

---

### Post by MetalMusicAddict on 2005-09-30
[Ardour]("http://ardour.org/")
[b][INDENT][i][COLOR="Black"]"Ardour is a digital audio workstation. You can use it to record, edit and mix multi-track audio. Produce your own CD's. Mix video soundtracks. Experiment with new ideas about music and sound. Generate sound installations for 12 speaker gallery shows. Have Fun.
Ardour capabilities include: multichannel recording, non-linear, non-destructive region based editing with unlimited undo/redo, full automation support, a mixer whose capabilities rival high end hardware consoles, lots of plugins to warp, shift and shape your music, and controllable from hardware control surfaces at the same time as it syncs to timecode. If you've been looking for a tool similar to ProTools, Nuendo, Cubase SX, Digital Performer, Samplitude or Sequoia, you might have found it.[/COLOR][/i][/INDENT][/b]
[img]http://ardour.org/img/main-screenshot-small.png[/img]
[FULLSIZE]("http://ardour.org/img/main-screenshot-big.png")

@ Paulus:
***"For high-end use, the RME Hammerfall series and the M-Audio Delta series are both recommended choices."***
From the suggested [requirements]("http://ardour.org/requirements.php").

---

### Post by Paulus on 2005-09-30
^ Thanks!!

i'll give this a go!

though in my opinion, some open source programs simply won't be better than professional applications.  We can only hope linux continues to improve to attract attention from people like emagic and adobe.

---

### Post by dolson on 2005-09-30
[QUOTE=Paulus]^ Thanks!!

i'll give this a go!

though in my opinion, some open source programs simply won't be better than professional applications.  We can only hope linux continues to improve to attract attention from people like emagic and adobe.[/QUOTE]

You could also pay a donation to open source groups/companies to help them along - Logic Audio, is that free? I'm guessing no, so why would you expect that volunteer coders can create something as good for free? There is only so much time in a day that you can use up without being compensated for.

I use Audacity, and it does all I need for multitrack recording. As far as I know there are no VST plugins, but LADSPA. Steve Harris has a good plugin package... It's all in Ubuntu too. And the dev version of Audacity is looking pretty cool, with some great new features. It's not aiming to take on the world like Ardour is, but for me at least, Audacity works out of the box on every distro I've used it to record with - Debian, Ubuntu, Mandrake...

Here's a screenshot of one of my projects:
[http://aslan.homelinux.com/dana/images/rivir-worldtrap.jpg](http://aslan.homelinux.com/dana/images/rivir-worldtrap.jpg)

---

### Post by 23meg on 2005-09-30
[QUOTE=MetalMusicAddict]Its compiled to be a low-latency kernel. Its important when doing things like multi-track recording.
Does anyone here use M-Audio cards? Im looking at [THIS]("http://www.m-audio.com/products/en_us/Audiophile2496-main.html") one. Ide like to buy 2 or 3. Maybe 4 so I can do 16 track recording. Ide have to build a good patch-bay. :)[/QUOTE]

i have an M-Audio Quattro which i'm satisfied with, but i haven't yet got it working with JACK. i've read some success stories though, so it's definitely possible, but i haven't found the time to make it real yet.

if you'd like to record that many channels at once you should consider a single interface with 16 or more channels rather than 4 interfaces with 4 channels each. multiple cards are always a royal pain to manage. also you need quite a fast HD if you'll be recording 16 channels and playing back at least two (probably more since you'll need separate monitoring for multiple musicians?).

dolson: i'd be interested in a 2.6.12 / 13 kernel package that's patched with the task preemption patch (from Ingo Molnar i guess). and i'm sure it would be handy for lots of people who don't have the time or knowledge to do it themselves.

---

### Post by MetalMusicAddict on 2005-09-30
Audacity is great dont get me wrong. I just think people comming say from a Pro-Tools background are looking for something like that expierence. :)

Im looking to build a 16-track, mobile (road case) project studio. Something I can fit in a nice size road case. Its gonna be a several thousand dollar investment. When looking around (for me) Ardour fit the bill. I do love Audacity and use it on my laptop for recording. If after I get all my info together and find that Agnula will work well I plan on donating regularly. With as little as I have played with Ardour I can still tell a *GREAT* deal of work has gone into it.

Now I just gotta see if Ardour supports USB DAW controllers now. Didnt last year. ;)

---

### Post by 23meg on 2005-09-30
AGNULA based on Ubuntu? are you sure? it used to have Debian and Red Hat based versions but i haven't heard of any plans to make an Ubuntu based one.

[QUOTE=Paulus]though in my opinion, some open source programs simply won't be better than professional applications. We can only hope linux continues to improve to attract attention from people like emagic and adobe.[/QUOTE]

this is like saying "Linux will never be as good as Windows so let's hope it gets Microsoft's attention". we don't have to beg for the attention of the proprietary software world; there are many examples of distributed open source development    developing much better applications than closed, proprietary development. if you want good audio software for Linux you can write it yourself, help people who write it, and encourage people to use it. you don't have to know about coding; you can help by testing, reporting bugs, designing interfaces, writing documentation, doing propaganda, or even by just using the software.

---

### Post by MetalMusicAddict on 2005-09-30
[QUOTE=23meg]AGNULA based on Ubuntu? are you sure? it used to have Debian and Red Hat based versions but i haven't heard of any plans to make an Ubuntu based one.[/QUOTE]
I looked for info on a Ubuntu based live cd but couldnt find any.
> this is like saying "Linux will never be as good as Windows so let's hope it gets Microsoft's attention". we don't have to beg for the attention of the proprietary software world; there are many examples of distributed open source development developing much better applications than closed, proprietary development. if you want good audio software for Linux you can write it yourself, help people who write it, and encourage people to use it. you don't have to know about coding; you can help by testing, reporting bugs, designing interfaces, writing documentation, doing propaganda, or even by just using the software.I figure the best way to support developers (if you cant code yourself) is by donating. If they cant get paid full-time I figure that donating is kind like saying "Thanx alot man. Can I buy ya a beer?" :)

---

### Post by primeirocrime on 2005-09-30
[quote=dolson]What's so good about that kernel? I could always just get the source and recompile it, it's really pretty simple. Maybe I'll look at that, and I could make an unofficial deb for Ubuntu, if anyone wants it.[/quote]


yep! I would like to try that, yes sir!

---

### Post by acidvertigo on 2005-10-05
This is the link for agnula ubuntu live cd: 

[http://demudi.agnula.org/images/1.2.1/demudi-live_1.2.1_i386.iso]("http://demudi.agnula.org/images/1.2.1/demudi-live_1.2.1_i386.iso")

:eek:

---

### Post by MetalMusicAddict on 2005-10-05
[QUOTE=acidvertigo]This is the link for agnula ubuntu live cd: 
[http://demudi.agnula.org/images/1.2.1/demudi-live_1.2.1_i386.iso]("http://demudi.agnula.org/images/1.2.1/demudi-live_1.2.1_i386.iso")
:eek:[/QUOTE]
Do you have a link that talks about it being based on Ubuntu?

---

### Post by dolson on 2005-10-05
[QUOTE=MetalMusicAddict]Audacity is great dont get me wrong. I just think people comming say from a Pro-Tools background are looking for something like that expierence. :)

Im looking to build a 16-track, mobile (road case) project studio. Something I can fit in a nice size road case. Its gonna be a several thousand dollar investment. When looking around (for me) Ardour fit the bill. I do love Audacity and use it on my laptop for recording. If after I get all my info together and find that Agnula will work well I plan on donating regularly. With as little as I have played with Ardour I can still tell a *GREAT* deal of work has gone into it.

Now I just gotta see if Ardour supports USB DAW controllers now. Didnt last year. ;)[/QUOTE]

Yup, Ardour is probably great. I have it on my list of things to try again, but the last time I tried it, it was more than I needed, and wasn't immediately intuitive. I was just putting up Audacity as an alternative, and it is in use currently by yours truly. Just got my ocarinas in, so I'll probably be inspired to record a new song with it too. :)

---

### Post by acidvertigo on 2005-10-06
[QUOTE=MetalMusicAddict]Do you have a link that talks about it being based on Ubuntu?[/QUOTE]


[http://distrowatch.com/?newsid=02337#0]("http://distrowatch.com/?newsid=02337#0") :razz:

The link and the name of the iso is changed

---

### Post by MetalMusicAddict on 2005-10-06
If you want, here are the repos for Demudi. I havnt tried them for Ubuntu. If you have Debian they do work.

```
 # A/DeMuDi stable
deb http://demudi.agnula.org/packages/demudi stable main
# A/DeMuDi development
deb http://demudi.agnula.org/packages/demudi testing main
```

Taken from [THIS]("http://demudi.agnula.org/wiki/InstallApt") page.

---

### Post by 23meg on 2005-10-06
alright, i can't wait until Breezy goes final, and i can risk messing this beta installation anyway, so i'm adding the DeMuDi repos and apt-getting the kernel and a few apps. i'll report how it went.

---

### Post by darkstar5680 on 2005-10-08
any luck with the kernel and apps install, 23meg?

---

### Post by joshpelkey on 2005-10-13
I'm new to home recording, and I have a simple question.  How do you get the sounds of you intruments to your software like Ardour.  I want to do simple home recording, kind of a one-man band deal.  I've seen people use products like the M-box to interface their instruments and computer, but I assume these devices may not be supported in Linux.  I'm really excited about getting started into this, so any help is great!

If the simple answer to this question is use some good pre-amps and a solid soundcard, I should also ask, will this give good quality recording?  Also, it is possible that you could have too many outputs for you sound card to handle.  Does using a mixing board to mix all these signal first degrade the quality?  Sorry this is a little less specific to Linux and Ubuntu, but I figure somebody here knows the answer to my questions.

---

### Post by dolson on 2005-10-14
[QUOTE=joshpelkey]I'm new to home recording, and I have a simple question.  How do you get the sounds of you intruments to your software like Ardour.  I want to do simple home recording, kind of a one-man band deal.  I've seen people use products like the M-box to interface their instruments and computer, but I assume these devices may not be supported in Linux.  I'm really excited about getting started into this, so any help is great!

If the simple answer to this question is use some good pre-amps and a solid soundcard, I should also ask, will this give good quality recording?  Also, it is possible that you could have too many outputs for you sound card to handle.  Does using a mixing board to mix all these signal first degrade the quality?  Sorry this is a little less specific to Linux and Ubuntu, but I figure somebody here knows the answer to my questions.[/QUOTE]

I was advised to get a pre-amp, but I went to the store, and I saw a 10-channel mixer for cheap (or at least in my opinion, it's not unreasonable for a quality Yamaha piece of hardware at under $100CDN). It REALLY helps improve the sound quality! You can cut the frequencies you don't need, which helps make room in your mix for the other instruments. It's great. You can improve your sound so much just by learning what frequencies you don't need, and cut them on the way in.

If you do a lot of guitar, I really recommend you get a Line6 POD. I got mine on eBay, and while it was $199, it was well worth it. You can get any amp sound out of it, and lots of gain controls, and it's awesome. Best guitar-home-recording investment EVER.

If you do acoustic guitar, get an acoustic-electric. Micing works, but it's not as clear and clean. Depends what sound you want though. Again, I got an Applause by Ovation guitar, and it was $199 as well. Very nice sound, especially through the Line6 POD.

I record using Audacity, but I'm going to look at Ardour I think, just to see how it is. It's more advanced, and I've heard it's faster at performing filters, but I really like Audacity. It's, at the very least, a great place to start.

The sound card I currently use is an Audigy2 ZS with ALSA as detected in Ubuntu. I don't really like how it mixes analog inputs, but it still sounds great. Previously I was using an SB Live! 5.1, and that was great too. I don't recommend the standard SB Live! cards though, only the 5.1 or Audigys. The mixer -10dBV output is plugged in to the Line In on the sound card, and it works perfectly.

My mixer is a Yamaha MG10/2 mixer, and I have a picture of my setup on my website, [www.rivironline.com](www.rivironline.com). All of my gear is listed on my site too, on the About page.

If you do electronic music, like I have, you should always record your analog gear one track at a time, and line the tracks up using a common 'click' sound at the begining. The reason is that you can cut frequencies you don't need, and the sound is much fuller in the end result. I used to make a ton of newbie mistakes like that, recording multiple tracks at a time from an RM1x sequencer... Bad idea.

---

### Post by joshpelkey on 2005-10-17
Thank you much for such an informative post!  Whenever I get some time and money set aside, I'll be taking your advice.  Most likely I'll look into buying a mixer first.  We have an excellent music store close to where I live, and I can probably check out the POD that you suggested.  Thanks again.

---

### Post by dolson on 2005-10-17
[QUOTE=joshpelkey]Thank you much for such an informative post!  Whenever I get some time and money set aside, I'll be taking your advice.  Most likely I'll look into buying a mixer first.  We have an excellent music store close to where I live, and I can probably check out the POD that you suggested.  Thanks again.[/QUOTE]

No problem. The POD 2.0 series may not be available new anymore, but the XT series is newer and more versatile (and more expensive!).

Pretty much any mixer will do, just try to get one with at least +/-15dB for the EQ knobs (high, mid, and low at least recommended). My mixer has basically 6 inputs (4 of them are stereo, so that comes out to 10 channels) and I find it sometimes limiting, as far as keeping each channel for something specific goes (one for guitar, one for bass, one for drums, one for a sequencer, and three for vocals (myself, my wife, and a friend for another band)).

Anyhow, let me know what stuff you buy, and if you need more advice, let me know.

---

### Post by Jan Krey on 2006-06-29
M-box drivers will they ever come for Ubuntu???

CUrrently I have to partition my hardisk into an windows XP audiodedicated partiotion and an Ubuntu everything-else-dedicated partition.

I am using iPod, M-box usb card, and software witch exceeds linux software in usability (except PURE DATA of course witch is essential for programmers/musicators...

If M-box drivers ever get supported, Im all linux!!!!!!!!!!!!!!!!!!!!

---

