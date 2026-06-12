---
title: "Gnash, Flash, Youtube"
date: 2011-03-17
forum: Apple Hardware Users
---

### Post by canhoto on 2011-03-17
I read somewhere that Flash Player doesn't work with Ubuntu (or Linux) for PPC and it should be better to use Gnash. I installed Gnash (although I don't know where it is... is there a place where to find installed applications outside the "Applications" menu?).

But when trying to view an Youtube it says that I should have Flash 10 or more; I thought Gnash would automatically do the job. Any ideas?

---

### Post by cantormath on 2011-03-17
Have you tried installing flashplugin-nonfree from medibuntu repository?  Try to load the medibuntu repos and then try to install flashplugin-nonfree.

> **canhoto said:**
> I read somewhere that Flash Player doesn't work with Ubuntu (or Linux) for PPC and it should be better to use Gnash. I installed Gnash (although I don't know where it is... is there a place where to find installed applications outside the "Applications" menu?).

But when trying to view an Youtube it says that I should have Flash 10 or more; I thought Gnash would automatically do the job. Any ideas?

---

### Post by avtolle on 2011-03-18
> **cantormath said:**
> Have you tried installing flashplugin-nonfree from medibuntu repository?  Try to load the medibuntu repos and then try to install flashplugin-nonfree.

Don't waste your time with this suggestion, as there is no ppc flash for linux. Cantormath's suggestion works for intel-based macs, not power pc ones.

Gnash has come a long way, but it doesn't do well enough to play YouTube videos in place. For me, I've used the Download Helper add-on for Firefox, and in the process converted the video to a format that VLC (my favorite) can handle. Others will have their suggestions, and it's a matter of preference in most cases. Good luck.

---

### Post by oswaldkelso on 2011-03-19
Take you pick from the options shown here. I assume the same packages are in Ubuntu, 
[http://forums.debian.net/viewtopic.php?f=16&t=51504](http://forums.debian.net/viewtopic.php?f=16&t=51504)

---

### Post by cantormath on 2011-04-23
> **avtolle said:**
> Don't waste your time with this suggestion, as there is no ppc flash for linux. Cantormath's suggestion works for intel-based macs, not power pc ones.

True, there is no Adobe Flash for PowerPC Linux but there are two free open  source projects aiming to create a functional alternative, gnash and swfdec.  It is still good to use the medibuntu codecs, I believe medibuntu has ppc codecs.  

I wonder if the mozilla-plugin-vlc or totem-mozilla packages work with youtube for their mp4 content.

---

### Post by teachop on 2011-04-24
Having flawed flash options stops some websites from falling back to a functional non-flash alternative.  You just have broken.  For me it is better to go flash-free.  Probably depends what you are using the ppc for...

---

### Post by pauljwells on 2011-04-24
I installed gnash and mozilla-plugin-gnash from the ppc repos and mostly youtube works fine, even in-place.

You have to forget DRM stuff like BBC iPlayer though.

---

### Post by tiresia on 2011-04-26
Installing mozilla-plugin-gnash let me watch youtube videos on my PowerMac g5.

---

### Post by linuxftw3 on 2011-05-01
> **canhoto said:**
> I read somewhere that Flash Player doesn't work with Ubuntu (or Linux) for PPC and it should be better to use Gnash. I installed Gnash (although I don't know where it is... is there a place where to find installed applications outside the "Applications" menu?).

But when trying to view an Youtube it says that I should have Flash 10 or more; I thought Gnash would automatically do the job. Any ideas?


do you have gnash 0.8.9 installed ? i installed that on my eMac that i  put Xubuntu 11.04 on and it works great.  also install ubuntu-restricted-extras along with Gnash and that should
 do it for you .:D  also, DRM based flash content doesn't work with Gnash, so if your trying to watch BBC or something like that, it won't work.

---

### Post by mrethan on 2011-07-19
Hi, I am having a difficult time following the recommendations posted here to address the flash problems encountered by power pc users. I am using an ibook g4 power pc. I have Ubuntu 11.4 running on it and it works exceptionally well. However I cannot understand what I should do to watch a youtube video. Currently all I receive is a message indicating that I have to install flash. Can someone please post a very simple set of steps?

Thanks!
-e

---

### Post by rsavage on 2011-07-20
From the Ubuntu Software Centre install "Gnash SWF viewer" and "browser-plugin-gnash".  In ppc Natty, there seems to be a number of packages missing and this could be the case for browser-plugin-gnash.  So you may have to download it from here [http://ports.ubuntu.com/ubuntu-ports/pool/universe/g/gnash/browser-plugin-gnash_0.8.9-1ubuntu1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/universe/g/gnash/browser-plugin-gnash_0.8.9-1ubuntu1_powerpc.deb) and install it with the command "sudo dpkg -i path_to_file" where path_to_file will be something like ~/Downloads/browser-plugin-gnash_0.8.9-1ubuntu1_powerpc.deb .
 
My iBook isn't fast enough for  it so when I last tried playing flash videos I installed the firefox extension FlashVideoReplacer ([https://addons.mozilla.org/en-US/fir...videoreplacer/]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/")).  As this link ([http://ubuntuforums.org/showthread.php?t=1487327&page=4](http://ubuntuforums.org/showthread.php?t=1487327&page=4))  explains, the developer recommends you install the gecko-mediaplayer  (watch out for the typo in the instructions!).  Using FlashVideoReplacer  allows you to watch YouTube videos 'normally' i.e. no command line  stuff.  I'm not sure how you installed Ubuntu 11.04, but you could again have difficulty with mediaplayers due to missing packages.  See my lubuntu thread for a solution.
 
You may want another extension that blocks flash content on websites because gnash CPU usage is high even for simple adverts.  I hate my laptop fan coming on so I try to run my iBook as cool as possible at all times.  
 
Other ways to watch YouTube is by using html 5 ([http://www.youtube.com/html5](http://www.youtube.com/html5)).   This works quite well for videos coded in h.264.  You'll need Midori  or Epiphany browsers, but sadly the number of videos encoded in this  format are very few and I don't think it's worth the while installing  them just for that.  WebM videos  can be played in Firefox 4 & 5, Opera, Midori and Epiphany, but for me the playback  is choppy (similar to gnash).

---

### Post by rsavage on 2011-07-20
It would be good to hear from anybody who has gecko-mediaplayer working with firefox 5?  Videos don't seem to want to start with me.

---

### Post by rsavage on 2011-07-20
Okay, I haven't found much from googling, but I think there is a problem with firefox 5 and gecko.  I found something that said you have to install a newer version of gecko.  So it is compile time or you can use the slightly newer version from here [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa") (haven't had a go yet).

EDIT: Just tried version 1.0.0-0ubuntu2.1 from the 'proposed' repository.  Still doesn't work.  So will have to try compiling it now....

---

### Post by rsavage on 2011-07-20
The other thing I read was you don't have to install gnash now to use FlashVideoReplacer.

---

### Post by rsavage on 2011-07-20
Don't bother compiling the latest version of gecko-mediaplayer (1.04).  You get this error [https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053](https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053)
[I]
**EDIT: Note this post is very old now!  The problem was gecko didn't like being embedded into the web page, but worked in standalone mode.  I replaced gecko with totem at the time to get around this.**[/I]

---

### Post by oswaldkelso on 2011-07-21
On my debian testing boxes for youtube I use umplayer built from source. I think it has the code from minitube built in.

[http://www.umplayer.com/download/](http://www.umplayer.com/download/)

[http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)

Gnash also works here but I don't use it as my machines are to old for it's demands.

---

### Post by rsavage on 2011-07-23
I can't get gnash working with Firefox 5.  It seems a similar problem to gecko-mediaplayer.  Can anybody else confirm this with Firefox 5 of Iceweasel 5?
 
Btw, Totem also has a built in Youtube player.

---

### Post by alexcckll on 2011-07-24
> **linuxftw3 said:**
> do you have gnash 0.8.9 installed ? i installed that on my eMac that i  put Xubuntu 11.04 on and it works great.  also install ubuntu-restricted-extras along with Gnash and that should
 do it for you .:D  also, DRM based flash content doesn't work with Gnash, so if your trying to watch BBC or something like that, it won't work.
I've just raised that on a  BBC Internet blog thread, especially covering Adobe not providing builds for all architectures - and asked them to look into backing the DRM off just enough so iPlayer will run on Gnash as well as Flash - watch this space... 

[http://www.bbc.co.uk/blogs/bbcinternet/2011/07/bbc_news_and_bbc_iplayer_web_i.html#comments](http://www.bbc.co.uk/blogs/bbcinternet/2011/07/bbc_news_and_bbc_iplayer_web_i.html#comments)

---

### Post by Kaminari on 2012-06-12
Greetings,

A bit old, but still useful thread. I'd like to throw in my own experience with Flash on Linux PPC.

Neither Gnash nor Lightspark work on my iBook G4 running Lubuntu 12.04 and Firefox 11. Trying to use FlashVideoReplacer with Gecko MPlayer and Totem didn't produce any result either. Their respective plugin interface would load, but not the movie.

I finally stroke gold with VLC. It runs great with FlashVideoReplacer set on Medium quality (wifi connection). I disabled MP4 Over FLV option as it's too blurry otherwise, as well as WebM which is too slow. With those settings, picture quality on YouTube is nice and playback smooth, actually smoother than Flash player on my Window 7 system (3.6 GHz no less).

Although it's not specific to PPC, it's important to note that this solution doesn't work on all streaming sites. DailyMotion for example insists on using the Flash player, which makes it useless. Hopefully FlashVideoReplacer will be updated to work with more problematic websites, like this one:

[http://thebottomline.cpaaustralia.com.au/](http://thebottomline.cpaaustralia.com.au/)

Anyway, hope it helps!

---

### Post by canhoto on 2012-06-12
I use FlashVideoReplacer. It's a nice tool to replace Flash, at least with Youtube.

I disabled the html5 option within Youtube so that all the videos are  played like flash videos and replaced by FVR. Before, the html5 videos  wouldn't play, or I would hear the sountrack only, I don't remember.

But recently when I open a Youtube video the sound begins to play natively, even if it's recognized as a flash video. So, I hear the video's soundtrack and then, when FVR begins to play (with VLC, you're right, it's great), I hear the two sountracks.

I don't know why. To turn it around I set FVR to open the video in a new tab, then I close the original tab. But it's not so simple as it was when it worked very well embeded in the original page (and with only one sountrack!).

Another way of viewing flash videos (from most of the sites) is using Miro. Miro can play flash videos and you can navigate to the video sites from within, or add them to your sidebar.

So, if you're surfing the web and whatching videos, the best tool is FlashVideoReplacer (Gnash is outdated I'm affraid, and Lightspark is experimental and a long way behind). 

If you just want to surf the web for videos, then you can use Miro (there you can add Youtube, Dailymotion, Vimeo, etc.)

---

### Post by rsavage on 2012-06-16
With Flash Video Replacer it seems you need gnash/lightspark installed otherwise you get the double sound on youtube.  I think you are hearing the html5 soundtrack (it kicks in even if you are not part of the trial).  With a flash plugin installed you have more videos available to you too.

With html5 you are better using midori than firefox.  You get more options so you can watch  the video in lower quality.  I can watch html5 youtube on my ibook in this way.

For dailymotion site just spoof an iphone as described in the FAQ.  Works on my ibook.

Totem appears to crash in 12.04 (thanks for the vlc tip).  Anybody reported this as a bug?

Gnash works in midori.  

I don't normally watch videos on my ibook so have rather neglected testing and updating the FAQ about this sort of stuff.  I'm going to leave it for others with an interest in the subject to update.  Other people have got to start contributing to the documentation/testing/bug reporting!!!!

---

### Post by rsavage on 2012-06-17
FYI, the spoofing of an ipad seems to work much better if you downgrade libwebkitgtk-1.0-0 to the oneiric version.  Something else to look into....

---

### Post by rsavage on 2012-06-17
Okay here is a challenge for uk users! The BBC have finally started to do non flash video on their sports web site [http://www.bbc.co.uk/blogs/bbcinternet/2012/06/bbc_sport_mobile_video_euro.html](http://www.bbc.co.uk/blogs/bbcinternet/2012/06/bbc_sport_mobile_video_euro.html) . So far it is defeating me though. I've tried various user agent strings from [http://www.useragentstring.com/pages/useragentstring.php](http://www.useragentstring.com/pages/useragentstring.php) but I can't get midori to stream the video. Can anybody out there find the magic formula? Maybe try other web browsers??? 
 
It's so frustrating. I can get video on theguardian and dailytelegraph websites to work perectly on my ibook. 
 
As an aside, lightspark should now work on bbc new videos [http://allievi.sssup.it/techblog/?p=773](http://allievi.sssup.it/techblog/?p=773) . I've not looked into it yet as I'm still expecting problems with it due to my radeon card and gnash not working in firefox on PowerPC....
 
*EDIT: Changed the link to a proper BBC one. Reading the comments on that page it looks like the beeb are still not using proper html5 so maybe it is still impossible to view the content.*

---

### Post by rsavage on 2012-07-04
So 12.04....
 
To fix totem/parole/dragon/gstreamer apps crashes I had to run gstreamer-properties and change the video settings. The embedded firefox totem plugin then works. 
 
There is also some wierdness with pulseaudio. Some gstreamer apps with certain videos will crash if pulseaudio is not running. I don't know if it is a bad codec or some other problem with gstreamer. So if you are running midori/rekonq and html5 video crashes then this could be the reason. 

Totem crashes if I try to play a DVD without pulseaudio, but even with pulseausdio installed the video plays badly and the pulseaudio processor usage if through the roof! Same DVD plays fine with gnome mplayer or vlc.

With Dragon player in KDE you can change the audio backend if you are having problems:

```

sudo apt-get install phonon-backend-vlc
sudo apt-get remove phonon-backend-gstreamer

```

---

### Post by rsavage on 2012-07-16
Don't know if this is one of the problems with gstreamer [http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html) .

---

### Post by bobsan on 2012-07-16
You don't need to install flash or gnash or any of those with flashvideoreplacer. To eliminate the double sound in Youtube just disable html5. Go to [http://www.youtube.com/html5/](http://www.youtube.com/html5/) (check leave html5 trial) 

Instead of fooling around with totem and gstreamer, just install the gecko-mediaplayer. It works better any way.

Finally, in my experience gnash and lightspark never work and they freeze my machines.

---

### Post by 2blue on 2012-07-16
I think the gnash plugin for powerpc is broken. I`ve had expert help from guys on irc, and it will not play anything in browser. I`ve spend yet a few hours on this, with good help, an nothing to show for. Maybe there should be filed a bug message on this, or made a new thread devoted to Gnash. Does it play at all in 12.04 powerpc iso?

Thanks rsavage and all of you for your efforts, I shall give your post good attention tomorrow, and I am sticking with this. Also tomorrow, mplayer, gecko and FVR addon in powerpc.

---

### Post by rsavage on 2012-07-17
I think the problem is more likely to be Firefoxy than gnash since it works fine in other browsers.  The problem is very similar to gecko-mediaplayer and lightspark.  They get so far and then seem to not load the swf/whatever file and you end up with a black rectangle.  I haven't tried 10.04 for a while, but back in the day they all worked with Firefox 3.6.
 
Since you are using Lubuntu, the best thing to do is speak to the QA guys [https://lists.launchpad.net/lubuntu-qa/date.html](https://lists.launchpad.net/lubuntu-qa/date.html) .  See if the new version of Firefox produces a fix.  Gecko-mediaplayer is part of Lubuntu so they should be made aware that it doesn't actually work on PowerPC.
 
Raising a bug would also definitly be the way to go.  Everybody leaves it for somebody else to do.  Which is exactly what I am going to do.

---

### Post by 2blue on 2012-07-17
I did file a bugreport, hoping that someone will notice it. I suppose what it really needed is a capable builder or tester with an old powerpc he or she wants to use. I wish I was that clever.

---

### Post by rsavage on 2012-07-18
For completeness, I'll add shumway as another flash solution [http://mozilla.github.com/shumway/](http://mozilla.github.com/shumway/) .
 
It seems there are some successful users of lightspark [https://answers.launchpad.net/lightspark/+question/201611](https://answers.launchpad.net/lightspark/+question/201611) .  Come on Conal, tell us how you did it?!

---

