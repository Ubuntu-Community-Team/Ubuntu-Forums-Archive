---
title: "YouTube with a PPC Linux system - is it possible?"
date: 2008-10-18
forum: Apple Hardware Users
---

### Post by khelben1979 on 2008-10-18
Is it possible to get YouTube videos to work with my old Powerbook over here? I haven't got it to work.

Any suggestions?

---

### Post by ppc_guy on 2008-10-19
Good question. If you are still running debian on your Lombard you will need to get the restricted repos for either Etch or Lenny depending. It's pretty much the same as ubunturesticted from there. Enable those via Settings->Repositories. See if that helps, you might be restricted by the 8mb ATi rage onboard though, more so if you are trying to stream via wirless. 

As a side note, could you post how your install went? I have the same laptop here with 192mb's of ram I have yet to get a successful install of any form of linux onto yet..

As always, your mileage may vary,
ppc_guy
---------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango_Hotel.
---------------------------------------------------------------------

---

### Post by khelben1979 on 2008-10-19
The first install of Debian on to this powerbook was Debian Woody and then later I upgraded to Sarge and now it's on Etch.

Later this autumn/winter I will be upgrading to the new Lenny release.

Debian works very good on this old hardware, although the speed is... well. I would say that it's fast on how it is utilizing the hardware, but of course more speed would be desirable. :)

I installed Etch using an netinstall CD and after a install, the basic things like working graphics and working sound worked well. I think that I might have done a manual install of the alsa packages later on, I don't remember.

When it comes to YouTube, I actually have installed a flash package several months ago, but it seems that it isn't compatible with later versions of flash. That's my main problem. I think that 8MB of graphics memory is no problem, actually. I installed some libflash package because there is no available flash or working source package for this platform.

Debian Etch works very good over here and it's a pure joy to use it.

---

### Post by tiresia on 2008-10-19
I have installed gnash on Debian Lenny, and it works with youtube - but not with every flash data, and the fans speed loud.
I tried it also in Etch and in Ubuntu Hardy, but it did not work. Other possible solution did not work.

---

### Post by kerry_s on 2008-10-19
[http://debian-multimedia.org/](http://debian-multimedia.org/)

---

### Post by khelben1979 on 2008-10-19
Since Lenny hasn't been released yet, I'll continue on using Etch. Right now I'm actually compiling up a lot of source packages in order to be able to install the latest version of gnash.

It remains to be seen if this will work.

When it comes to my pc, the keyboard is broken right now so I can't use it until tomorrow. That is why I'm struggling with getting YouTube to work on this machine also.

---

### Post by sethvath on 2008-10-19
Lenny works on a G3? That is promising, all I need to do is find a weekend installing it or end up pulling out the rest of my hair.

---

### Post by tiresia on 2008-10-19
> **sethvath said:**
> Lenny works on a G3? 
[http://www.debian.org/devel/debian-installer/index.en.html](http://www.debian.org/devel/debian-installer/index.en.html)
I don't know, how it works on a powerbook g3, but I installed it on my G5 and on a beige g3 (with BootX). And it runs perfectly :) -

---

### Post by khelben1979 on 2008-10-19
For the moment I have given up. It ended up that I needed a newer version of libglibs. *sigh*

Looking forward to using Lenny when it's finished. Etch feels a bit old now.

---

### Post by ssam on 2008-10-19
the best way to watch youtube on powerpc is to use totem or miro. in totem you need to enable the youtube pluggin (and you need to have 2.22 or later (the plug in is much improved in 2.24)). miro has a video search that does youtube.

---

### Post by khelben1979 on 2008-10-20
There is an firefox plugin which enables me to convert the videos directly from the YouTube website into another format. I chose AVI. So, currently I can view all YouTube videos, but not without converting them.

The Firefox plugin is called: media converter.

I have chosen to drop my efforts in trying to get this to work with Etch, as I wrote.

Looking forward on seeing a stable version of Lenny once it's out.

---

### Post by oswaldkelso on 2008-10-20
I use clive on my 333imac works great. you'll have to build it your self if you on etch or use backports

[http://forums.debian.net/viewtopic.php?t=25187](http://forums.debian.net/viewtopic.php?t=25187)

---

### Post by khelben1979 on 2008-10-21
The impression I got when looking at that webpage was that it was a bit too complicated for my taste.

The Firefox plugin is very easy to use.

---

### Post by oswaldkelso on 2008-10-21
No it's easy once installed. In it's simplest form just open a terminal:
clive url
e.g.
clive [http://uk.youtube.com/watch?v=PuGVz15Pe5Y](http://uk.youtube.com/watch?v=PuGVz15Pe5Y)

to play cd_to_video and choose:
player name_of_video
e.g.
ffplay name_of_video
done.

It downloads the hight quality mp4 if available, gives the file a real name, not [http://uk.youtube.com/watch?v=PuGVz15Pe5Y](http://uk.youtube.com/watch?v=PuGVz15Pe5Y) 

I find it makes my whole internet experience faster than having a flash type player installed. I suspect that websites see you don't have flash installed and don't try loading stuff in the background, improves the performance of my low end machines noticeably.

---

### Post by mkvnmtr on 2008-10-21
I had never watched you tube but after reading this thread I tried. Miro keeps crashing so I tried Totem. The first time I tried search You tube nothing happened. Then I installed the add on Media Converter and I am able to search and view the movies just fine. I am on a power pc and have no flash and no script add on on Firefox so I had never tried. I am sure if you put in a litle work with Totem you should be able to view You Tube. It's just that I am not real interested. Maybe when I have time I will see what else works that In never use.

---

### Post by khelben1979 on 2009-01-10
> **ssam said:**
> the best way to watch youtube on powerpc is to use totem or miro. in totem you need to enable the youtube pluggin (and you need to have 2.22 or later (the plug in is much improved in 2.24)). miro has a video search that does youtube.

I haven't found where I can get this youtube plugin for my ppc linux system over here. Do you have a link?

I still haven't upgraded to Lenny yet on this laptop, but it should work on Etch, yes?

---

### Post by MegaLoler on 2009-10-26
I know this is an old thread, but I've had this problem before and I found a solution!  So I decided to post it here.
First you need to install greasemonkey: [https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)
And then, install this script: [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)
And you can watch them directly in your browser without any downloading or any other stuff.
That's it!  Hope this helps.

---

### Post by khelben1979 on 2009-10-27
Hmm.. My Powerbook is no longer working due to crashed harddrive since several months ago, but thanks anyway for the advice.

---

### Post by natgab on 2009-10-29
> **MegaLoler said:**
> I know this is an old thread, but I've had this problem before and I found a solution!  So I decided to post it here.
First you need to install greasemonkey: [https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)
And then, install this script: [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)
And you can watch them directly in your browser without any downloading or any other stuff.
That's it!  Hope this helps.

---Dude, you rock !  I saw this thread, and now I have perfect YouTube videos on my PPC computer.  If this works well on other Flash stuff, I might not need to get a PC box to run Ubuntu :D

You really need to post this little How To in some of the other Linux forums for us PPC users.  It the only real drawback for running Linux on our PPC Macs for those of us abandoned by Snow Leopard.

NOTE: I got this working on my G5.  I did not try it yet on the iMac. In Mac OS 10.3 on it, I could not get YouTube to stream without stuttering. My Pismo with the same  video chip also stutters and both of these with fast internet. Both machines play flash fine once downloaded, just not streaming.

---

### Post by Praxicoide on 2009-11-04
Thank you so much. I've been scratching my head with this for at least an hour and here's a simple solution.

---

### Post by treoptika on 2010-10-03
Amazing!!! Powerbook G4 with 10.04 ubuntu this workaround is perfect. Took a little tooling around with the YWOF preferences but I was able to get it to a very nice streaming quality. ( Changed the default quality to MP4 - high;  generic player MIME to application/x-mplayer2. Before doing this the videos were unwatchable-y choppy / no sound. ) I'm sure this can be reworked to handle other streaming media websites.

---

### Post by oswaldkelso on 2010-10-04
epiphany and midori work with youtube if you choose the html5 option.

Minitube is a very easy option that I use most for quick viewing then switch to clive or cclive or youtube-dl if I want to keep the file

[http://forums.debian.net/viewtopic.php?f=16&t=51504](http://forums.debian.net/viewtopic.php?f=16&t=51504)

Also gnash is quite usable now, though you do need to keep a killall -gtk-gnash in your menu :) I find it very helpful in getting the actual URL I need to down load a file even if gnash can't play it.

All the above on Debian testing

---

### Post by trj021782 on 2010-10-05
I have not read every post in this forum so i appologize if i am re-posting what some else already said, but you can view certain youtube files in HTML5 using an appropriate web browser like Opera 10.(something) goto 

[http://www.youtube.com/html5](http://www.youtube.com/html5) 

it will tell you what browsers support it

this is still in beta for you tube so only certain videos work, also for all of you die hard firefox fans there is a firefox that supports HTML5 but it is still in beta as well so i would not reccomend it yet

---

