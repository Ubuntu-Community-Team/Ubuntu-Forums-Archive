---
title: "Newest iMac having odd bugs with 8.04LTS..."
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by ov3rcl0ck on 2008-07-25
First off I install Ubuntu 8.04LTS, so after installing i rebooted and noticed the sound didn't work because there was no log-in music so I figured it was something to do with the drivers, I didn't bother dealing with it then i was all about getting it set up for programming and network. So i install all my software, update, reboot, and it works fine(still no sound though), so i decide to change the theme, it works, but the next day i log on and i see that none of the panels where loading, I didn't know what to do... so i reinstalled, did the same thing but used a different theme and installed avant(awm), rebooted, samething, i reinstall, i set it up, same thing. I'm sick of it and if i can't use the theme i want then i will just convert to using another Debian based OS, but i really like ubuntu and i don't want to have to do this, what is wrong with my interface? And can i get the sound to work?

Sorry for the long entry btw.

---

### Post by cyberdork33 on 2008-07-25
Did you ever stop to think that maybe there is a problem with the theme you are trying to use?

Please check the FAQ about your sound problem. I think that the same solution that works for MacBook Pros will work for you, but if not, I know there is an ALSA patch.
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

### Post by Brightbelt on 2008-07-27
I may be repeating Cyber's link, but this might be a condensed, easier way to swallow this. First, to see if you have an hda intel sound card, or something listed like an ALC885, run this in the terminal:

```
cat /proc/asound/card0/codec#* | grep Codec
```

If this brings up an hda intel or ALC type sound card, then you could try what I did.

I ran this:

```
sudo gedit /etc/modprobe.d/alsa-base
```

That brought up a file (in root mode so I could edit it). And I added this at the end of the file:


```
options snd-hda-intel model=imac24
```

And then I saved the file and rebooted. Now this worked for my 24" aluminum iMac, but I don't have the most recent one either. 

So you might get different results. Just a friendly warning...
I hope this helps.   Frank B.

---

