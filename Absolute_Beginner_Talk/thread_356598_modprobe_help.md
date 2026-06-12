---
title: "modprobe help"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ImolaOrange on 2007-02-08
I dont think my last post had a good title. So I'll try again...

Just installed Ubunto 6.10 and am trying to get my HVR-1300 card working.

I followed the steps here...
[http://www.ubuntuforums.org/showthre...hlight=hvr1300](http://www.ubuntuforums.org/showthre...hlight=hvr1300)

... and I managed to get the card working.

However if I reboot I need to re-run this command... "sudo modprobe cx88-dvb"

Can I had this to some config file so its run when I reboot the machine?

Thanks
Alan

---

### Post by DSn0wMan on 2007-02-08
You can put that option in /etc/modprobe.d/options

On my machine I  would us this command to fix my soundcard bug

sudo modprobe snd_intel8x0 ac97_quirk=hp_mute_led

So my /etc/modprobe.d/options file looks like this:

# Fix for intel ICH6 sound
options snd_intel8x0 ac97_quirk=hp_mute_led

---

