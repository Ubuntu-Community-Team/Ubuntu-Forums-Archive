---
title: "Poor recording quality with background noise"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by ironorion on 2008-02-12
Hello there,

I'm attempting to use teamspeak ( or any recording software) with my microphone. It does work, though not well at all.

When I push the activate local test in teamspeak, even if the mic is not plugged in I can hear a buzzing/humming noise from the speakers.  When i do have the mic plugged in, I can hear my voice though it is poor quality. 
When I tried to mute or lower the mic volume in the mixer, I got no change in volume. it seemed like it was hardcoded. 

I tried updating Alsa, to 1.0.16
sound playback is VERY nice for anything NOT from the microphone.

the system is a HP dv9035nr
running Gutsy 7.10

I'm sure I'm missing some information that you might need. I'm a bit new to ubuntu, so letting me know what commands to enter to get that info would be great.

Thanks!

---

### Post by defenestratos on 2008-02-12
If you have onboard sound chips then those sounds are probably you hard drive heads and CPU fan etc. It will most probably be the same in Windows. I don't know how much you can do about it apart from get a nice new PCMCIA or USB sound device. My  onboard sound has a noise threshold of around -45-55db depending on how it is feeling that day. The Creative Audigy I had on my old computer boasted of -120db. That is well below human perception and promises a nice clean signal you can mess around with, no artifacts and stuff.
You could also try using a power supply (Preamp) between your mic and your pc. That can boost and clean up the levels of the mic and optimise the noise threshold. 
Hope this helps.

Ah yes forgot. Go to your sound mixer (This can be brought up through the sound aplet on the taskbar) and turn of +20db boost. That can be pretty nasty on a cheap soundcard. You might need to tell the mixer to show this setting under edit/preferences.
:)

---

### Post by ironorion on 2008-02-12
Actually, this laptop has no problems with the microphone under windows. 

If I had to guess, I'd say this is a driver issue, but I'm not really sure how to go about updating the driver.

---

