---
title: "Is my ati x1950 pro working as it should?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-09-29
[IMG]http://img.photobucket.com/albums/v294/kutulu/Screenshot-2.png[/IMG]

This is what Ubuntu is showing in the restricted drivers list and while I was using GIMP last night I noticed some lag in how it was working. I was wondering if I needed to download new drivers to get it to work properly.

On the same note I also noticed some bad playback of my cd player as well, skips on a cd with no scratches, how can I update the drivers for my Audigy 2 Value?

---

### Post by overdrank on 2007-09-29
> **devosion said:**
> [IMG]http://img.photobucket.com/albums/v294/kutulu/Screenshot-2.png[/IMG]

This is what Ubuntu is showing in the restricted drivers list and while I was using GIMP last night I noticed some lag in how it was working. I was wondering if I needed to download new drivers to get it to work properly.

On the same note I also noticed some bad playback of my cd player as well, skips on a cd with no scratches, how can I update the drivers for my Audigy 2 Value?

Hi as for your Ati card, if you have not installed any other drivers for it then you may want to. But let me warn you that it may cause your xorg to crash. As for your cd playing have you installed the restricted formats?

---

### Post by devosion on 2007-09-29
To the cd player question, no but incidentally it works sometimes and other times doesnt work. Like right now I just tried to play a cd but nothing came out, although I have a feeling this might have something to do with my recent update. Im guessing im going to have to do some searching to find the codec downloads.

What exactly is the xorg? And crashing is never good...

---

### Post by overdrank on 2007-09-29
> **devosion said:**
> To the cd player question, no but incidentally it works sometimes and other times doesnt work. Like right now I just tried to play a cd but nothing came out, although I have a feeling this might have something to do with my recent update. Im guessing im going to have to do some searching to find the codec downloads.

What exactly is the xorg? And crashing is never good...

HI here are some links to the restricted formats and codecs
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As for you xorg it is what makes your desktop session and by crashing I mean you will reboot to a blue screen telling you that your xorg is not configured. Then you will have to use this command 
```
sudo dpkg-reconfigure xserver-xorg
```
I would advise you to search the forums for that card and learn from there experience. Good luck!

Edit also on the cd playing I would suggest VLC but that is opinion

---

### Post by devosion on 2007-09-29
I couldnt find much on the forums but on a hunch I ran a search of xorg in terminal and found this...

i   xserver-xorg-video-ati          - X.Org X server -- ATI display driver    

Im not sure if that is what came installed in the system but how would I check that? Also how can I check to see what version of xorg and glibc im running?

Thanks in advance. :)

---

### Post by overdrank on 2007-09-29
> **devosion said:**
> I couldnt find much on the forums but on a hunch I ran a search of xorg in terminal and found this...

i   xserver-xorg-video-ati          - X.Org X server -- ATI display driver    

Im not sure if that is what came installed in the system but how would I check that? Also how can I check to see what version of xorg and glibc im running?

Thanks in advance. :)

HI I can not answer your question because I have not used that card as of yet. But here is a search that turn up your card.
[http://ubuntuforums.org/search.php?searchid=27948768](http://ubuntuforums.org/search.php?searchid=27948768)
Like I said I would research and learn as much as I can because I have tried to several users of that card and it can turn in to a hassle. I am by no means trying to scare you just trying to help and learn as much as I can and also suggest the same for you. Good luck!

---

### Post by devosion on 2007-09-29
Thanks much. The link outta help me out quite a bit. I'll try to take it as slow as I can but im a little anxious to get Guild Wars up and running again, read a bit and found out it runs well on Ubuntu and linux based OS' in general. Anyways im dead tired and out.

---

### Post by overdrank on 2007-09-29
> **devosion said:**
> Thanks much. The link outta help me out quite a bit. I'll try to take it as slow as I can but im a little anxious to get Guild Wars up and running again, read a bit and found out it runs well on Ubuntu and linux based OS' in general. Anyways im dead tired and out.

Ok and a wise decision I might add and good luck and enjoy! :guitar:

---

