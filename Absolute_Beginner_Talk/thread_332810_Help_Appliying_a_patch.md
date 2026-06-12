---
title: "Help Appliying a patch"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by albesan on 2007-01-06
Hello team,

I'm trying to get the sound working properly on a Dell i6400.
Sound output is fine, I can't record any sounds though.
After going through the comprehensive guide to audi problems and several other how to's I found there is a known bug and I found a patch for it but I'm new to linux and I'm not sure how to use it.
the patch: [http://hg-mirror.alsa-project.org/alsa-kernel?cs=7ec5965d96a3;style=raw](http://hg-mirror.alsa-project.org/alsa-kernel?cs=7ec5965d96a3;style=raw)

any help/comment on the issue welcome

thanks 

a.

---

### Post by dannystaple on 2007-01-06
That patch would require you to be building a component (possibly the audio driver kernel module) from source, so you would need to acquire the source for that and a configured kernel, then apply the patch (assuming the patch is correct for the version you have), and then compile with that. This is not something I would recomend for a newbie.

What are the dates of the postings detailing the known bug? Is it possible you have missed some much smaller problem, for example enabling the audio input and making sure it has its level above zero from the audio dialog box?

What version of Ubuntu are you using?

Cheers,
Danny

---

### Post by albesan on 2007-01-06
hello danny,

thanks for the reply.

I'm running Dapper, 

I found this posting related to my laptop model, although some people make no mention to mic in not working.

[http://www.ubuntuforums.org/archive/index.php/t-190167.html](http://www.ubuntuforums.org/archive/index.php/t-190167.html)

I've tried alsamixer, alsamixergui, genome-alsa-mixer and all show capture channels available and enabled... I don't get it...

within that post I found:

"bmandoline
October 3rd, 2006, 09:08 PM
Reference:
------------------
Re: Dell Inspiron 6400/e1505
yes, i have the same problem: speakers/headphone audio output not switching properly. (with my dell inspiron e1505)
currently, fresh boot without headphones plugged in and no sound from speakers. when i plug in the headphones i hear audio through the headphones. when i unplug them i still get no audio output from the speakers.
i'd rather not roll the reboot dice.
i'm searching for more info.
soundcard: sigmatel STAC9200
using default ubuntu sound setup of alsa/esd
---------------------

My hint: Kick your DELL-Sigmatel audio chip to perform as you want and go to : [http://www.ekhoury.com/2006/08/25/sigmatel-stereo-mix-support-for-dells/](http://www.ekhoury.com/2006/08/25/sigmatel-stereo-mix-support-for-dells/) for your solution for your Dell Inspiron.
I am looking for a solution for same problem for my :( :( Dell Dimension5100 :( with same Sigmatel chip, however an other processor chip then your Inspiron .
Cheers, Bert"


I've gone to the site and downloaded the relevant file but it is a .zip file containing a windows driver.

Is it posible to install it on ubuntu?

thanks again.

a.

---

### Post by albesan on 2007-01-07
Hi I have been having sound input problems on the Dell i6400 laptop.

After much research I found a patch but I was adviced in this forum not to get into recompiling since I'm new to linux. The patch:

[http://hg-mirror.alsa-project.org/alsa-kernel?cs=7ec5965d96a3;style=raw](http://hg-mirror.alsa-project.org/alsa-kernel?cs=7ec5965d96a3;style=raw)

So I kept searching for a solution and found this post:

[http://www.ubuntuforums.org/showthread.php?t=201657](http://www.ubuntuforums.org/showthread.php?t=201657)

Follow the instructions and after that I could finally record sound.

Then I couldn't use skype, and after much researching I found this other post:

[http://www.ubuntuforums.org/printthread.php?t=32063&pp=40](http://www.ubuntuforums.org/printthread.php?t=32063&pp=40)

And after following that I can finally use skype.

I hope this helps anybody with audio problems on the Dell i6400


a.

---

