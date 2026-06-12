---
title: "How to watch youtube clips without flash-gnash etc on PPC"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by oswaldkelso on 2009-09-17
First off I use Debian but I'm pretty sure these apps are in Ubuntu. I just notice a lot of new PPC users struggling so thought I'd chuck this in. 

I only really need flash for youtube and as it doesn't exist and gnash can be a bit cpu intensive on my old PPC hardware I use clive in terminator.  Then I split the screen and run mplayer -ontop name-of-clip, works a treat. (you can leave out the -ontop bit if your feeling lazy)
No need to wait for the download, and you can be adding other clips at the same time.

Depending on your connection speed you can vary how much video to cache. On my poor 1mb connection I give 5% on small clips and 10-15% on larger ones.

In reality by the time you've split the terminator screen and typed mpla (TAB to auto complete) and read and started typing the youtube clip name (clive changes all that gobby gook to a real name) your buffer has loaded. Sweet. 

In debian I use mplayer from debian multimedia repo,(non gui) I don't know which ubuntu repos has it. 

as root ```
apt-get install clive mplayer
``` 

 or you could just use the customvid addon for firefox/iceweasel [https://addons.mozilla.org/en-US/firefox/addon/12027](https://addons.mozilla.org/en-US/firefox/addon/12027) (License: Mozilla Public License 1.1 (MPL 1.1) 

[http://www.youtube.com/watch?v=aahiPQwb5hM](http://www.youtube.com/watch?v=aahiPQwb5hM)

enjoy :)

---

### Post by urosg3 on 2009-09-18
tnx, nice tip :)

---

### Post by zerobotman on 2009-09-18
awesome! do you think an imac g3 500mhtz with 512 ram would be up to the task?

---

### Post by oswaldkelso on 2009-09-18
Works fine on my imac. 333mhz 256mb :) Of course you don't have to have terminator. If you want, or like another terminal just open two windows or use the stream option. 

I like to see the size of the download so I can make a judgment on how much cache to allow. If the clip is small I start mplayer as soon as the name shows up in clive.

---

### Post by marshag63 on 2009-09-19
You can also use the Firefox Add-On Video Downloadhelper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Works great on my G4 iMac running Ubuntu 8.10.

MarshaG.

---

### Post by rjcalifornia on 2009-09-22
I added Mplayer, however, I get a fatal error message :S

the firefox add-on doesn't work at all for me :'(

any suggestions?

---

### Post by oswaldkelso on 2009-09-22
> **marshag63 said:**
> You can also use the Firefox Add-On Video Downloadhelper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Works great on my G4 iMac running Ubuntu 8.10.

MarshaG.

But does it play the downloading stream?

---

### Post by oswaldkelso on 2009-09-22
> **RandyVanBuren said:**
> I added Mplayer, however, I get a fatal error message :S

the firefox add-on doesn't work at all for me :'(

any suggestions?

I know youtube broke compatibility with clive and it was patched maybe customvid still needs updating?

Does clive work? If not get the latest version.

Make sure mplayer can play an already down loaded clip first. 
Open a terminal and start mplayer to see what info it gives. I dont use ubuntu but you'll get mplayer info here.

[http://www.mplayerhq.hu/design7/info.html#docs](http://www.mplayerhq.hu/design7/info.html#docs)
and here
[http://forums.debian.net/viewtopic.php?f=16&t=17783&start=0](http://forums.debian.net/viewtopic.php?f=16&t=17783&start=0)

Try another player xine or vlc. Both these players have non gui versions.

---

### Post by B_Free on 2009-09-22
I am still trying to learn. Does this video help anyone?
[http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)
It is about getting CODECS for Ubuntu.

---

### Post by rjcalifornia on 2009-09-24
> **oswaldkelso said:**
> I know youtube broke compatibility with clive and it was patched maybe customvid still needs updating?

Does clive work? If not get the latest version.

Make sure mplayer can play an already down loaded clip first. 
Open a terminal and start mplayer to see what info it gives. I dont use ubuntu but you'll get mplayer info here.

[http://www.mplayerhq.hu/design7/info.html#docs](http://www.mplayerhq.hu/design7/info.html#docs)
and here
[http://forums.debian.net/viewtopic.php?f=16&t=17783&start=0](http://forums.debian.net/viewtopic.php?f=16&t=17783&start=0)

Try another player xine or vlc. Both these players have non gui versions.

VLC does not work at all under K/X/Ubuntu, I don't know why, but it doesn't. 

I tried xine, but nothing. I used to grab the youtube link from [HTML]www.keepvid.com[/HTML] with Kaffeine in 7.04, however in 9.04 doesn't work. 

I did the Mplayer thing, but I'm a total newbie so I don't know what to do with that info :S

---

### Post by sweetleaf on 2009-09-25
Thanks for the tip, oswaldkelso. I'm looking forward to taking clive for a spin.

For those of you who are having trouble with mplayer and vlc, are you by any chance using G3s? As far as I can tell, the mplayer, vlc, and gstreamer packages in the Jaunty PPC repositories are all broken for G3. There are some bug reports that suggest the problem is that they were compiled without support for non-Altivec processors. I've successfully recompiled mplayer, vlc, and gnash/ffmpeg (instead of gnash/gstreamer) on my G3, which means that it isn't a problem with the hardware or with some other package.

---

### Post by rjcalifornia on 2009-09-26
> **sweetleaf said:**
> Thanks for the tip, oswaldkelso. I'm looking forward to taking clive for a spin.

For those of you who are having trouble with mplayer and vlc, are you by any chance using G3s? As far as I can tell, the mplayer, vlc, and gstreamer packages in the Jaunty PPC repositories are all broken for G3. There are some bug reports that suggest the problem is that they were compiled without support for non-Altivec processors. I've successfully recompiled mplayer, vlc, and gnash/ffmpeg (instead of gnash/gstreamer) on my G3, which means that it isn't a problem with the hardware or with some other package.

ok... so, how do you recompile mplayer or vlc????

---

### Post by sweetleaf on 2009-09-26
> **RandyVanBuren said:**
> ok... so, how do you recompile mplayer or vlc????

There's a pretty good thread [here]("http://ubuntuforums.org/showthread.php?t=1081070").

A workaround would be to try debian instead; it sounds like they have better PPC support.

---

### Post by oswaldkelso on 2009-09-28
Here's a link to show it does work, on Debian anyway.

[http://www.youtube.com/watch?v=y-KeLxxHkEY](http://www.youtube.com/watch?v=y-KeLxxHkEY)

---

### Post by JanusDC on 2009-10-25
@oswaldkelso: Thank you VERY much! Me and my debian/ppc on PowerBook G4 12'' are realy thankful! WE CAN SEE YOUTUBE!!!! :)

---

### Post by oswaldkelso on 2009-10-25
Your welcome. You may like cclive also it seems to do more sites than just clive. For multiple downloads with a nice little gui see abby :)

---

### Post by JanusDC on 2009-10-25
Mmm... ok, but I don't get it: Does this add-on use clive (or cclive) for something? Because I am using it without clive and it works perfectly... what is clive needed for?

---

### Post by oswaldkelso on 2009-10-25
> **JanusDC said:**
> Mmm... ok, but I don't get it: Does this add-on use clive (or cclive) for something? Because I am using it without clive and it works perfectly... what is clive needed for?

Yes, Abby needs clive or cclive to be installed [http://code.google.com/p/abby/](http://code.google.com/p/abby/) I use clive or cclive if I just want to play a single youtube link and abby if I want to select from all the links on the page.

---

### Post by JanusDC on 2009-10-25
What I ment is that you don't need cclive nor abby to play youtube clips! It is enough with the add-on + mplayer!

---

### Post by oswaldkelso on 2009-10-25
Customvid add on? Yes it works but not as flexible as clive cclive and abby. It's still alpha so not as reliable yet. Basically you need something to grab the real url of the video, and something to play it. What you choose will depend on many things. 

I showed clive and mplayer because it works on really lowend PPC's and is not tied to firefox/iceweasel. This allows users of dillo2 (great browser for low end stuff) or arora etc to stay light and keep those crappy machines running.

---

