---
title: "Lightspark on a powerpc"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by rsavage on 2011-01-18
Hi all,

I posted most of this last night, but the thread seems to have disappeared for some reason!

I'm just wondering if anybody has tried lightspark (the new open source flash player) on a powerpc yet? 

I've managed to compile and install it on a late 2004 G4 ibook (1.2Ghz, 12" 9200 radeon mobility) running ubuntu 10.10 (maverick).  However, when I go to a website with flash the browser just closes.  When I try the standalone package (using the test suggested in [http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting](http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting)) I get the error "problem in t_src_class" and again the test window just closes.

A bit of googling and this error seems to be associated with the open source mesa drivers for radeon cards.  A bit more googling and it seems the radeon drivers have been problematic with lightspark.  The suggested fix is to use Mesa 7.8.2 or better.  I have 1.3 Mesa 7.9-devel courtesy of the update to maverick.  What I'd really like to know is if anybody has got lightspark working and what version of mesa they are using?  I'm wondering if people with 10.04 lucid will have more luck as graphics seemed less troublesome in that version. 

For those interested in trying lightspark the web page you need is [http://sourceforge.net/apps/trac/lightspark](http://sourceforge.net/apps/trac/lightspark).  The release 0.4.5.1 is the version with ppc support.

I've only been using linux for 3 months and less than 1 month on my ibook so I don't really know what I'm doing or understand it all.  I've tried the 0.4.5.1 version as well as the "bleeding edge" version following the instructions for installing from source which is on the page [http://sourceforge.net/apps/trac/lightspark/wiki/Building](http://sourceforge.net/apps/trac/lightspark/wiki/Building). I installed the list of packages on the bottom of the web page.  The command "c*make -DCMAKE_BUILD_TYPE=Release -DCOMPILE_PLUGIN=1 -DCMAKE_INSTALL_PREFIX=/usr .. *" wanted more packages and I installed them to satisfy it.  I compiled and installed the latest version of libxml++2.6 from here [http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/) (following the instructions on the INSTALL file).  Other packages I remember needing are libboost-dev and libboost-filesystem-dev which I just did normally.  I also needed the command "*sudo ln -s /usr/include/gdk-pixbuf-2.0/gdk-pixbuf /usr/include/gtk-2.0/gdk-pixbuf*" when I had an error when compiling.

Experimenting a bit I can get lightspark to run by omitting "radeon.modeset=0" from the yaboot.conf.  This causes the software rasteriser to be used, but nothing sensible appears on a youtube video or on the test swf.  This is not surprising as performance generally is rubbish when ubuntu is run like this (i think most comments on this forum about ubuntu being slow can be tracked down to not having this option in their yaboot.conf). 

I guess my next step is to try out different versions of Mesa, but I have no idea how to do this.  Do I need to uninstall the currently used version first?  If so how do I do it?

I'm a great believer that all answers can be found on the internet as generally somebody has already had the problem and found a solution, but in this case I've drawn a blank!!  Hence, this thread!  Apart from articles announcing the powerpc version of lightspark I haven't found anything on google.  I'd encourage all powerpc users to try out lightspark and support its developers.  You may have better luck than I have!  Afterall, powerpc users are surely going to have the most to gain from the development of a modern open source flash player.  Flash is going to be around for a while yet!!!

---

### Post by rsavage on 2011-01-28
For those new to Ubuntu I thought I'd add a bit about the other open source flash player that is also being developed - gnash!  It can play SWF files up to version 7, as well as some features of 8, 9 and 10.  From the Ubuntu Software Centre install "Gnash SWF viewer" and "browser-plugin-gnash". 
 
The version in maverick works on YouTube videos unless they are TV programmes or the like.  Sadly for me, my computer isn't fast enough for it so I've also installed a few firefox extensions that get around this.  These are also really easy to install - you just click the button in the link. 
 
The first firefox (or opera) extension I use is FlashVideoReplacer ([https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)).  As this link ([http://ubuntuforums.org/showthread.php?t=1487327&page=4](http://ubuntuforums.org/showthread.php?t=1487327&page=4)) explains, the developer recommends you install the gecko-mediaplayer (watch out for the typo in the instructions!).  Using FlashVideoReplacer allows you to watch YouTube videos 'normally' i.e. no command line stuff that I've read about on other threads!  Just a warning, I tried it with the vlc plugin and that really messed some settings up which I don't think I've fully sorted out yet.  It set audio playback through PulseAudio which resulted in choppy playback. 
 
The other extensions I have had a play around with are FlashBlock and QuickJava.  The first allows you to block flash playing on a website.  You can then select to individually play the flash or setup a whitelist of sites where you always want flash.  The latter allows you to setup an enable/disable button for the flash plugin.  Ideally, I'd like a combined extension incorporating the enable/disable button and the whitelist.  Does anybody know of one? 
 
Other ways to watch YouTube is by using html 5 ([http://www.youtube.com/html5](http://www.youtube.com/html5)).  This works quite well for videos coded in h.264.  You'll need Midori or Epiphany browsers, but sadly the number of videos encoded in this format are very few and I don't think it's worth the while installing them just for that.  You also can't play in fullscreen easily.  Opera (and Midori and Epiphany) can play WebM videos, but for me the playback is choppy (similar to gnash).  I'd love to know if and how somebody has got WebM playback running well.  
 
 
Back to lightspark.......I failed to compile the latest mesa driver, but I was able to install libgl1-mesa-dri 7.10 from debian experimental ([http://packages.debian.org/experimental/libgl1-mesa-dri](http://packages.debian.org/experimental/libgl1-mesa-dri)).  This has solved the error message and the browser/windows closing, but I just see a black or white rectangle - no flash playback.  I'm wondering if this is because my other libgl1 packages are still stuck on 7.9?  I really could do with some help in updating those. 
 
Lightspark uses gnash to play old versions of flash and it is interseting to see how much it 'falls back' onto gnash.  Even on the BBC website that won't work unless you have a 10 flash player installed.  For example, flash on the BBC iplayer site falls back to gnash, but gnash hasn't actually got the necessary features implemented yet to play the video.  However, video and audio clips on the news site does use lightspark (this is actually what I wanted lightspark for so that is good). (Btw, UK users should check out get_iplayer in the Ubuntu Software Centre, but you'll probably want to compile the latest version so that you can download videos of the appropriate quality).  It might be my imagination, but I think gnash plays better alongside lightspark.

---

### Post by rsavage on 2011-01-29
Just a quick update ....

I've now got the latest versions of the other mesa packages installed.  I added 

[FONT=Courier New]deb [http://*ftp.de.debian.org/debian*]("http://%3Ci%3Eftp.de.debian.org/debian%3C/i%3E") experimental main[/FONT]

[FONT=Verdana]temporarily to the repository list and used Synaptic Package Manager to update libgl1-mesa-glx.  That sorted out the dependencies and appears not to have broken anything.

However, flash still does not play correctly for me.  I'm out of ideas now so it would be good to hear from somebody else who's had a go with lightspark?
[/FONT]

---

### Post by 1984dc on 2011-04-13
I just tried to download and install lightspark, but I am getting the following problems

```
sudo apt-get install lightspark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lightspark

```

I downloaded the ppa properly and added the entries to the sources.list (using the update manger).

Any suggestions would be great.

Many thanks,

Dc

---

### Post by 1984dc on 2011-04-18
Bump

---

### Post by avtolle on 2011-04-18
> **1984dc said:**
> I just tried to download and install lightspark, but I am getting the following problems

```
sudo apt-get install lightspark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lightspark

```I downloaded the ppa properly and added the entries to the sources.list (using the update manger).

Any suggestions would be great.

Many thanks,

Dc
If you are on a ppc mac, it appears to me that the packages in the ppa are version 0.4.6.1, which appear to be i386/amd64 only.

---

### Post by plecebo.mc on 2011-04-18
this is very intresting and i apperciate you posting this i have the same computer but i have been trying to solve this problem for some time unfortunatly im no guru but i might try this out. also im only running 498MiB of ram. how much are you running and who thinks that bumping it up to the max of 1Gb will help with the choppy video that gnash spits out every 2 seconds? P.S firefox just destroys my cpu usage :(. and dont forget your ibookg4 is still eligable for a free battery if yours is the type recalled i got anew on this year check the fourm about the ibook g4 batteries

---

### Post by plecebo.mc on 2011-04-23
i was compiling the source but after all iv done im stuck at the make command


this is where it trips up on me and because of this it fails:
.
.
.
 19%] Building CXX object CMakeFiles/spark.dir/backends/decoder.cpp.o
/home/matt/Downloads/lightspark-0.4.6.1/backends/decoder.cpp: In member function ‘virtual bool lightspark::FFMpegVideoDecoder::decodeData(uint8_t*, uint32_t, uint32_t)’:
/home/matt/Downloads/lightspark-0.4.6.1/backends/decoder.cpp:232: warning: comparison between signed and unsigned integer expressions
[ 20%] Building CXX object CMakeFiles/spark.dir/backends/extscriptobject.cpp.o
.
.
[ 36%] Building CXX object CMakeFiles/spark.dir/parsing/amf3_generator.cpp.o
.
(it spazzes out here but i copied the last 3 lines if you need me to i could figure out how to post a log up too)
.
make[2]: *** [CMakeFiles/spark.dir/parsing/amf3_generator.cpp.o] Error 1
make[1]: *** [CMakeFiles/spark.dir/all] Error 2
make: *** [all] Error 2

______________
im running an ibook g4 ppc with ubuntu 10.04 LTS
im using lightspark-0.4.6.1

can any one help me out here ?

---

### Post by linuxftw3 on 2011-05-01
in natty narwhal lightspark is in the repositories just  do sudo apt-get install browser-plugin-lightspark for the browser plugin   in terminal .  and do sudo apt-get install lightspark in terminal to get the player.

---

### Post by linuxftw3 on 2011-05-01
> **avtolle said:**
> If you are on a ppc mac, it appears to me that the packages in the ppa are version 0.4.6.1, which appear to be i386/amd64 only.


in natty narwhal repositories there is lightspark for ppc . just do sudo apt-get install browser-plugin-lightspark in terminal.

---

### Post by linuxftw3 on 2011-05-01
> **plecebo.mc said:**
> i was compiling the source but after all iv done im stuck at the make command


this is where it trips up on me and because of this it fails:
.
.
.
 19%] Building CXX object CMakeFiles/spark.dir/backends/decoder.cpp.o
/home/matt/Downloads/lightspark-0.4.6.1/backends/decoder.cpp: In member function ‘virtual bool lightspark::FFMpegVideoDecoder::decodeData(uint8_t*, uint32_t, uint32_t)’:
/home/matt/Downloads/lightspark-0.4.6.1/backends/decoder.cpp:232: warning: comparison between signed and unsigned integer expressions
[ 20%] Building CXX object CMakeFiles/spark.dir/backends/extscriptobject.cpp.o
.
.
[ 36%] Building CXX object CMakeFiles/spark.dir/parsing/amf3_generator.cpp.o
.
(it spazzes out here but i copied the last 3 lines if you need me to i could figure out how to post a log up too)
.
make[2]: *** [CMakeFiles/spark.dir/parsing/amf3_generator.cpp.o] Error 1
make[1]: *** [CMakeFiles/spark.dir/all] Error 2
make: *** [all] Error 2

______________
im running an ibook g4 ppc with ubuntu 10.04 LTS
im using lightspark-0.4.6.1

can any one help me out here ?


upgrade to 11.04 natty narwhal , and you can install it from the repositories  like this:
in natty narwhal  just  do sudo apt-get  install browser-plugin-lightspark for the browser plugin   in terminal .   and do sudo apt-get install lightspark in terminal to get the player.

---

### Post by 1984dc on 2011-05-02
Thats great guys, can't wait for to upgrade (i haven't got round to it yet)!

---

### Post by spaceballl on 2012-05-07
Hey guys!

I know this post is basically a year old, but I'm about to get Ubuntu up and running on my iMac G5 17"...

and i want to know... what's better now on PPC? Gnash? Lightspark?

---

### Post by bblackbelt on 2012-09-30
> **spaceballl said:**
> Hey guys!

I know this post is basically a year old, but I'm about to get Ubuntu up and running on my iMac G5 17"...

and i want to know... what's better now on PPC? Gnash? Lightspark?


have you found an answer?

---

### Post by wildmanne39 on 2012-10-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

