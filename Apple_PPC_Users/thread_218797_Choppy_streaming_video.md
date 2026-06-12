---
title: "Choppy streaming video"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by oss_monkey on 2006-07-19
Hi all,

I've noticed that video streaming isn't as good as it used to be in Windows. While my audio is good (no popping, no clicking, etc.), it's the video that is suffering. For example, YouTube videos play at around 10fps.

I've observed this under both Opera and Firefox. Swiftfox can't play the videos since I couldn't install codecs for it (I just run it from a folder in my /home directory.

Any ideas on how to fix this? TIA.

---

### Post by x64Jimbo on 2006-07-19
It's likely one of several possible issues:
Is your video card driver installed?
It could be related to you running an older version of flash player. to get around this, I run Windows Firefox through Wine with the latest Flash player and everything runs smoothly. YouTube is not really streaming video as it is streaming Flash movies. There's a difference, even though it may be a very technical one.

---

### Post by oss_monkey on 2006-07-20
> **x64Jimbo said:**
> It's likely one of several possible issues:
Is your video card driver installed?
It could be related to you running an older version of flash player. to get around this, I run Windows Firefox through Wine with the latest Flash player and everything runs smoothly. YouTube is not really streaming video as it is streaming Flash movies. There's a difference, even though it may be a very technical one.

Hmm.. How can I know if my video card driver is installed? I'm at max resolution (1024x768), with respectable color depth (at least 16-bit).

As much as possible I don't use Wine. :)

---

### Post by x64Jimbo on 2006-07-20
Very frequently you can get up to your monitor's maximum potential without using the video card drivers. The generic driver for Linux is quite nice and often fools people into thinking they're all set up. But I can tell you that if you didn't install the driver yourself, you almost certainly do not have it installed. Video drivers for Linux are tricky because they're proprietary (closed-source) and many distributions have rules about including closed source software in the shipping version of their OS. Also, sometimes the license to use the driver from the manufacturer explicitly states that it may not be re-distributed. 
Anyway, if you want to test if you have the driver installed, run this:
glxgears
That's a test of your 3D acceleration. Post your results here. 
If you are pretty sure that you didn't install the drivers, you may want to have a look at EasyUbuntu here: [http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)
It's a special script that will not only install your video card drivers for you, but also a bunch of other useful software that isn't (for one reason or another) included in Ubuntu.

---

### Post by oss_monkey on 2006-07-20
> **x64Jimbo said:**
> Very frequently you can get up to your monitor's maximum potential without using the video card drivers. 

Oh, I didn't know that.

> **x64Jimbo said:**
> The generic driver for Linux is quite nice and often fools people into thinking they're all set up. But I can tell you that if you didn't install the driver yourself, you almost certainly do not have it installed. 

Got it. I'll go try EasyUbuntu.

> **x64Jimbo said:**
> Anyway, if you want to test if you have the driver installed, run this:
glxgears
That's a test of your 3D acceleration. Post your results here. 

I just ran this. The window with the three gears came out, but they moved about one step every 10 seconds or so. With 8MB of RAM on this card, this should move faster, right?!

Will post EasyUbuntu results later. Thanks.

---

### Post by x64Jimbo on 2006-07-20
Yeah, a properly configured video card will make those gears run in the hundreds of frames per second, so it sounds like you don't have the driver installed ;)

---

### Post by oss_monkey on 2006-07-20
Well, I just ran EasyUbuntu and installed the ATI drivers. I'm pretty sure this isn't an Nvidia card.

I restarted (though I'm not sure that was necessary), but glxgears still moves at the same rate.

Also, this came out:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Any idea what that's about? :(

---

### Post by oss_monkey on 2006-07-20
I just remembered that this video card is a Trident Cyberblade Aladdin i1. Dang it, a cursory search of the forums says that many are looking for a driver for this but can't find it.

I Googled it, but found that the trident driver (a generic trident, that is), is already part of the xserver-xorg-driver-trident package, which is already installed on my system.

What's wrong?! This is getting frustrating...

---

### Post by x64Jimbo on 2006-07-22
Unfortunately my experience is limited to nVidia and ATI cards. Wish I could help more.

---

### Post by Brian McConnell on 2006-07-26
Why is this in the PPC section?

---

### Post by avtolle on 2006-07-26
Just wondering the same thing. To OP; if the specs in your sig represent your system, could have something to do with the amount of memory.

---

### Post by oss_monkey on 2006-07-27
While I've accepted that the specs are really wanting, I never had playback problems when this laptop had Windows2000 installed.

I tried playing some videos, and had varying degrees of success.
1) Offline videos worked ok.
2) Websites (like Apple.com's Trailers) that used the mplayer plugin played fine, but the whole movie had to download first. If I streamed it, the audio and video didn't sync.

Any other ideas? :s

PS- The system files point to the proper driver, trident. So it couldn't be the problem, unless the driver was buggy in the first place.

---

### Post by tical2756 on 2007-02-25
i'm having the same problem has anyone cone up with a driver for the cyberblade i1?

---

