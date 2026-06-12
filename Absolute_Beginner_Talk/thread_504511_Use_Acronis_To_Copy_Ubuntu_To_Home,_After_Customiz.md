---
title: "Use Acronis To Copy Ubuntu To Home, After Customizing?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by sandmanfvr on 2007-07-19
I haven't been on here in a while, wow.  I have got an iBook and I got old Winblows on a tower.  I do audio video stuff now with ghost hunting (yes very serious, [www.ghosttn.com](www.ghosttn.com)).  I have an 8mm digital (uses firewire) and I got an audio recorder.  I capture video, then export and convert.  I capture audio (I have to use windows for the software, nobody and I mean nobody has done it that I found in Linux or OS X.  Recorder:  Sony ICD-P28 )  and then pictures from SD.  I am use to the step with my audio recorder, then after that the hours of listiening to audio in audacity/goldwave/sound studio can be done in any OS.  

Now, what I want to do is install ubuntu here at work, then add vlc, all the restricted multimedia stuff, kino if needed, any video converting software (I need suggestions so I can make at least wmv's or something out of the capture).  After I get it setup, I want to take it home.  WHY? **I have dial up and it is very slow.**  It sucks, but I can't do all this updating via the web, so do it here and take an image. :)

I have at work here and at home a Sound Blaster Audigy 32 card with firewire port and wonder if **the fireware port** will work, I know the sound card will not, I can use on board sound that is fine.  I got an Nvidia card here at work and an ATI X1600 at home.  How will that work?  Just wondering all of this, want a custom tower that is another alternative so I have more options in audio/video editing.  Thanks.

---

### Post by sandmanfvr on 2007-07-19
Anybody?

---

### Post by starcraft.man on 2007-07-19
> **sandmanfvr said:**
> I haven't been on here in a while, wow.  I have got an iBook and I got old Winblows on a tower.  I do audio video stuff now with ghost hunting (yes very serious, [www.ghosttn.com](www.ghosttn.com)).  I have an 8mm digital (uses firewire) and I got an audio recorder.  I capture video, then export and convert.  I capture audio (I have to use windows for the software, nobody and I mean nobody has done it that I found in Linux or OS X.  Recorder:  Sony ICD-P28 )  and then pictures from SD.  I am use to the step with my audio recorder, then after that the hours of listiening to audio in audacity/goldwave/sound studio can be done in any OS.  

Now, what I want to do is install ubuntu here at work, then add vlc, all the restricted multimedia stuff, kino if needed, any video converting software (I need suggestions so I can make at least wmv's or something out of the capture).  After I get it setup, I want to take it home.  WHY? **I have dial up and it is very slow.**  It sucks, but I can't do all this updating via the web, so do it here and take an image. :)


Hmmm, I see interesting... ok well first thing make sure your boss or whoever owns the computer is ok with you installing Ubuntu on it. I will assume you have permission. Installing Ubuntu isn't so difficult to install, if you need help getting the dual boot look [here]("http://www.psychocats.net/ubuntu/installing") and [here]("http://users.bigpond.net.au/hermanzone/") (first is for Live CD, second alternate (in the orange box)). After installing, if your looking for video editing software you might want to give Cinelerra a try, it's a neat program I found [here.]("http://cv.cinelerra.org/getting_cinelerra.php") As for converting programs, depends on what you want.... [here is a list of programs to try]("http://linuxappfinder.com/multimedia/videodvdencoders"). Give konverter a shot, and keep the site handy if you ever have to find another program.

Now as for the imaging, there will be no problem. Ubuntu quite easily moves from system to system being imaged with little effort. The only thing I will warn against is if you have conflicting cards (i.e different makes) then I would strongly recommend against installing your drivers until you get on your home machine. Acronis can do this quite easy though just use the live cd and backup to your preferred media.

> I have at work here and at home a Sound Blaster Audigy 32 card with firewire port and wonder if **the fireware port** will work, I know the sound card will not, I can use on board sound that is fine.  I got an Nvidia card here at work and an ATI X1600 at home.  How will that work?  Just wondering all of this, want a custom tower that is another alternative so I have more options in audio/video editing.  Thanks.

I can't vouch for sound cards, I don't know so much about them with Linux. Firewire may or may not work right away, I'm pretty sure the new kernel has brought lots of improvements in the support so maybe when Gutsy comes that may be fixed (I could be wrong). As for the cards like I said simply ensure you are using generic drivers when you make your image for acronis (ideally please set the driver your using to "vesa").

To make sure you do this open a terminal and type in:

```
sudo dpkg-reconfigure xserver-xorg
```

Keep going through the screens and leaving the defaults for anything you don't know till you get to video section and make sure the driver is set to "vesa" instead of "nv" or any other.

Oh and ideally I'd recommend getting a dsl line at home, imagining like this every 2 weeks or month to get updates might get tedious. Best of luck.

---

### Post by sandmanfvr on 2007-07-19
I am the system administrator here, so yeah I can do that. :)  Just wanted to try and that makes sense on the drivers.  Will have to try it.  Thanks.

---

