---
title: "help with sound, please?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by ahervey85 on 2008-01-23
i am at a loss as to how to get sound working on my laptop. in alsa mixer it comes up says  card is hda intel chip realtek id 268. i tried a search and didnt come up with anything. can someone please point me in the right direction? please?

---

### Post by ahervey85 on 2008-01-23
when i open up alsamixer there is nothing underneath master but i am able to move it up and down same with pcm. could there be a problem there?

---

### Post by biggieshorty on 2008-01-23
I got the same problem here, mate :(


Im at a total loss of why the sound isn't working...It's as if all the devices are installed but yet its all "muted".


I too have the Intel HDA card, with the Realtek ID 268 chip. All the devices seem fired up, yet theres no sound when I test the sound with system-->preferences-->sound or when I try and play mp3's. 

:confused::confused::confused::confused:

---

### Post by Casual Fan on 2008-01-23
Best. Thread. Ever.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Enjoy! :)

---

### Post by OSlinuX on 2008-01-23
try running

sudo alsaconf

in the command line, it will try to autodetect and set up your sound

---

### Post by ahervey85 on 2008-01-23
i have tried the comprehensive sound guide before thanks anyways

---

### Post by ahervey85 on 2008-01-23
i can get my sound card listed and everything just for some reason no sound at all. i was hoping someone out there could help me but doesnt seem like it no matter where i ask for help.

---

### Post by Redptc on 2008-01-23
I think that the sound problem is a real pain. You won't get a lot of help because it's not very important I guess.

If you have the master sound icon in the upper panel it looks like your card is recognized. It is the first call I make when necessary. Move the button to the max position even if you have to move it down then again to the max. Step 2 is to right click on the icon and select ...Open Volume control. Unmute, is that a word, everything but most of all move the Master and PCM control and, again, move them to the max position. After all that I usually have sound again! Very unscientific but it usually works.

I spend most of my computer life without the need for sound so it doesn't matter a lot but I have to thru this process every few days. Lotsa luck! 

Redptc

---

### Post by ahervey85 on 2008-01-23
yeah i wish it was that easy. they are in the max position but there is nothing underneath them like the mm or oo saying muted or not though if that matters.

---

### Post by BandD on 2008-01-23
Many people have had trouble with the Intel HDA chipsets, including me.  Now I'm pretty much a noob to Linux, though I'm a pretty savy everyday PC user.  I found these posts to be particularly helpful:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

The best tip I took from here was editing /etc/modprobe.d/alsa-base:

```
sudo gedit /etc/modprobe.d/alsa-base
```

 and adding this line of code at the end of the file:  

```
options snd-hda-intel model=MODEL
```

Where MODEL is one of the models listed on that page.  Try a few and see if they work.

If that doesn't work, you could try updating your ALSA drivers to version 1.0.15 which has much better support out of the box for the Intel HDA series.  See this post:

[http://ohioloco.ubuntuforums.org/showthread.php?t=530374]("http://ohioloco.ubuntuforums.org/showthread.php?t=530374")

There are other ways out there to update the ALSA drivers as well.  You can search around for them.  But both of these helped me to get EVERYTHING working on my HDA Intel Realtek 260 chipset.  So give it a shot and let us know how it goes.

---

### Post by Redptc on 2008-01-23
Sorry mate, you got the full depth of my experience and knowledge regarding 'sound'!

Anything more complex will need the marines. :(

---

