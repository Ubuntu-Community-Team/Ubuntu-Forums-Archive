---
title: "[SOLVED] does wine drag you down"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-15
hi not used wine yet but im planning to as there are lots of windows programs I need not available for linux and I wanna ditch windows completely.

Some of the programs I use take a lot of processing power. Like video encoding etc. Just how much of an overhead does wine give. would running a benchmark like pc mark work to compare the results?

---

### Post by nickj6282 on 2007-10-15
I'm not sure what your other needs are, but for video transcoding I have found nothing better than the wonderful VLC, which is available for Linux, Windows, and Mac. I would try the native Linux programs before trying to muck around with Wine. I have found that very little that I want to do works in Wine.

---

### Post by LowSky on 2007-10-15
Synaptic has many video/music editing programs, try those.

---

### Post by arashiko28 on 2007-10-15
What kind of video encoding yo do? add subtitles, edit the length, MV? Prepare them for DVD burning? All of this can be done with linux programs in the half of the time. Just give it a try:)

---

### Post by bigmonmulgrew on 2007-10-15
i also use nlite to create unattended windows discs. This doesn't take a massive amount of time, maybe 20 min depending on settings. but i dont want the time to go up massively.
i have tried various video encoding programs and im liking how much faster they are
but I need to encode to wmv to play on my xbox 360 and linux does not have great support for windows file formats. To be honest I like the linux stuff but I want to be able to fall back onto more familiar programs without having to dual boot.

I also wanna stream to the 360 but the only programs that can do this run in windows as far as I am aware. If i could get wmp11 in wine to stream to the 360 that would be great. hows wine with networking by the way?

---

### Post by nickj6282 on 2007-10-15
> **bigmonmulgrew said:**
> 
i have tried various video encoding programs and im liking how much faster they are
but I need to encode to wmv to play on my xbox 360 and linux does not have great support for windows file formats. To be honest I like the linux stuff but I want to be able to fall back onto more familiar programs without having to dual boot.

I also wanna stream to the 360 but the only programs that can do this run in windows as far as I am aware. If i could get wmp11 in wine to stream to the 360 that would be great. hows wine with networking by the way?

I've heard it's possible to stream to the 360 without Windows, but I never tried it. Another option is to load up your WMVs on a burned DVD or a USB hard disk and put that on your 360 to watch them. I'll play around with VLC when I get home, but I think it's possible to convert to WMV with it.

---

### Post by bigmonmulgrew on 2007-10-16
it is possible but ive never had a usable file output.


Currently I drop the wmvs on a usb stick. I have to use windows to convert them though. If i cant get vlc or other to convert I will have to use windows or wine. as above though I am also concerned about nlite running correctly

---

### Post by asmoore82 on 2007-10-16
> **bigmonmulgrew said:**
> hi not used wine yet but im planning to as there are lots of windows programs I need not available for linux and I wanna ditch windows completely.

Some of the programs I use take a lot of processing power. Like video encoding etc. Just how much of an overhead does wine give. would running a benchmark like pc mark work to compare the results?

GNU+Linux is a Free Operating System;
but Linux is **Not** *Free Windows*.

Wine should only be used for programs for which there is no native Linux alternative.
If there is a viable Linux alternative but you still prefer the Windows based app., maybe Linux is not for you.

End Disclaimer;

That having been said, benchmarks are, for the most part, a waste of time.
The Proof is in the Pudding.

End Double Disclaimer;

That having been said, Windows based apps *that do not make system calls*
will run **Faster** through Wine/UNIX than on Windows.

Begin Reality;

I can assure you that in the area of Video transcoding,
the Linux apps are far superior to their Windows counterparts.
A growing number of Windows tools in this area are actually
using stolen GPL "Free" code from Linux based projects.
[http://slated.org/anvsoft_dvd_photo_slideshow_is_stolen_gpl_software](http://slated.org/anvsoft_dvd_photo_slideshow_is_stolen_gpl_software)
how does one steal what is Free?
by selling it to people without telling them that it is Free.

---

### Post by Kilz on 2007-10-16
> **asmoore82 said:**
> GNU+Linux is a Free Operating System;
but Linux is **Not** *Free Windows*.

Wine should only be used for programs for which there is no native Linux alternative.
If there is a viable Linux alternative but you still prefer the Windows based app., maybe Linux is not for you.

End Disclaimer;

That having been said, benchmarks are, for the most part, a waste of time.
The Proof is in the Pudding.

End Double Disclaimer;

That having been said, Windows based apps *that do not make system calls*
will run **Faster** through Wine/UNIX than on Windows.

Begin Reality;

I can assure you that in the area of Video transcoding,
the Linux apps are far superior to their Windows counterparts.
A growing number of Windows tools in this area are actually
using stolen GPL "Free" code from Linux based projects.
[http://slated.org/anvsoft_dvd_photo_slideshow_is_stolen_gpl_software](http://slated.org/anvsoft_dvd_photo_slideshow_is_stolen_gpl_software)
how does one steal what is Free?
by selling it to people without telling them that it is Free.

Quoted for the pure truth it provides.

---

### Post by bigmonmulgrew on 2007-10-16
I am very much aware that linux is not free windows. I want to move off windows completely and being able to use nlite and convert to wmv are 2 of my requirements.
I really cant see a program that is designed to make slipstreamed windows installations having a native windows alternative.
This leaves me with 2 options. Keep windows and dual boot, which is what i may be forced to do but want to avoid, or run it in wine.

On the wmv subject everyone seems to have picked this up as the main point of my thread. I know there are native linux applications that will convert to wmvs but until I can get them to work I want wine or dual boot to tide me over. Again I would like to avoid dual booting

The reality is that I may be forced to dual boot but I want to avoid this as much as possible.

I also wish to play WoWand as im aware there is no native linux app for this it must run in windows or wine. I didn't ask about this because I'm sure I far exceed the requirements for the game so having overheads was not an issue.

---

### Post by bliffle on 2007-10-16
You should look at "ffmpeg" on linux. It has great flexibility and successfully transcoded everything that I threw at it. For example, FLV files from youtube.

---

### Post by argie on 2007-10-16
It depends upon the application and what functions it uses. As you can see from these benchmarks of old releases: [http://wiki.winehq.org/BenchMark-20050419](http://wiki.winehq.org/BenchMark-20050419) , some things are faster and some slower. Also, it varies a lot between distros. The only way to tell is to try it. If you do transcode the same video twice, once under wine, once under windows, and once with ffmpeg, then you'll have a nice idea of which to use. 

Good luck.

---

### Post by amlucent23 on 2007-10-16
> **bigmonmulgrew said:**
> I am very much aware that linux is not free windows. I want to move off windows completely and being able to use nlite and convert to wmv are 2 of my requirements.
I really cant see a program that is designed to make slipstreamed windows installations having a native windows alternative.
This leaves me with 2 options. Keep windows and dual boot, which is what i may be forced to do but want to avoid, or run it in wine.

On the wmv subject everyone seems to have picked this up as the main point of my thread. I know there are native linux applications that will convert to wmvs but until I can get them to work I want wine or dual boot to tide me over. Again I would like to avoid dual booting

The reality is that I may be forced to dual boot but I want to avoid this as much as possible.

I also wish to play WoWand as im aware there is no native linux app for this it must run in windows or wine. I didn't ask about this because I'm sure I far exceed the requirements for the game so having overheads was not an issue.

Wow plays near perfect through wine. Your biggest draw back will not be the layer of wine between the game and the operating system but the quality of your video cards drivers. as an example ATIs *nix drivers are no where near the quality of their windows drivers I would get 50-70 FPS in WoW with my ATI x1600 in windows, however using the same PC I will get half that in linux. On my notebook pc with a Nvidia card my FPS in Wow is greater than windows as Nvidias *nix drivers actually work correctly. :lolflag:

---

### Post by linuxlizard on 2007-10-16
Just some free advice-

Don't count on wine running your apps and delete windows until you try them under wine first. Wine is pretty hit or miss- some programs will work great, many won't work at all. Don't find out that something you want won't work *after* you delete windows- give it a whirl on wine first.

Speed wise- like everyone says- depends on the application. For the stuff I've used wine works fast. But a lot of stuff won't run at all. 

Really cool when it works though.

Check out wine-doors (google) before you install wine. Wine-doors will do it for you and set things up nicely.

---

### Post by bigmonmulgrew on 2007-10-20
> **amlucent23 said:**
> 
On my notebook pc with a Nvidia card my FPS in Wow is greater than windows as Nvidias *nix drivers actually work correctly. :lolflag:

thats good to hear I have a nvidia card 7600 to be precise

---

### Post by bigmonmulgrew on 2007-10-20
> **linuxlizard said:**
> Just some free advice-

Don't count on wine running your apps and delete windows until you try them under wine first. Wine is pretty hit or miss- some programs will work great, many won't work at all. Don't find out that something you want won't work *after* you delete windows- give it a whirl on wine first.

Speed wise- like everyone says- depends on the application. For the stuff I've used wine works fast. But a lot of stuff won't run at all. 

Really cool when it works though.

Check out wine-doors (google) before you install wine. Wine-doors will do it for you and set things up nicely.

My plan is first to look for a native linux alternative, second to try and run my current windows program in wine, then as a last resort to keep XP and just shrink its partition.

Hopefully with DELL moving to using ubuntu then driver and software support for the OS will improve and I will be able to drop MS products completely.
I can see that taking a long time but theres no harm in trying is there

---

