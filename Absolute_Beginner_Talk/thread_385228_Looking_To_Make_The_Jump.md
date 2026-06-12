---
title: "Looking To Make The Jump"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by nullfactor on 2007-03-15
I just received my brand spanking new computer with hardware specs that I figured would make my job of an electronic musician who relies on his computer for writing and recording music a snap.  The computer came pre-loaded with the new Windows Vista.  As it turns out, my studio software is not compatible with the new Windows OS.  I have a very powerful computer that is good for web surfing, only.  How sad.

My web surfing brought me to this site.  When reading about Ubuntu, I became so excited that I literally have a lump in my throat.  I've used Linux in the past, but this seems different and very fresh.  I'm thrilled!

My question is, are there any packages out there, preferrably for free, that can be used for writing music (soft synths, sequencers, etc.) and for recording music (multi-track recorders in the likes of Audition) that works on Linux.  More specifically, Ubuntu?

Any help would be appreciated!  Thanks to all of you.

+null factor

---

### Post by lamalex on 2007-03-15
Coming in april - [http://ubuntustudio.org/](http://ubuntustudio.org/) if you're into music editing, you should need new panties right about now.

for right now, I hear good things about Audacity.

---

### Post by nullfactor on 2007-03-15
I think that lump in my throat just got bigger.  I may be able to get rid of the Corporate OS Burden, completely!!!

Please pardon me while I make a quick change of skivvies...

---

### Post by lamalex on 2007-03-15
no worries no worries, Ubuntu has caused me to make quite a few stains on my sheets.:popcorn:

---

### Post by arochester on 2007-03-15
As a start look at something like "Permaculture Musicians" at [http://www.permaculturemusicians.co.uk/linux.htm](http://www.permaculturemusicians.co.uk/linux.htm) 

The Agnula Project is now at [http://www.agnula.info/](http://www.agnula.info/)

Dynebolic is worth a look, as is Studio to Go.

---

### Post by nullfactor on 2007-03-15
I will go there, now.  It's good to see that there are, indeed, alternatives to expen$ive $oftware.  Life is starting to look pretty good, right about now.  New sources of creativity are just a download away...:guitar:

---

### Post by old_geekster on 2007-03-15
> **nullfactor said:**
> I will go there, now.  It's good to see that there are, indeed, alternatives to expen$ive $oftware.  Life is starting to look pretty good, right about now.  New sources of creativity are just a download away...:guitar:
Ya know, if I were you, I might wait until Feisty (Ubuntu) 7.04 is released in April.  This would save you from having to do an update.

I installed Edgy three weeks ago and just got it running the way I like.  Now, since Feisty comes so highly recommended, I wll upgrade as soon as I can download it.

From what I have read, the purpose for which you want to use your rig will suit Feisty perfectly.

---

### Post by damu on 2007-03-15
The only good solution that I know of which:
- works out of the box 
- is complete (systems, apps, realtime, VST support)
is the coming [studio-to-go]("http://www.studio-to-go.com/") 2.0.
The 3rd beta has just been released, so it is not far from the final release.
Why do I say it is the 'only' solution :

- it is the only one working out of the box fully with jackdmp. Some other audio-distro (64Studio, Jacklab) think about it. Others just avoided this subject (Ubuntustudio). A dual core machine without jackdmp will mostly use one core = unefficient, back to Cubase and others few years ago on Win and MAC computers. Even on one core, jackdmp will improve performances in different ways.

-it comes with VST support as standalone and in Rosegarden . 
Due to licensing, VST is not supported in Ardour. It is still a big drawback : Ardour is 'the' platform for multi track recording, and mostly final mix with automation. VST support in Ardour (which works absolutely fine once compiled) is the only way to get some functionalities and state of the art plug-ins (SIR reverbs, dynamics come to mind). Studio-to-go is still the best way to go so far on this subject too. You can use you VST synthetisers  and effects as standalone and in Rosegarden, and you might be just fine for your mix in Ardour with the 300 or so ladpsa plugins available.

- compatible now with debian etch, easy to complete with synaptic if installed on HD. It comes as a live-cd, which is just great if you work with other musicians. You just bring your STG live-cd and your external HD with your audio files, and off you go...impressive!

- qjadeo. Loads of music, soundtracks are produced for either movies, cartoons, 3D animations,etc. So, having a video sync to audio is quite essential. That's what qjadeo provides, again, out of the box in STG. Just click on qjadeo, select your video, and here you go with your video synced to Ardour or Rosegarden through jack. Here again, it seems this is something which didn't seem to be relevant during the Ubunstudio think tank, even though it targets "middle to experienced users" which therefore would definitely look for this kind of feature.


So, my 2 cents are that you can wait for Ubuntustudio (I will obviously give it a try, but am for now quite skeptical on the relevance of the choices which have been made in the overall design of it...nice black theme though...) or try other free distros like 64Studio, Musix , Dynebolic, but if you really want to produce audio, then just get a live-cd of STG 2.0.

For now , you can download the free demo STG 1.5, but there is really a giant step in between 1.5 and 2.0, so I would wait for the final release of 2.0 to consider a purchase (£50). The core developers are also developers of some of some apps that you will use (Rosegarden, DSSI, etc) which obviously give a serious touch of professionalism to the support you get on STG forums...

Don't get me wrong : I work on Ubuntu 8 hours a day, I love it, and there is no way I would change it for anything else, for my day-today work. But STG for audio prod seems to be far beyond anything else for audio-prod on linux.

---

### Post by nullfactor on 2007-03-15
OLD-GEEKSTER - Thanks for the tip.  Seems worth the wait.  Nothing worse than getting a system performing how you want it only to have to revamp.  So, wait I shall.

---

### Post by nullfactor on 2007-03-15
DAMU - Interesting.  I'll do some research on STG.  Is STG a complete package (a shaped distro of Linux with all apps required bundled) like the Ubuntu Studio is?  That would be very convenient.  What I would like to avoid is having to build the whole thing, ground-up.  I want to install and go.  Though I am willing to do a bit of work to get it to perform properly...

---

### Post by damu on 2007-03-15
STG is a live-cd, which means that :

-you download the .iso file
-burn the .iso file on a cd 
- restart your computer with the cd that you just burnt in your cd/dvd drive.
- that's it. It will boot from the cd on STG. Within 5 mins, you have a ready to go system, alike any other live-cd (ubuntu, etc), except that this one is ready for audio production with all the apps for audio at your fingertips.

You can off course install it on hard drive if you want to. That's what I have been doing so far with STG 1.5. This way, I could benefit of some upgrades of few softwares.

I am not sure I will install on HD for STG 2.0. Booting from the live-cd is quite fast, and except the time it takes to load an app(longer from the cd), once loaded, I don't really feel the difference in terms of performances. With my vsts, soundfonts, sample library and audio projects on a firewire/usb2 external HD, and an RME soundcard with a cardbus connection, I can work either on my desktop (dual core with 2 Go Ram) for solid mix/mastering sessions, or with any laptop anywhere for live-recording sessions!

---

### Post by nullfactor on 2007-03-17
That sounds like the perfect solution.  The only thing that might stop me from getting this is the $98 US price tag.  Small price to pay, considering, but still a large sum for a man with a family of 5! :)

I think my plan of attack is - give Ubuntustudio a chance.  If it doesn't live up to my needs, take the plung and get the STG 2.0 package, as I WILL need VST support... that is a must.

Go with the free, and if free doesn't work, shell out a few clams.  Either way, it'll run circles around Vista. :(

---

### Post by bodhi.zazen on 2007-03-17
Have you looked at Musix :

> The Musix Project is proud to announce the release of Musix GNU+Linux 0.99, a new version of the 100% Free Software multimedia operating system for artists and general users. This is the most stable and user-friendly version until now. Since version 0.79, Musix GNU+Linux is focused on multimedia content creation and especially on music, that is: music production, audio and video editing, 3D animation, graphic design, image editing and web design. Hundreds of software packages have been updated to the Debian Etch versions. New additions include the midi sequencer Muse and the sequencer and synthesizer SpiralSynthModular.

[http://www.musix.org.ar/en/index.html](http://www.musix.org.ar/en/index.html)

Cool web site ;)

Also you may want to check out Dyne:Bolic :

> dyne:bolic is shaped on the needs of media activists, artists and creatives as a practical tool for multimedia production: you can manipulate and broadcast both sound and video with tools to record, edit, encode and stream, having automatically recognized most device and peripherals: audio, video, TV, network cards, firewire, usb and more; all using only free software!

[http://www.dynebolic.org/](http://www.dynebolic.org/)

Also very cool ...

---

### Post by damu on 2007-03-17
Musix and Dynebolic are indeed nice projects. Dynebolic has a few audio apps, but is overall more multimedia than audio orientated.

Musix is nice. It is the one I give to students and kids when I give a musical workshops...it comes as a live-cd and is for now the easiest free solution to offer as a first step in the linux-audio world.

It doesn't play in the same league as STG though. And Ubuntustudio will probably be way more polished too.

There are some nice things in Musix, but it has many drawbacks too : an older kernel, a mix-up of  english and spanish in the menus and apps, no VST support, no video post-sync , etc.
STG 2.0 is also so far the only distro which mounts properly my RME multiface (even feisty doesn't seem to make it...)! 

So it depends very much of what are your needs. If you want to play a bit with audio, have fun recording few tracks at home, or record your own band, ubuntustudio, jacklab, 64studio, musix will make it.
If you intend to build a DAW with dual core, vst , etc, so far STG is the only solution available, and even this one still lack the support of VST in Ardour (it has VST support in standalone and Rosegarden, which I don't consider as enough for a 'pro' solution).

Enjoy!

---

### Post by bodhi.zazen on 2007-03-17
damu : thanks for the info

I guess I am guilty of not reading the whole thread before I posted, but wanted to make a few suggestions. :redface:

Nice link, BTW, I was not aware of STG ;)

---

### Post by nullfactor on 2007-03-17
DAMU - Again - awesome!  So many things to check out before I make my jump.  I think my biggest concern (and the reason why I'm a little apprehensive about shelling out some $$$ on software) is hardware compatibility.  I've had some pretty difficult times in the past with Linux and audio.  Kind of defeats the whole purpose! :)  

All of these packages sound extremely promising, though.  I'm getting more stoked by the day.  Unfortunately, my computer is going to the repair depot, already (only had it a month)... the keyboard is a little messed up... :(  After I get it back, though... I have some serious software to mess around with!

---

### Post by nullfactor on 2007-03-17
bodhi.zazen -  Excellent suggestions.  I just read about Dyne:Bolic on another forum and it did catch my eye.  Yet another software package I might want to check out.  Hey, if it's free, what's the harm of downloading and trying, right? :)

Thanks!

---

### Post by damu on 2007-03-18
bodhi.zazen, I don't know if you remember, but you saved my day when I was blowing a fuse , trying to get my hands on IRC... :) 
I don't have the profile of a techie... But it happens that I've been working a bit in sound design and audio-prod so, obvioulsy , the subject of 'audio on linux' is quite hot for me ! :)

Your suggestions were indeed really interesting, as the spectrum of possibilities is quite large, and the good solution depends very much on the needs of each of us.

I wish the ubuntustudio project had kept a link to their potential user base (which was the point of the existing ubuntustudio forum before it was shut down). It has obviously an amazing potential, being based on one of the most solid and outstanding Linux distro. It benefits of loads of existing packages (most of the apps are already available in the repos) and will be based on the stock kernel, whereas all the audio linux distro needed to integrate real-time patches to the kernel before 2.6.20.

Knowing that they target 'middle to experienced users', I just don't get why they wouldn't integrate available and open source tools : 
- jackdmp is a bit tricky to integrate, but many managed to get it working with very few developers involved. Without it , you simply can't target experienced users , as for most of them they use dual-core machines, and loads of them will possibly use quad-core pretty soon if not already. For them, a DAW  which uses  only  one core for audio is a non-sens. It's like driving a sport car using just the first gear...

-dssi-vst has no licensing issue any more, so providing vst support shoudln't be a big deal, except for Ardour with fst. Again, without this feature, let's not talk of targeting 'experienced users'. None of my friends (sound engineers, musicians) would consider a DAW without this.

-xjadeo (and the front-end qjadeo) are available for debian. This simple app changes the scope of an audio-distro. Suddenly, as a musician , you can be part of any movie/multimedia/3D project.
Without it, forget it, as you don't have any other solution to produce audio synced to video.

I 

As you see , everything is linked...I needed to learn more about IRC, so that I could at one point express this view to the Ubuntustudio team  :)

---

