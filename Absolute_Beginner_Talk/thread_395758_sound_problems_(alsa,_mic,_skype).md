---
title: "sound problems (alsa, mic, skype)"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-28
i have a problem since i tried to fix the skype . i just want to enable the option for making a conversation with two people in the same time. since then i searched for tips how to solve the problem and i messed a little bit with alsa and now skype doesn't work at all , and even my sound recorder give a message :" your audio capture settings are invalid... etc
i checked the alsamixer to see my mic isn't muted . i tried many things and find no solution.
*my sound still work , i can listen to music and everything..
i know the older version of skype doesn't make this problem , but i dont want to use it.
 if you need more information tell me.

---

### Post by RichPicker on 2007-03-28
I think there is a bug. Several people have had sound/mic problems recently.

---

### Post by fanny on 2007-04-11
is there any other suggestion?

---

### Post by fanny on 2007-04-11
help..........

---

### Post by Valstorm2323 on 2007-04-11
What does your alsa-base file say?

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-intel8x0 index=0                  <*insert this line
options snd-ice1712 index=1                   <insert this one too
options snd-usb-audio index=2                    <And finally that one.

If the last three lines are missing, just put them in.
Mine started working after I did that and turned it off. Of course I put my PCI sound card in it but turns out the sound came back on after switching it on.

So basically your hardware is still installed but alsa-base got messy for whatever reason, I'm guessing.

---

### Post by fanny on 2007-04-11
i didnt understand allot.. where to start? im total newbie please consider :)

---

### Post by Valstorm2323 on 2007-04-11
ahh sorry, I read too fast. I see your sound is working so don't do what I posted.

You are only having problems with the mic?

---

### Post by fanny on 2007-04-11
much or less. 
when i try to call someone in skype i have a message after one ring: "problem with the sound device"
and when im trying to record in the sound recorder i have message: "your audio catpture settings are invalid...

---

### Post by Valstorm2323 on 2007-04-11
Did you try going to SYSTEM>Preference>Sound

I suggest you play around selecting each and testing to see if any of the SOUND CAPTURE DEVICES work.  Mine is ADC CAPTURE.

Little warning, if you choose one that doesn't work the window might just hang but it doesn't look like it will break anything. 

If that fails then I guess the new update must've screwed it up.

---

### Post by fanny on 2007-04-11
why when im going to :  SYSTEM>Preference>Sound i dont find any capture sound?

---

### Post by Rospo Zoppo on 2007-04-11
And what's your ```
lspci | grep Audio
``` ?

---

### Post by fanny on 2007-04-11
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
.
dont forget it used to work fine untul i edit someaudio files . i had sound in the skype but i couldnt make conference call. then i start to mess and probably did something wrong.

---

### Post by Rospo Zoppo on 2007-04-11
I think you should give a look here [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
and then check alsamixer..

---

### Post by fanny on 2007-04-11
i have sound i can listen to music ....

---

### Post by Rospo Zoppo on 2007-04-11
I had too, but following that wiki I got my mic work well.. And I have same hardware..

---

