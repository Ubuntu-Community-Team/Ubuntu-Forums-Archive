---
title: "Threw my xp out the window...now I need a little help"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by rubix64 on 2007-05-03
I just made the switch from xp to running nothing but feisty and Im loving it but I need a little help.

1) Im having trouble viewing dvd's via gxine or mplayer. I keep getting:  'error opening/initializing  
     the video_out (-vo) device' any ideas? 
2) Now that Im running ubuntu on my machine what would be the best way to access windows software I need i.e cs2, PremierePro, Fritz Chessbase  etc?

Sorry, I know these are probable prettye elementary things but I'd appreciate any help that you could give me.  I'm also searching the forums for answers to things popping up along the way so I hope to not burden the forum with much more of these....

Thanks in advance,
rube

---

### Post by mi_were on 2007-05-03
> **rubix64 said:**
> I just made the switch from xp to running nothing but feisty and Im loving it but I need a little help.

1) Im having trouble viewing dvd's via gxine or mplayer. I keep getting:  'error opening/initializing  
     the video_out (-vo) device' any ideas? 
2) Now that Im running ubuntu on my machine what would be the best way to access windows software I need i.e cs2, PremierePro, Fritz Chessbase  etc?

Sorry, I know these are probable prettye elementary things but I'd appreciate any help that you could give me.  I'm also searching the forums for answers to things popping up along the way so I hope to not burden the forum with much more of these....

Thanks in advance,
rube

With regards to the windows software try installing them using "wine" there are very good threads on it or simply google it. It is pretty straight forward

[http://www.winehq.com/site/howto](http://www.winehq.com/site/howto)
[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine)
[http://ubuntuforums.org/showthread.php?t=431498&highlight=wine](http://ubuntuforums.org/showthread.php?t=431498&highlight=wine)

---

### Post by tophatandy on 2007-05-03
you must have more than one program that runs videos open.. if you close the other you should be able to use one (I prefer totem, but it cant play dvd menus.. so next I suggest Gxine) just make sure you have the right codecs.. I think you have to type ```
sudo apt-get install libdvdread3
```
or something like that in terminal

WINE is an emulator that sometimes allows you to run windows .exes files..

hope that helped 
-Andy

---

### Post by teddybairs1 on 2007-05-03
Wine will run a lot of windows programs, give it a try. I usually launch winefile and navigate to the executable through the wine file browser.

I think I understand what you're asking regarding the DVDs. By default, Ubuntu will not play encrypted dvds (pretty much any store bought DVD) because of legalities and licensing nonsense. What you have to do is find the libcssdvd .deb package. There are a number of places where you can download it from. I recommend doing a search on this forum for "medibuntu". This is the repository for proprietary software which isn't included in the regular Ubuntu repositories because of grey area legalities. Do the search and you should turn up the instructions on how to add this to your repositories list. You probably also want to add w32codecs.

This is the actual web page to get them:

[http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/](http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/)

These are the lines you add to Synaptic to add Medibuntu's repos to your list:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Open up Synaptic. Go to Settings-->Repositories-->Third-Party Software, and then hit Add.
Copy and paste each of the lines, the entire line, into the box.
Reload.

Do a search in Synaptic for libdvdcss2 and w32codecs. Mark them off, and then hit apply.

This should fix your dvd problem.

---

### Post by kittyhawk63 on 2007-05-03
.

---

### Post by rubix64 on 2007-05-03
whew! I never expected so much help! thanks guys.

So...before I ever got to read the replies I followed the beginner forum sticky on how to set up DVD etc, pasted all the appropriate lines in and I believe I have the codecs etc installed/ However the dvd does now work,  but continually freezes after 20 seconds. Thge crtl-alt-bkspace wont work. only hard reset....

Any thoughts guys?

Again thanks for the great help, I should be up and running soon !

---

### Post by PARO on 2007-05-03
Try VLC media player if you don't want to worry about installing codecs and such, it plays dvds fine, just download and play.  It's a good fallback too in case some file doesn't want to play with other media players.

About windows apps, you can also run vmware to run a virtual windowsXP while under Ubuntu, in case wine doesn't work with one or more of those programs.

---

### Post by rubix64 on 2007-05-04
O.K

Well VAL installed and the same thing happed as with the other media players...it froze the system about 10-15 seconds into play.

same thing happened while trying to view youtube video as a test.

strangely enough the multimedia file in the /examples with nelson mandella ...played video just fine...

stumped - can anyone help?

thanks 
Rube

---

### Post by teddybairs1 on 2007-05-04
gxine and mplayer both run on the xine engine. Youtube runs on adobe flash player 9. What kind of a graphics card do you have? Are you running a laptop or a desktop? How much video memory do you have available. My card's 128mb. I do have problems at times with flash freezing my browser in youtube, but it doesn't cause my entire system to freeze. It almost sounds like X doesn't like something about the video output. Any video output. Have you tried playing video with totem? It's just called "Movie Player" in the menu, but it runs on the gstreamer engine by default. Try running video with that and see if it freezes again. If it does, we know that it's not the video engines.

To be honest it sounds to me like your video driver. I'm not an expert by any stretch, but if we rule out software glitches between the three possibilities (xine, gstreamer, flash) then we have to go to hardware. What video card do you have?

---

### Post by rubix64 on 2007-05-04
O.K. I might have the problem...

My video card is an ATI Radeon 7200  [http://ati.amd.com/products/radeon7200/index.html]("http://ati.amd.com/products/radeon7200/index.html") 

could the fact that it has only 64Mb of SDR memory be the problem ? If so whats the best fix....get a video card? if so any recommendations?

---

### Post by LaurelLynn on 2007-05-04
That amount of memory will not cause a problem, since DVD doesn't require 3D.

Low system RAM is usually a bigger issue since DVD involves a lot of caching.  Make sure DMA is enabled for the harddrive.

---

### Post by teddybairs1 on 2007-05-04
But it might be the ATI driver. I've read some horror stories about ATI here on the forum. LaurelLynn is right though, 64MB of SDRAM should be enough to run video without a problem. I wouldn't go less than that in general, but to run video, it's not the size of the memory that's the problem.

How much system RAM do you have? Ubuntu generally needs about 256 MB of RAM and no less to run properly. I generally recommend no less than 512. 1GB is better.

---

### Post by PARO on 2007-05-04
DVDs play fine for me on a family computer with 128mb ram and no video card, so your video card is fine I'm sure.  Did you get the restricted drivers for your card through the restricted drivers manager (I'm not sure there is such a thing for the ATI cards, I've got Nvidia on mine, and that set it up anyway), if it's a driver issue it's worth checking.  The only time I had any freezing or crashing going on with video was when I ran out of space in my / partition, and when DVD ff-ing in xine.  I'm not sure that's applicable to you at all though.

---

### Post by kvonb on 2007-05-04
Did you install the "restricted driver" for your card?

If not, open the "restricted drivers manager" from menu->system->administration, and click on "enable".

If you do decide to buy a new video card, get an Nvidia.

Not the latest and greatest, maybe a slightly older one would be the best supported, and it might be cheaper too :).

Is your video card AGP or PCIE?  The PCIEs are a bit of a problem, especially with the ATIs.

---

### Post by rubix64 on 2007-05-04
Hmmmm.... 

re: restricted driver for my video card -The only to Items available to enable in the Restricted Drivers Manager are  VMware Machine Monitor & VMware network driver ..... :confused: 

RE: my ATI Radeon card - the bus type is PCI...

RE: RAM, I have 500MB RAM on a pentium4 with a 1.6 GHz processor


Thanks for all the help you guys....what do you think I should try now?

Rube

---

### Post by maddog39 on 2007-05-04
>  WINE is an emulator that sometimes allows you to run windows .exes files..
_**W**_ine _**I**_s _**N**_ot an _**E**_mulator, its a recrusive acronym and it even says it on the WineHQ main page. :D

As far as restricted drivers. This just means you will need proprietary video drivers, just like you do in windows. Where you have to either download or install from a CD your graphics card drivers. In linux (or more specifically Ubuntu), they make it easy for you. Somewhere under the system menu is a tool where you can check off a box and it will automatically install and configure your video drivers. But since I dont run/have edgy, I have no clue what its called or where it is. But I believe it's called Restricted Drivers Manager or something of the like.

---

### Post by imon9 on 2007-05-04
actually regarding the video problem with mplay..i had them before...
you will have to open mplayer preferences and use x11 as your video rendering engine... or GL (try them out...) 

there is a documentation somewhere at mplayer homepage... lazy to google it for u... :p

---

### Post by rubix64 on 2007-05-04
Arrrgh!

O.K. .....

I just realized that audio makes my platform freeze too.

I tried to play a cd via Amarok and just like the video problem...it just froze.

help please?

---

### Post by maddog39 on 2007-05-04
You need libdvdcss (which is illegal in the US) to play DVDs. Someone suggested you install libreadcss, but thats only half of it.

---

### Post by rubix64 on 2007-05-04
install instructions for libdvdcss

...anyone?

thanks!

---

### Post by davahmet on 2007-05-04
The freezing with audio and video is most likely not caused by your video card drivers.  I would first suspect DMA for your DVD-drive.  Under "Services", check that hdparam is enabled.  By default it is not.  This should help a bit with the freezing.

As for your Windows software, you nmay or may not have some success with WINE.  While many titles work fine with WINE (personally I prefer Crossover to handle WINE configuration), many do not.  You'll have to check support forums for WINE to find out what works and what doesn't.  I wish I could give you better support for running these, but really the problem is because the software vendor simply doesn't want it run on Linux for whatever reason.

---

