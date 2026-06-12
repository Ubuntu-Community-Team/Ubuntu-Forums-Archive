---
title: "iPod Support in FF7.04"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-04-24
Hello,

This is my first time trying out Linux (I'm a total beginner!) 
I recently burned a Live CD of the newly released Ubuntu Feisty Fawn 7.04, and have been using it for a while to test out all the neat applications it has, because I want to make the switch to Ubuntu, not Vista. But after testing it out for a few days now, I have been trying to get my iPod to be read while using the Live CD. I'm wondering if it's possible for me to listen to my music from my iPod while I am using the CD, like what program would I need to download, terminal command to enter, etc. I ask this because I have used a Mac program called Sentui which, when the iPod is plugged in, you can immediately play your songs straight from your iPod without having to copy anything whatsoever, and I was just wondering if Ubuntu Linux has a similar application for me that I could run while I test out Feisty Fawn for a bit.

Thanks

---

### Post by gilforsyth on 2007-04-24
My personal favorite is Amarok, which can play music off of your ipod no problem and has every feature you could need.  Maybe.  Amarok is KDE but it runs pretty well on gnome.  

To install, in terminal, type:
```
sudo aptitude install amarok
```

And as an extra measure, you'll want to install some extra codecs
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

If you are running Amarok and plug in your ipod, Amarok should detect it and ask you what kind of player it is.  After that, you just need to select 'Media Device' and play songs off of it.  

Other options include Rhythmbox, gtkpod, yamipod and banshee.

If your ipod isn't showing up on your desktop when you connect it, or if you have any problems at all, [this thread]("http://ubuntuforums.org/showthread.php?t=103071") is pretty comprehensive.

---

### Post by dswhite85 on 2007-04-24
Thanks for the speedy reply gilforsyth, arigato!
I'll try this out on the Live CD right now, and let ya know how it goes and see if I still have any troubles.
Thanks again.

---

### Post by dswhite85 on 2007-04-24
I'm still unable to play any songs directly from my iPod with Banshee or Rhythmbox. I guess it's because I'm on the Live CD. Although, while on the Live CD, I have had success downloading an individual song, then playing it, downloading the needed codecs automatically, and that worked fine, but one song just isn't enough to listen to while trying to figure out if Ubuntu is right for me, you know.

---

