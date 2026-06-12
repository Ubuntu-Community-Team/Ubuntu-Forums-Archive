---
title: "sound problem"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by fayazskarim on 2007-07-10
I have a sound problem, I have a spdif soundcard(riviera turtle beach) and the sound is not coming out, do I need to install any specific codec or driver for it and I also have a 5.1 channel card, I tried with that too but still it's not working... It's weird. I have the oem cd for the turtle beach riviera sound card and when I browse the cd I see the linux folder, I dont kn ow how to patch the file, it's complicated.

Can someone help me with this problem please, thank you again...

Ubuntu is the Best !!! Keep it up

---

### Post by KIAaze on 2007-07-10
What's in the linux folder on the CD?

Try installing the alsa-oss, alsa-base and alsa-utils packages.

More generally have a look at packages related to:
-alsa
-esd
-oss

Sometimes, you don't hear any sound just because the PCM level is too low.
It can be set with the "alsamixer" command for example (available in the alsa-utils package).

---

### Post by fayazskarim on 2007-07-12
Hi, thx for ur help, I installed all packages that u told me, so it was working but when I restarted the computer it didnt work, I tried to re-install the packages but still didnt work, I cant see the driver in the sound configuration...

Help plz...

Thank you

---

### Post by KIAaze on 2007-07-13
Install the esound package and then run this command if there is no sound:
> /usr/bin/esd -nobeeps

If it works, this trick will prevent you from having to run the command everytime:
[http://ubuntuforums.org/showthread.php?p=2982117&highlight=esd#post2982117]("http://ubuntuforums.org/showthread.php?p=2982117&highlight=esd#post2982117")

---

### Post by fayazskarim on 2007-07-13
thx it's working now but only in stereo mode, not in 5.1 , I have a spdif output card. Do u need a special player for this?

---

### Post by fayazskarim on 2007-07-17
thx it's working now but only in stereo mode, not in 5.1 , I have a spdif output card. Do u need a special player for this?

---

### Post by KIAaze on 2007-07-17
I did see your last post. The problem is that I have no idea about how to get 5.1 sound working.
Unless somebody else takes interest in this thread, I think you should just post a new one. (unanswered threads are more attractive ^^)

But I still did a quick research and the good news is it should work in 5.1! :)
>  Linux knows to use it for standard stereo sound, as well as 5.1
[http://www.newegg.com/Product/Product.asp?Item=N82E16829118105]("http://www.newegg.com/Product/Product.asp?Item=N82E16829118105")

ALSA sound card matrix:
[http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Turtle_Beach]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Turtle_Beach")

---

### Post by fayazskarim on 2007-07-17
thx bro, let me post another thread...

---

### Post by rustix on 2007-07-17
hey guys please take a look at this thread.. it's related to sound problem as well....

[http://ubuntuforums.org/showthread.php?t=502880](http://ubuntuforums.org/showthread.php?t=502880)

need help badly..

---

