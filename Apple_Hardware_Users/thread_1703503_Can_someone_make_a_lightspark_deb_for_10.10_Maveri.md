---
title: "Can someone make a lightspark deb for 10.10 Maverick PowerPC"
date: 2011-03-09
forum: Apple Hardware Users
---

### Post by linuxftw3 on 2011-03-09
can someone lock this ??

---

### Post by linuxopjemac on 2011-03-09
there is a ppa for Lucid Lynx and Natty:
[https://launchpad.net/lightspark](https://launchpad.net/lightspark)

---

### Post by rsavage on 2011-03-09
Linuxopjemac are you sure about that?  I don't think there are PPC versions, but please correct me if I am wrong.

If you don't want to compile then you could add temporarily the natty or debian experimental repositories to your sources and install Lightspark that way.  A load of other stuff will be updated too though so it may break something?  I haven't tried this, I'm just speculating.

I had a go at compiling Lightspark as detailed in this lengthy post [http://ubuntuforums.org/showthread.php?t=1670102](http://ubuntuforums.org/showthread.php?t=1670102).  Haven't tried again, but if you tell me what the problem is I may be able to help?

It's good to hear that somebody else is giving it a go!

---

### Post by rsavage on 2011-03-09
Probably has a never ending list of things you have to update....... but [http://packages.debian.org/experimental/utils/lightspark](http://packages.debian.org/experimental/utils/lightspark) is where there is deb for PowerPC.

---

### Post by linuxopjemac on 2011-03-09
You are right, it's in experimental. I would not pull in too much from experimental, I would just try to install Lightspark in the Mavrick environment. If that does not work, I would leave it. Lightspark has not been optimized for PPC anyway. It's far from working. That's why you find it in experimental. It's under heavy development still.

PPA is indeed for i386 / amd. Sorry:
[http://allievi.sssup.it/techblog/](http://allievi.sssup.it/techblog/)

---

### Post by rsavage on 2011-03-09
Well I think it is definitely worth trying it out.  Somebody has reported that the version in natty works on a PS3 [http://psx-scene.com/forums/f149/anyone-get-flash-support-debian-82423/](http://psx-scene.com/forums/f149/anyone-get-flash-support-debian-82423/).  I wonder though if they are seeing gnash playback or actually lightspark animation? 

I think my problem was radeon (maybe not having KMS?) related, rather than PPC related.  That was two versions ago now, and things will have probably improved!

---

### Post by linuxopjemac on 2011-03-10
Well, try it out. I would be interested in your results. My PowerBook G3 is too old anyway to try flash.

---

### Post by rsavage on 2011-03-10
Just to be clear I meant it is worth trying out lightspark in general.  Compiling cannot be that hard, because, well, I did it.  I will return to lightspark, but at the moment I have other irons in the fire.  Currently trialling a more 'unity' desktop with 'gnome-applet-globalmenu' and 'window applets' which I have/about to compile.  Can setup another thread about this if anybody is interested.  It is by setting yourself projects like this that you get to learn stuff.  Way more and faster than a general user.  So that is why I say it is worth persevering.  Ultimately, it may not work, but you are guaranteed to have a better understanding of ubuntu/linux/etc by seeing it through and not giving up.  What have you got to lose anyway? If you find a problem that is new then report it to the developers and hopefully it will get fixed in future versions.

---

