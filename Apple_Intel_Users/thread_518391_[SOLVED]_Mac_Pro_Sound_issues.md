---
title: "[SOLVED] Mac Pro Sound issues"
date: 2007-08-05
forum: Apple Intel Users
---

### Post by macaholic on 2007-08-05
Alright so, the sound on my mac pro under ubuntu is not working. How would I go about doing this? Is it something with the alsa drivers? Here is a screenshot of my sound preferences:
[ATTACH]39932[/ATTACH]

As always any help on this would be great.

---

### Post by cyberdork33 on 2007-08-05
> **macaholic said:**
> Alright so, the sound on my mac pro under ubuntu is not working. How would I go about doing this? Is it something with the alsa drivers?

Looks like hardware is detected. Try adjusting values in alsamixer

---

### Post by macaholic on 2007-08-05
Well I guess the sound HAS been working it is just sooooooooooooooooooo soft even when it's cranked all the way up I can barely hear it. Any ideas?

---

### Post by macaholic on 2007-08-05
Another note, when I do the system tests, they seem to be the right volume, but when I do anything else, for example youtube, it is ridiculously soft.
EDIT:
Actually they are a bit soft too :p

---

### Post by DMills on 2007-08-06
This is fixed in the latest ALSA driver release from the ALSA project, but does not appear to have made it into the Ubuntu kernels yet. 

If you have the developer tools installed then just downloading the latest alsa-driver tarball and doing the normal ./configure && make && sudo make install routine followed by a reboot should result in mostly working audio (At least it does on my quad core example). 

I still cannot get the front headphone jack to work, but apart from that it seems to work fine.

HTH.

Regards, Dan.

---

### Post by macaholic on 2007-08-06
Thx, I will try this soon when I get the time (currently trying to get xgl to work correctly). Will post when I have tried installing the latest release.

---

### Post by macaholic on 2007-08-06
Which driver do I download?

---

### Post by DMills on 2007-08-07
1.0.14 worked for me. 

Regards, Dan.

---

### Post by macaholic on 2007-08-07
Alright I'll try that and post back later.

---

### Post by macaholic on 2007-08-07
I installed alsa driver, lib, and utils, how do i load the driver?
excuse my noobishness :p.

---

### Post by macaholic on 2007-08-07
Nevermind worked aftter a reboot. ty for help.

---

### Post by cyberdork33 on 2007-08-07
Thanks for marking as solved, that rarely happens here.

---

### Post by macaholic on 2007-08-09
No problem, I assume it helps other people when they are searching for threads. :D

---

### Post by mariguango on 2008-05-27
I have 1.0.16 installed, but sound still very soft on my macbook pro. Need advice.

---

### Post by cyberdork33 on 2008-05-27
> **mariguango said:**
> I have 1.0.16 installed, but sound still very soft on my macbook pro. Need advice.
This thread is for Mac Pros, not MacBook Pros. You should post in the newer Apple forum with new questions. There are several people reporting a problem similar to yours right now.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by mariguango on 2008-05-28
> **cyberdork33 said:**
> This thread is for Mac Pros, not MacBook Pros. You should post in the newer Apple forum with new questions. There are several people reporting a problem similar to yours right now.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)
Thank you. You right, this is wrong place.

---

### Post by peanutboy on 2008-06-19
I have installed the alsa drivers 1.0.16, twaeked the alsamixer and still absolutely nothing... alittle help

mac pro

hardy

ubuntustudio

---

### Post by naitsirhc on 2008-06-21
Hello,

I am running a Mac Pro (aluminum case) and am having trouble getting sound working.  I have tried compiling and installing the alsa 1.0.16 drivers, but still am not having any luck.

In addition, I tried setting manually setting the model using:

options snd-hda-intel model=macpro

and then,

options snd-hda-intel model=mbp3 (just in case)

However, neither of these seemed to make a difference.  After no luck with these attempts, I tried applying the patch mentioned [here]("http://ubuntuforums.org/showpost.php?p=4457201").  I still have no sound from either the internal speakers, the front headphone jack, or the rear headphone jack.

Does anyone have any suggestions?  Below is a list of my system info:

Ubuntu Hardy Heron
Kernel: 2.6.24-19-generic
alsa 1.0.16
Mac Pro
Codec: Realtek ALC885 (from `cat /proc/asound/card0/codec#0 | grep Codec`)

Any help would be greatly appreciated!

Thanks!

---

### Post by cyberdork33 on 2008-07-02
> **naitsirhc said:**
> Any help would be greatly appreciated!
Try this thread from the Apple Intel FAQ:
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

Also, please use the new Apple Users forum in the future.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by wubi on 2008-07-06
> **cyberdork33 said:**
> Try this thread from the Apple Intel FAQ:
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

Also, please use the new Apple Users forum in the future.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

I think you are directing us back to this thread...and the issue still persist so I wouldn't say this is solved.  I'm using the Alsa 1.0.16 drivers and I get no sound at all as well.  I'm on a "MacPro" with Ubuntu Hardy...anyone with this issue solved and suggestions would be appreciated!

Cheers.

---

### Post by naitsirhc on 2008-07-08
> **cyberdork33 said:**
> Try this thread from the Apple Intel FAQ:
[http://ubuntuforums.org/showthread.php?t=518391](http://ubuntuforums.org/showthread.php?t=518391)

Also, please use the new Apple Users forum in the future.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)


Thank you for your suggestion, but I agree with wubi - I have tried the 'solutions' suggested in this thread and am still unable to get sound working.

---

### Post by cyberdork33 on 2008-07-08
> **naitsirhc said:**
> Thank you for your suggestion, but I agree with wubi - I have tried the 'solutions' suggested in this thread and am still unable to get sound working.
Sorry, didn't realize, but still, new posts / questions / problems should go to the new forum. Nobody checks these threads anymore. 

Also, If this solution surely doesn't work, I will remove it from the FAQ.

---

