---
title: "trouble downloading a valid disk image"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Malimbar04 on 2007-03-17
I'm having a very basic problem that I can't get around. I'm running Mac OS X 10.4.9 right now, trying to download a liveCD to try ubuntu, to possibly install it later. I've downloaded the iso disk image literally about twenty times. My download manager still holds the history of six seperate times, usually from different mirrors. 

After I download the image, I can not verify it. Sometimes it says "invalid argument", sometimes it says "no checksum to verify". I don't know exactly what all the errors were, but there is always an error of some sort. can anybody help me?

---

### Post by steve101101 on 2007-03-17
Im not sure about any mac issues but if the iso made it to your desktop, just burn an image disc.

---

### Post by Malimbar04 on 2007-03-17
I just tried. Disk utility says that it was unable to because of a medium write error... so I tried a different CD. The next CD says...failed to calibrate the laser power level for this media... maybe I have two bad CD's... so I try again. The device failed to respond properly, unable to recover or retrieve. well, I tried and failed to burn some images a while ago of something else, maybe it has some old data? I'll try again with a CD from a different part of the stack. OK... I'm going through a lot of cd's, but it isn't saying problems that I would expect to be from the disk image. 

I'll try one more time for now. it says it's burning it. it says it's "writing track". It's lasting longer this time. it's taking so long... I have to go to work. well, I'm back now and it says "unable to burn ubuntu-6.10-desktop-powerpc.iso    verification of the burn failed. sigh. I don't know what to do still.

---

### Post by chengt on 2007-03-25
I'm having the same problem with a " The burn failed because of a medium write error" trying to burn the ubuntu cd using mac's disc utilities.

I'm getting the same thing using hdiutil so it's not looking good.

```

chengin:~ chengt$ hdiutil burn ~/Desktop/ubuntu-7.04-beta-desktop-amd64.iso 
Preparing data for burn
Opening session
Opening track
Writing track
.......
Closing session
Finishing burn
................................................................................................................................................................................................
Burn failed
The burn failed because of a medium write error.
The burn failed because of a medium write error.
hdiutil: burn failed - The burn failed because of a medium write error.

```

I'm going to try on windows vista and see if it works.

---

### Post by chengt on 2007-03-25
Well I tried using Cheetah on Windows Vista and it still didn't verify.
I've gone thru about 10 cd-rs now. Maybe CompUSA brand just sucks.

---

### Post by sammas on 2008-02-20
Try burning the disk at a slower speed.  I was getting disk write errors trying to burn at 24x on Macbook Pro.  I tried 8x and it worked like a charm.

---

### Post by twodayslate on 2008-02-20
You can always request a CD if you can't get it to work.

---

