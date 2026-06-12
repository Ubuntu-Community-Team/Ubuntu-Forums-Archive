---
title: "Need some help with my sound card."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by uruk912 on 2008-02-20
Alright Ubtuntu recognizes my sound card as this:
82801H (ICH8 Family) HD Audio Controller

But their is no driver for it or its not recognized or something. On my quest if you will call it that i google it and saw something that their is a bug that for this type of sound card. So will anyone give me a direction to go to on here. I will get this out of the way. Its not on mute also i am on an Acer Aspire laptop(i had a problem with my wireless card as well but that solved). But thanks in advanced to anyone who helps me.
Uruk912

---

### Post by uruk912 on 2008-02-20
If anyone is helping me i belive i found something that just i need to be "dumbed" down for me to understand. Here is a link:
[code]https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller[/code/

And it saids this:
#

Aspire 5315

    *

      installed linux-backports-modules-generic
    *

      added options line to /etc/modprobe.d/alsa-base:
      options snd-hda-intel model=acer
    *

      Ubuntu 7.10/Gutsy Gibbon
    *

      Speakers work, front headphone jack and front mic works.
    *

      Internal mic doesn't seem to work.

---

### Post by oedha on 2008-02-20
maybe you need the clue for the above step.......
open terminal....
sudo apt-get update
sudo apt-get install linux-backports-modules
then
gksu gedit /etc/modprobe.d/alsa-base
insert :        options snd-hda-intel model=acer
then restart.......

---

### Post by spiderbatdad on 2008-02-20
That is the short solution. If it doesn't work, you may need to rebuild alsa. This is related to a bug in the driver for this card.
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by uruk912 on 2008-02-20
Well i found this out when i was trying the second method that is on this site:[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

It saids this on my terminal
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.
 So if its muted by default did i just do something i didnt need to do? Elaborate please.

---

### Post by spiderbatdad on 2008-02-20
run alsamixer in the terminal. You can navigate through the settings with the arrow keys. But there are bug reports regarding the driver and that sound card.

---

### Post by uruk912 on 2008-02-20
I did what oedha said to do and all that happends is when i reboot and start up the volume is muted and theirs no sound still and then i unmute it and still their is nothing. so wtf?

---

### Post by uruk912 on 2008-02-20
Where exactly am i soposta add the new code to the alsa-base?

---

### Post by spiderbatdad on 2008-02-20
> **oedha said:**
> maybe you need the clue for the above step.......
open terminal....
sudo apt-get update
sudo apt-get install linux-backports-modules
then
sudo gksu gedit /etc/modprobe.d/alsa-base
insert :        options snd-hda-intel model=acer
then restart.......

```
gksu gedit /etc/modprobe.d/alsa-base
```

---

### Post by uruk912 on 2008-02-20
Yes i understand where as in the file. Im asking where in the file to place the new line? their is several places to put this code where should i place it?

---

### Post by spiderbatdad on 2008-02-20
anywhere in the list of options

---

### Post by teamkiller87 on 2008-02-20
At the end of the file although I don't think it really matters... I might be wrong... Just put it at the end.

---

