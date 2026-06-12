---
title: "Blue Tooth headset and Skype"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Horomancer on 2008-03-23
Hello. Before i get to my problem i would just like it known that I've had about 4 whole hours of linux experince now and know nothing of things like the command terminal. I've been getting along well so far with just GUI exicuted commands. My copy of Ubuntu 7.10 has nothing that couldn't be pulled from the Synaptic Package manager and it has been change very little.

I have a blue tooth headset (jawbone) and the Ubuntu copy of skype. When i started running skype, whatever the default sound setting was, worked and I could hear everything loud and clear from my desktop speakers. My speakers are hooked up to a soundblaster sound card that i have done nothing too, since it works fine with the default ubuntu drivers.
I paired my headset with no trouble, and clicking on the blue tooth ap shows that my Jawbone is bonded to Ubuntu and set for both incoming and outgoing audio.
I go to adjust skype's audio settings and get a list of options i do not understand.
My choices are-
Default Device
HDA ATI SB (hw:SB,0)
HDA ATI SB (plughw:SB,0)
CA0106 (hw:CA0106,0)
CA0106 (plughw:CA0106,0)
CA0106 (hw:CA0106,1)
CA0106 (plughw:CA0106,1)
CA0106 (hw:CA0106,2)
CA0106 (plughw:CA0106,2)
CA0106 (hw:CA0106,3)
CA0106 (plughw:CA0106,3)

I've played with all of them but with no success. Is there a way to test my headset to insure it is working properly?
And how do i tell what these different options mean?

---

### Post by benpage26 on 2008-06-16
as i understand, making a file called ".asoundrc" with gedit and adding ```
pcm.bluetooth {
  type bluetooth
  device 00:0D:3C:6B:75:3C
  profile "headset"
}
```

To it should mean that a "Bluetooth" audio type shows up in the settings of skype.  This may not work though, as i never got my Jawbone to pair, so i cannot test it.

Can you tell me what steps/software you used to pair your jawbone please?

Edit:

A command to achieve this quickly is "gedit ~/.asoundrc" in the command line then copy/paste the code segment above.

---

