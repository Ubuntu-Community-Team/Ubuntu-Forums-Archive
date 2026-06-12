---
title: "Re: Microphone not working on MacBookpro 15 (version 8.2) and Xubuntu 16.04"
date: 2016-05-08
forum: Apple Hardware Users
---

### Post by alejandro-f on 2016-05-08
I have a Macbook pro 15 (version 8.2) with Xubuntu 14.04 the mic worked out of the box, with xubuntu 16.04

* upgraded from 14.04
* fresh install

The mic does'nt get any signal, i have tried these:
[http://askubuntu.com/questions/482626/microphone-not-working-on-ubuntu-14-04-on-macbookpro10-2](http://askubuntu.com/questions/482626/microphone-not-working-on-ubuntu-14-04-on-macbookpro10-2)

with no luck.

This is what i got (attachments added)

[ATTACH=CONFIG]268935[/ATTACH][ATTACH=CONFIG]268936[/ATTACH]

the output of the command:
```
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
is here:
[http://www.alsa-project.org/db/?f=1a18a2a3188be0c68d960ae4e6d8ec2ccacb994d](http://www.alsa-project.org/db/?f=1a18a2a3188be0c68d960ae4e6d8ec2ccacb994d)
```
if please can anyone help me ?
not being able to use the microphone is killing me.
thank you !

---

### Post by hatuko on 2016-06-08
Same laptop, Ubuntu 16.04, same problem. Have you found a solution?

Kernel 4.6 seems to fix it, although the sound recorded is a bit weird... still looking

---

### Post by alejandro-f on 2016-06-08
great, at least trying that out, a more refinate solution would be great also

> **hatuko said:**
> Kernel 4.6 seems to fix it, although the sound recorded is a bit weird... still looking

installed from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/) and mic still doesnt work ](*,)

---

### Post by hatuko on 2016-06-09
Was working for me but it broke VMWare Workstation and after spending lots of time I gave up on 4.6.

So I've found a fix for 4.4 (the default kernel with 16.04). Follow these instructions [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) :)

I forgot, if you still have problems also try [http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)

---

### Post by alejandro-f on 2016-06-30
> **hatuko said:**
> Was working for me but it broke VMWare Workstation and after spending lots of time I gave up on 4.6.

So I've found a fix for 4.4 (the default kernel with 16.04). Follow these instructions [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) :)

which one of all this steps did work for you ?

---

