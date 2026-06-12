---
title: "lshw and lshw-gtk not showing proper/full results"
date: 2009-03-11
forum: Apple Hardware Users
---

### Post by sms0611 on 2009-03-11
I have a PowerMac G4 running Hardy.

Since installation it insists that there is no sound devices installed

If I run sudo lshw I get one line up (PCI (sysfs)) and then it hangs (need ctrl-c to exit back to prompt)

If I run sudo lshw-gtk no sound devices are shown but I can see everything else.

Could this be a cmos battery problem? Or does anyone out there have another idea?

---

### Post by roym4 on 2009-03-12
not sure about your lshw problems. If you need to get sound working you might try adding snd-powermac to the /etc/modules file and reboot.

---

### Post by sms0611 on 2009-03-12
Thanks for that it helped somewhat,

I now have a recognised sound device PowerMac Tumbler

But still no sound coming out. Any suggestions ?

---

### Post by sms0611 on 2009-03-13
Correct that.

OK Now I have sound options available but still no sound. The sound card does not appear in lshw.

---

### Post by roym4 on 2009-03-15
You might try adding the following lines to your /etc/rc.local file:

amixer sset 'Auto Mute' off
amixer sset 'PC Speaker' on

you'll need to reboot to run the rc.local scripts. 

We've seen many tower G4/QuickSilvers that do have sound from the internal speaker but at a very low level. Make sure the volume level is high. You may want to try alsamixer to adjust sound levels. 

I believe that these G4s may require Apple Pro speakers that are powered from the speaker jack. Regular externally powered speakers & headphones should use the headphone jack.

---

### Post by sms0611 on 2009-03-16
That's solved it, at least as far as playing CD's, DVD's etc.

I still find it strange that the hardware doesn't appear anywhere on lshw.

One interesting point is that none of the system sounds are playing, I've got them all set up in system->preferences->sound
and if I do a test on the system events I get a tone but when I go to the individual events and press play I get nothing.

It's no big deal coz I can easily live without them but even so I can't see why they don't work.

Anyway thanks for the great advice.

---

