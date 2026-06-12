---
title: "I need help Improving picture/screen quality of wma"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-13
Hello again, I have almost fixed my media issues.

My new issue is the picture and screen quality. I have installed a few mdeia players and all played the video (WMA), but the picture quality was so bad compared to how it use to play on WMP or Quicktime. 

The picture was very bright and grainy.

Any guides for fixing my picture resolution for either gxine, totem Movie Player, or Xine. I also have VLC installed and Real MP10, as well as xfmedia which is default.

Do I have too many media players. They all had the same exact screen resolution and brightness.

I'm thinking that I haven't installed the proper code to support my HP pavilion intel celeron dv4230us sound/video/graphics, or I need to adjust something.

I also need to support my internal wireless card if anyone knows of a good guide to link me too.

Any help would be cool, thanks.
-c.

I

---

### Post by My Name on 2006-10-13
The video file for windows media if .wmv not .wma. WMA is the audio format.  

I would say the codecs are the problem.  I'd guess you need to list the codecs you have installed.

---

### Post by Rhubarb on 2006-10-13
Have you tried to install w32codecs?  This might fix up your problem, I dunno - I haven't installed w32codecs on my system because it had caused instability problems, so I just use gstreamer bad / ugly / multiverse.

Do you know what internal wireless card you've got?  Such as what chipset / brand / model it is?  ndiswrapper and some windows ini (inf?) drivers might help you out here.  I don't know how to use ndiswrapper personally.

---

### Post by crimesaucer on 2006-10-13
yeh, I'm really tired, I been up all night learning this new os, so I meant WMV not windows media audio.

Well as for codecs, I have added these: sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

and these...(some are repeated):gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs 
ffmpeg 
lame 
faad 
sox 
mjpegtools 
libxine-main1

...as well as what plugins were suggested in the synaptic manager with each media player.

I would love to install the best picture playback possible.

I also would like to get some info on things that I used to have to have installed in windows like the A3C-filter, Xvid codecs, and divX codecs that I needed to play my DVD movies and CD  movies and movie clips. Do I need those exact codes in a linux form, or something else that is similar.

Thanks.

I also have automatix2 and EasyUbuntu which I haven't used yet, so if I should install a codec from there I could. I just have been having fun learning it all on my own.

---

### Post by crimesaucer on 2006-10-13
Well I un-installed totem, gxine, and found and adjusted the contrast and brightness of the Xine media player. And it looked good, but still was a bit "grainy" instead of really clear.

any suggestions.

and my apologies for posting so much, I'm just really new to this and have been on the computer for like 3 days straight figuring this all out.

---

### Post by crimesaucer on 2006-10-13
umm...It's an intel...celeron...

 	
Mobile Intel® 910GML Express Chipset for the Celeron® M processor. DDR 333 MHz

I think the graphics is: Intel Graphics Media Accelerator 900 

bottom of the line baby...straight slummin it.

---

### Post by d3v1ant_0n3 on 2006-10-13
Been a while since I had to sort this issue out myself, but I got there in the end and will try and remember...

First off, give Automatix a run through, select the audio and video codecs it can install (plus dvd player support etc). I believe easyubuntu contains many of the features, but I always have issues with it so I don't use it.

This should fix your video playback problems.

If it doesn't, make sure you have the correct graphics driver- I use an intel 845 and the machine defaulted to using the basic vesa driver for me.

In a terminal, run "sudo dpkg-reconfigure xserver-xorg" (without the quotes) . This should bring up dialogue that will help you set up your display right. It's fairly straight forward, but you need to make sure it's choosing the i810 driver (for intel chips) rather than the vesa one.

Sorry if this isn't too coherent, still working on my first coffee of the morning:neutral:  .But I hope it helped some.

---

### Post by crimesaucer on 2006-10-13
thanks for the tip, I'm actually about to go to sleep after working through the night...lol

I have a question about the automatix2. I installed it, yet I just went ahead and installed what I needed like flash/java5 some codes, and some programs through terminal.

Now if I activate the automatix2, how will that affect what I've already installed. And when I'm done with the automatix2, and it's time to shut it down and close, do the installs like azerus or codecs, stay installed.

Also, I have added wine, freecontrib, automatix, canonical, budget dedicated and all of the dapper repositories, when I close the automatix2, and go back to my sources.list, the installs from automatix like certain codecs, will they still work. 

thanks.

---

### Post by evolvedlight on 2006-10-13
Hey

I would suggest using VLC instead. It is like the ultimate plays everything (even my badly converted broken mp3 files) player. Does your internal wireless not just work straight off? What laptop do you have? My Dell 1300 everything works fine apart from I needed to install 915resolution

S

---

### Post by jonrkc on 2006-10-13
> **evolvedlight said:**
> Hey

I would suggest using VLC instead. It is like the ultimate plays everything (even my badly converted broken mp3 files) player.
I suggest giving vlc a try, too.  I've found a few videos (including DVD's) that vlc gave up on, but I was able to play those using gxine.  Between vlc and gxine I've been able to play anything except ONE commercial DVD...  

Some of the "graininess" visible is not a fault in playback, but a token of poor picture quality in the original.  Also, on a good monitor you will be able to see the actual film grain in movies shot on film (as opposed to digital originals).  We're not used to seeing this, even sometimes in theaters.  But it's there.  I'm still not used to seeing detail in movies that I wouldn't have been able to see even on the theater screen.

---

### Post by qyot27 on 2006-10-13
Anything that supports the libavcodec libraries (that would be mplayer, VLC, xine, etc.) will decode most things straight out of the box, leaving the choice up to the user as to how they want to interact with the GUI.  libavcodec forms the core of ffdshow on Windows, and thus there aren't really any viable standalone DivX or XviD (well, more properly, MPEG-4 Advanced Simple Profile) decoders that work on Linux like the ones you'd install for Windows.  They're consolidated into one single decoding library (libavcodec) that is usually touted as the best even when running on Windows as well.

It is worth it to note that in certain cases, particularly with VLC and possibly mplayer, some things - like WMV9 - are not supported by default, and while there are posts floating around describing how to set them up so that they do, it requires compiling from source.

Part of the graininess issue is probably because of post-processing (or rather, lack thereof), which for performance reasons is better left disabled anyway.

---

### Post by crimesaucer on 2006-10-13
Thanks, I'll give VLC a try, the media player looks very professional.

As for my wireless card, I have a HP pavilion dv4230us with celeron m, and when I click on activate eth1 for wireless, it goes to an "activating interface eth1", then it says, "Wireless connection The interface eth1 is active." 

Then I press ok, and the dialogue box takes almost a minute to close out.

Then when I go back to Apps->-System->-Networking...it says that the "Wireless connection The interface et1 is not active."

plus my wifi antenna lcd light (little blue light above the mute button above the function keys) never went on at all.

My mute button doesn't work either, and volume won't go up or down. So, my new focus tonight will be correcting my volume issues and making sure my wifi wireless is perfectly working.

Any suggestions.

thanks again for the help.

---

### Post by qyot27 on 2006-10-14
> **qyot27 said:**
> libavcodec forms the core of ffdshow on Windows, and thus there aren't really any viable standalone DivX or XviD (well, more properly, MPEG-4 Advanced Simple Profile) decoders that work on Linux like the ones you'd install for Windows.
I think I should probably elaborate on this a bit, since I don't think I said it quite the right way.

DivX and XviD, if you use Windows Media Player (7/8/9/10/11/etc. series or the simple 6.4 version) use decoders that interact with DirectShow, which is one of two default video interfaces that Windows uses (the other being Video for Windows, which DirectShow was/is meant to replace).  For something like a standalone DivX or XviD decoder on Linux, it would require something similar to DirectShow.  gstreamer, from what I've read, comes the closest to this, but I'm not really all that crazy about it.  I've read about [UCI](http://uci.sourceforge.net/) a little bit and it certainly looks promising, but it's still too early to tell if it'll actually come to fruition (although since at least one of the developers worked on Matroska - i.e. MKV - I'd hope that it gets to that level, as Matroska is very nice and I fully support its use).

The main hurdle with UCI is the same hurdle that gstreamer has - widespread acceptance to make it a fundamental part of the system.  AFAIK, on Windows there's no way you can get rid of DirectShow without causing a bunch of other problems - I'm not saying that gstreamer or UCI would best be so intimately tied to the system that removing it would cause problems, but that it would have to gain enough recognition as an indispensable piece of software that most distributions would include it by default, and by extension it become so ubiquituous that developers for other programs make the use of either (or both) interfaces seamless.

Of course, for that matter, I don't know if UCI has any activity on it anymore.  Their dev maillist on Sourceforge hasn't been very active since late 2003, and most stuff from the last couple years that's present just look like posts from the kinds of spammers that show up on messageboards and ramble something about free Viagra.  Maybe all the development talk has just moved to IRC or some such, but I don't know.

---

