---
title: "Sound issues in 7.04"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-08-15
Hi, I know this issue must of been talked about in dozens of threads, but I can not seem to find an older one that solves my problem... I just installed Ubuntu 7.04 and have no sound. Occasionally my computer will play the start up sounds but it is rare and that is the only sound that will play. Anyone know what I can do to fix the problem? Thanks.

---

### Post by OZTack on 2007-08-16
Hmm - what sound card?

[And the obvious - have you activated all the sound options under the sound icon? I found that I had a lot of problems with my 5.1 audigy system - turned out there were a HEAP of controls - "off the window" that I did not realise and I had to scroll to get to 'em]

---

### Post by kevindubrow on 2007-08-16
On the Gateway website ( I have a MX7118), it says "AC '97 2.3 Compliant Audio" under the audio specifications. I don't think it is a matter of the audio being turned on or not because the sound occasionally works. Any ideas? Thanks a lot.

---

### Post by kevindubrow on 2007-08-16
Thats odd...the face... MX7118. Thats the model.

---

### Post by Hobo Joe on 2007-08-16
Under preferences in the sound control panel, check and see if you have more than one sound card.

---

### Post by kevindubrow on 2007-08-16
I have three options:

ATI IXP (ASLA mixer) which has all of the volume controls
ATI IXP modem (ASLA mixer) which has no volume controls
and Conexant id 30 (OSS mixer) which only has two volume controls: Speaker and PCM 2

---

### Post by kevindubrow on 2007-08-16
Some other info.

When typing aplay- l, I get this message:

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The alsa mixer seems ok.

---

### Post by Arthur Archnix on 2007-08-16
Intermittent sound playback? Does you logon sound always work? What about logoff sounds? Have you checked the connection between your speakers and computer? Is it firmly in? Are you having trouble hearing your music? If so, have you installed all your codecs needed?

---

### Post by kevindubrow on 2007-08-16
The log in sound does not always work. Same with the log off sounds. Its a laptop...I hope the connection is not the problem :). About music, the sound will work perfectly or not at all; the sound does not work at all more often. And I am not sure about the codecs. How would I get them? Thanks for your help!

---

### Post by kevindubrow on 2007-08-16
Ok, I have restarted the laptop a few times and it has booted up with sound on this boot. Now that it is working for this boot, is there some information I can get from the terminal that will help someone figure out what is going wrong?

---

### Post by OZTack on 2007-08-16
I do wonder if this is a hardware problem :(  
Intermittent sound on a laptop - I suggest  you try plugging  in headphones next time it doesn't seem to work - My laptop sound died just like that - loose connection - only headphones worked - then they died too.....

---

### Post by kevindubrow on 2007-08-16
That would be horrible...I just got this off of ebay. It works wonderfully. Let me restart so that I do not have sound and I will plug in some head phones. Thanks for the reply.

---

### Post by Arthur Archnix on 2007-08-16
It would be horrible, but like OZ I can't think of any other reason... maybe modules being loaded differently, blocking the sound... I'm stretching though and someone who knows more might say that that's unlikely...or impossible.

---

### Post by kevindubrow on 2007-08-16
Ok, no sound on boot. I plugged in the headphones and no sound. Any more ideas?:)

---

