---
title: "No Sound after upgrade ALSA, ATI on board sound"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by MasterColdSoul on 2007-01-24
Well it started with me having bad sound coming from my microphone, line-out, and front mic ports. I got sound just fine in Ubuntu, but in NWN my sound was also messed up (and I wanted to record through Line-in) so I followed this help below

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I installed the ALSA 14rc2 packs according to the help file and then re-started to No sound :(

I then tried the 13.0 packs.. again no sound

Then I tried the help listed below because the guy had the same error I had and it did nothing.
 [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=no+volume+control+GStreamer](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=no+volume+control+GStreamer)

This is my audo device:
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Gateway 2000 Unknown device 6047
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 41200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

aplay doesn't see it:
aplay: device_list:222: no soundcards found...

I know of a fresh edgy install it saw it... the thing that messed it up was the update.. any help?

---

### Post by MasterColdSoul on 2007-01-24
I would be happy for now to atleast have my sound back (even with the scatchy microphone, and line-in ports) so I can listen to music, and videos. 

Is there a way to re-install just the CD sound portion without a full re-install? 

If not.. where is the downloaded files kept (for updates) so I can back them up? Thanks.

---

### Post by MasterColdSoul on 2007-01-25
Can anyone please help?

---

