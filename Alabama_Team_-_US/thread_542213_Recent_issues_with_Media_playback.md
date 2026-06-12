---
title: "Recent issues with Media playback"
date: 2007-09-03
forum: Alabama Team - US
---

### Post by MerlinsLair on 2007-09-03
I've done some research but am at present abit confused here. Not exactly sure when my issue began showing up but for some reason my sound is acting up for starters.

When I boot into Ubuntu, the splash screen does it's thing and then the logon screen appears (sound is good here) then nautilus loads (sound present here too) but after that, gaim has no sound and anytime I attempt to playback a clip or any flash content (like from CNN or C/net) Firefox will freeze up. I have to "force quit" it to get it to close.

Read somewhere where Compfuzion (or whatever it's called) might be a culprit but I don't have it installed on my system. I had Beryl but uninstalled it to see if it made any difference. No joy.

The gist I'm getting is that an update may be the culprit instead but I'm a bit at a loss as to what to look for at this point.

I've checked sound settings in Gaim and they show as good. I've of a mind that this is two unrelated things but still, what's a solution for this?

Please keep in mind that I'm also relatively new to Ubuntu and am learning as much as I can. ;)

BTW, if this would be better off in a different forum then by all means move it. Just figured some of the Alabama gang might have an answer. :)

---

### Post by crane on 2007-09-03
Try double clicking you volume control. When the panel pops up select file>change Device. Look here and make sure the right sound card is selected.
Did it work before or is this a new install?

---

### Post by MerlinsLair on 2007-09-04
> **crane said:**
> Try double clicking you volume control. When the panel pops up select file>change Device. Look here and make sure the right sound card is selected.
Did it work before or is this a new install?

OK, tried both settings and still no dice. No, this happened after an upgrade I'm sure. Was working just fine until then. I just didn't catch it right afterwards due to a lot going on at once, I suppose.

The other odd thing was Firefox freezing up during flash palybacks like CNN.com. Weird. Unless I'm developing a driver issue all of a sudden?

---

### Post by crane on 2007-09-04
Try checking under System>Preferences>sound.
Should be a tab there to for systems sounds. make sure that is enabled. I don't know what they did but my sound got worse after upgrading ro Feisty. I can no longer use my Mic at all.
 I got my sounds working by enabling many of the options in my sound control panel and messing with those.
 I also have Gutsy installed to play with but i still cannot get sound working there either. Same as you now that I think about it. Boot screen sound is good, after system is up, no sound.
 It appears Ubuntu is moving backwards with sound issues. I'm going ti keep messing with it to see what I find.
What type of sound card do you have? I have Audigy myself and it will be the last Creative labs product I own.

---

### Post by MerlinsLair on 2007-09-05
This is what I pulled from the Everest Home Edition scan of the machine if it helps.


Motherboard Name ECS 755-A (5 PCI, 1 AGP, 1 CNR, 2 DIMM, Audio, LAN)
Motherboard Chipset SiS 755, AMD Hammer

Multimedia
Audio Adapter SiS 7012 Audio Device

---

### Post by WillieDaPimp on 2007-09-10
I'm not sure if you've tried running 'alsaconf' from the command line, but it seems to straighten out some sound issues. It may not even be installed by default, I can't remember' if not install it and try running it and see if it helps with your sound. Also you may need to reboot after running alsaconf, I have a friend running Mandriva who has to reboot after alsaconf is ran on his computer. Just figured it might be worth trying if nothing else is working for you.

---

### Post by MerlinsLair on 2007-09-10
Well, to be honest with you, I wound up reinstalling Ubuntu (partially due to other issues that were ongoing) and this seemingly has solved the problem at the moment.

Not too sure just what all had gone wrong but it seemed to have stemmed from an update. Not a good thing.

Now, I'm left with the task of trying to get my windoze drive accessable again. So far, no luck. But, I've got the time...it'll come around sooner or later. :)

Thanks for the advice, guys. ;)

---

